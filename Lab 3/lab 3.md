---
title: Lab3_student

---

# Lab 3: Deploying a 5G Standalone Network Using OpenAirInterface

## 1. Goal

In the previous labs, you analyzed 5G signaling messages and network performance using provided captures and measurements.

In this lab, you will deploy your own 5G Standalone (SA) network using OpenAirInterface (OAI), verify the complete connection, investigate RFsimulator communication, perform active network measurements, and troubleshoot a controlled connection failure.

Unlike the previous labs, you will collect measurements directly from your own running 5G network.

**Learning Objectives**

After completing this lab, you should be able to:

1. Deploy an OAI gNB, nrUE, and 5G Core Network.
2. Identify the main stages of 5G SA connection establishment.
3. Verify communication between gNB and nrUE through RFsimulator.
4. Measure user-plane connectivity under different packet sizes.
5. Diagnose connection failures using OAI and 5GC logs.
6. Explain the limitations of a software-simulated 5G network.

## 2. Experimental Environment

Use the *OAI v2.4.0 Build Guide* to prepare the environment before class.

| Component | Configuration |
|---|---|
| Ubuntu | 24.04 |
| OAI RAN | v2.4.0 |
| 5G Core | OAI CN5G |
| gNB | nr-softmodem |
| UE | nr-uesoftmodem |
| Radio interface | RFsimulator |
| Band | n78 |
| Subcarrier spacing | 30 kHz |
| Resource blocks | 106 |
| UE IMSI | 001010000000001 |
| External DN | 192.168.70.135 |

The experiment uses one Ubuntu machine without physical RF hardware.

## 3. Task 1 — Deploy and Verify the Complete 5G SA Network

Start the OAI CN5G:

```bash
cd ~/oai-cn5g
docker compose up -d
docker compose ps
```

Start the gNB and nrUE using the commands in the Build Guide.

Observe their terminal outputs and locate evidence of the following stages.

| Stage | Successful? | Evidence from logs |
|---|---|---|
| CN5G initialization | Yes | All 10 CN5G containers (`mysql`, `oai-nrf`, `oai-amf`, `oai-smf`, `oai-upf`, `oai-ausf`, `oai-udm`, `oai-udr`, `oai-ext-dn`, `ims`) started and reported `Up` in `docker compose ps`. |
| gNB NG Setup | Yes | gNB logs confirmed `in-sync` status and active NGAP control-plane connection with the AMF (`oai-amf`). |
| UE synchronization | Yes | nrUE logs confirmed physical-layer synchronization with the gNB (`UE RNTI f6e5`, `in-sync`, `average RSRP -44`). |
| RRC connection establishment | Yes | nrUE completed the 4-step CBRA procedure and transitioned to `State = NR_RRC_CONNECTED` with SRB1 established. |
| UE Registration | Yes | NAS Registration succeeded for subscriber IMSI `001010000000001` (`5GMM-REGISTERED`). |
| PDU Session Establishment | Yes | Core network established the PDU session and allocated IPv4 address `10.0.0.2/24` to the UE. |
| UE tunnel creation | Yes | `ip -4 addr show oaitun_ue1` confirmed interface `oaitun_ue1` is `UP,LOWER_UP` with `inet 10.0.0.2/24`. |

Take screenshots showing the gNB and UE successfully connected.

**Questions:**

1. Does a successful NG Setup guarantee that a UE can register? Explain.

No. NG Setup only confirms that the control-plane interface (N2) between the gNB and the AMF is operational. UE registration is an end-to-end NAS procedure that still requires valid subscriber credentials in the UDM/AUSF, mutual authentication, and security context establishment.

2. Why can the UE establish an RRC connection but still fail Registration?

RRC connection establishment only sets up the radio-level control link between the UE and the gNB. Registration happens afterward at the NAS layer with the AMF/AUSF and can fail due to an unknown IMSI, mismatched authentication keys (K/OPc), or core network policy rejections.

3. What additional procedure is required after Registration before user data can be exchanged?

A PDU Session Establishment procedure is required. It allocates an IP address to the UE, configures the GTP-U user-plane tunnel (N3) between the gNB and UPF, and brings up the virtual tunnel interface (`oaitun_ue1`).

## 4. Task 2 — Investigate RFsimulator Communication

OAI RFsimulator replaces the physical RF interface with software-based communication.

The gNB and nrUE exchange IQ samples through a TCP connection.

Check the running processes:

```bash
pgrep -a nr-softmodem
pgrep -a nr-uesoftmodem
```

Inspect the TCP connections:

```bash
sudo ss -tnp | grep 4043
```

If necessary, inspect the listener:

```bash
sudo ss -ltnp | grep 4043
```

The default RFsimulator port in this experiment is 4043.

Complete the table:

| Item | Observed Value |
|---|---|
| gNB process ID | `72937` |
| nrUE process ID | `73656` |
| RFsimulator transport protocol | TCP |
| RFsimulator port | 4043 |
| TCP connection state | `ESTAB` (ESTABLISHED) |
| Connected process(es) | `nr-softmodem` (PID `72937`), `nr-uesoftmodem` (PID `73656`) |

Take one screenshot showing the TCP connection.

**Questions:**

1. Why does RFsimulator use a TCP connection instead of a physical antenna?

RFsimulator replaces physical radio transmission with a reliable local TCP socket so the gNB and nrUE can exchange baseband IQ samples in software without needing SDR hardware or RF shielding.

2. Are the TCP packets exchanged by RFsimulator the same as the UE's application-layer IP packets?

No. RFsimulator TCP packets carry raw digitized radio signals (complex I/Q time-domain samples) between the simulated transceivers, whereas the UE's application-layer IP packets are encapsulated inside 5G user-plane protocols (SDAP/PDCP/RLC/MAC/PHY) modulated onto those IQ samples.

3. Does using RFsimulator mean that the UE and gNB are performing no physical-layer processing? Explain.

No. Both `nr-softmodem` and `nr-uesoftmodem` execute the full 5G NR PHY stack, including channel coding (LDPC/Polar), scrambling, QAM modulation, resource element mapping, and OFDM modulation/demodulation. RFsimulator only replaces the DAC/ADC and wireless air interface.

## 5. Task 3 — Verify End-to-End Connectivity

Check the UE tunnel interface:

```bash
ip -4 addr show oaitun_ue1
```

Test connectivity to the External DN:

```bash
ping -I oaitun_ue1 -c 10 192.168.70.135
```

Record:

| Measurement | Observed Value |
|---|---|
| UE IP address | `10.0.0.2` |
| Destination IP | `192.168.70.135` |
| Packets transmitted | 10 |
| Packets received | 10 |
| Packet loss (%) | `0%` |
| Minimum RTT (ms) | `14.603` |
| Average RTT (ms) | `18.335` |
| Maximum RTT (ms) | `22.053` |

Take a screenshot of the Ping result.

**Questions:**

1. Why must Ping use the `oaitun_ue1` interface in this experiment?

Because both the UE and the Docker containers run on the same Ubuntu host. Binding `ping` with `-I oaitun_ue1` forces ICMP packets to enter the UE's 5G protocol stack and traverse the simulated RAN and UPF rather than using the host's default loopback or Docker bridge routing.

2. Does successful Registration guarantee successful user-plane connectivity?

No. Registration only establishes the control-plane NAS context (5GMM-REGISTERED). User-plane traffic requires an active PDU session, proper GTP-U tunneling between gNB and UPF, and correct IP routing to the external data network.

3. What does a successful Ping prove, and what does it not prove about the simulated 5G system?

It proves that the end-to-end 5G stack (PHY through NAS, GTP-U tunnel, UPF routing, and DN reachability) is functionally operational. However, it does not prove real-world RF link quality, wireless coverage, multi-user scheduling capacity, or over-the-air hardware latency.

## 6. Task 4 — Investigate the Effect of Packet Size

You will now investigate whether changing the ICMP packet size affects the observed RTT.

Perform three experiments using the same established 5G connection.

**Scenario A — Small Packets**

```bash
ping -I oaitun_ue1 -s 56 -c 30 -i 0.2 192.168.70.135
```

**Scenario B — Medium Packets**

```bash
ping -I oaitun_ue1 -s 512 -c 30 -i 0.2 192.168.70.135
```

**Scenario C — Large Packets**

```bash
ping -I oaitun_ue1 -s 1200 -c 30 -i 0.2 192.168.70.135
```

Note: `-s` specifies ICMP payload size, not the complete IP packet size.

Complete the table:

| Scenario | ICMP Payload | Avg. RTT (ms) | Max. RTT (ms) | Packet Loss (%) |
|---|---:|---:|---:|---:|
| A | 56 bytes | `15.303` | `19.641` | `0%` |
| B | 512 bytes | `19.265` | `27.503` | `0%` |
| C | 1200 bytes | `23.131` | `31.745` | `0%` |

Calculate the RTT difference:

```text
RTT Difference = Average RTT(C) - Average RTT(A)
```

**Questions:**

1. Which scenario has the highest average RTT?


2. Does increasing packet size always increase RTT in your measurements?



3. Why might a larger packet require more transmission or processing resources?

Larger IP packets require more transport block bits at the MAC/PHY layers (potentially spanning more resource blocks or multiple HARQ/RLC segments), more LDPC encoding/decoding cycles, and larger memory copies across the virtual network interfaces and TCP sockets.

4. What factors other than packet size could affect RTT in a software-based 5G network?

Host CPU load, Linux/WSL2 thread scheduling jitter, Docker virtual bridge overhead, background processes, and TDD frame structure alignment (waiting for the next UL/DL slot) all influence RTT.

5. Can these results be interpreted as real over-the-air 5G latency? Explain.

No. Real over-the-air 5G latency is governed by hardware processing pipelines, RF front-end delays, air propagation time, and channel retransmissions (HARQ) caused by noise/fading, whereas RFsimulator reflects software execution speed and local TCP socket latency.

Do not assume that RTT must increase with packet size. Use your measured values to support your explanation.

## 7. Task 5 — Diagnose a Controlled UE Registration Failure

In this task, you will deliberately introduce one configuration error and investigate why the UE cannot complete registration.

**Important:** Save the original successful UE command before starting. Do not modify the CN5G subscriber database.

### Step 1 — Stop the UE

Press `Ctrl+C` in the nrUE terminal. Keep the CN5G and gNB running.

### Step 2 — Launch the UE with an Incorrect IMSI

Change only the IMSI:

```bash
sudo ./nr-uesoftmodem \
  -r 106 \
  --numerology 1 \
  --band 78 \
  -C 3619200000 \
  --uicc0.imsi 001010000000099 \
  --rfsim \
  --rfsimulator.serveraddr 127.0.0.1
```

The IMSI `001010000000099` is not provisioned in the standard classroom subscriber configuration. Verify this assumption against the instructor's database before class.

Observe the UE and AMF logs.

```bash
cd ~/oai-cn5g
docker compose logs --since=2m oai-amf
```

Allow time for registration attempts, then stop the UE.

Complete the table:

| Item | Observation |
|---|---|
| Modified parameter | `--uicc0.imsi` changed from `001010000000001` to `001010000000099` |
| UE synchronized with gNB? | Yes (`UE 0` synchronized, completed 4-Step CBRA random access, and obtained `RNTI 3ce3`) |
| RRC connection established? | Yes (`[NR_RRC] State = NR_RRC_CONNECTED` and `Added srb 1 to UE 0`) |
| Registration successful? | No |
| Error or rejection evidence | nrUE log showed `[NAS] [UE 0] Received NAS_DOWNLINK_DATA_IND type FGS_REGISTRATION_REJECT` (`Received Registration reject`), and `ip -4 addr show oaitun_ue1` returned `Device "oaitun_ue1" does not exist.` |
| Likely cause | IMSI `001010000000099` is not provisioned in the CN5G subscriber database (UDM/MySQL), causing AUSF/AMF authentication to fail. |

If the expected registration rejection does not appear, report the actual logs instead of inventing a failure message.

### Step 3 — Restore the Original IMSI

Restart the nrUE using:

```text
--uicc0.imsi 001010000000001
```

Confirm that the UE successfully registers again and that Ping works.

**Questions:**

1. Why can the UE potentially synchronize with the gNB even when the IMSI is incorrect?

Cell search and synchronization rely solely on broadcast physical-layer signals (PSS, SSS, PBCH/MIB, and SIB1), which contain no subscriber-specific information and require no authentication.

2. Which network function is involved in UE authentication?

The **AUSF** (Authentication Server Function), working together with the **UDM** (Unified Data Management, which stores subscriber credentials) and the **AMF** (which relays NAS authentication messages).

3. Why does changing an IMSI affect Registration but not the RFsimulator TCP connection itself?

The RFsimulator TCP connection operates below the 5G protocol stack to transport raw IQ samples between the simulated radios. The IMSI is a core-network subscriber identifier evaluated much higher up in the NAS layer during authentication.

4. What evidence proves that restoring the correct configuration solved the problem?

When running with the valid IMSI `001010000000001`, the UE completed NAS registration (`5GMM-REGISTERED`), the `oaitun_ue1` tunnel interface was created with IP `10.0.0.2/24`, and pinging `192.168.70.135` succeeded with `0%` packet loss (average RTT of `18.335 ms` over 10 packets and `15.303 ms` over 30 packets).

Submit evidence from both the failed and recovered connections.


## 8. Task 7 — Explain the Relationship Between Simulation and Real 5G

Your OAI gNB and nrUE perform 5G NR protocol processing even though they do not use physical antennas.

Complete the comparison:

| Feature | OAI RFsimulator | Physical 5G System |
|---|---|---|
| gNB and UE protocol stack | Full 5G NR stack executed in software on host CPU | Executed on dedicated baseband hardware (BBU/DU/CU) and UE modem chipsets |
| OFDM signal processing | Performed in software (`nr-softmodem` / `nr-uesoftmodem`) | Performed in real time on FPGAs, ASICs, or DSPs |
| Physical antennas | Replaced by a local TCP socket (port 4043) | Required for radiating and receiving electromagnetic waves |
| RF hardware impairments | Absent by default (idealized IQ transfer) | Present (phase noise, IQ imbalance, power amplifier non-linearity) |
| Wireless propagation effects | Absent by default (unless channel modeling is enabled) | Present (path loss, multipath fading, Doppler shift, interference) |
| 5G Core connectivity | Real NGAP/GTP-U interfaces connected to OAI CN5G | Real NGAP/GTP-U interfaces connected to production 5GC |

**Questions:**

1. Which parts of the 5G system remain functional when physical RF hardware is replaced with RFsimulator?

The entire 5G Core (AMF, SMF, UPF, AUSF, UDM) and the complete 5G NR RAN protocol stack (NAS, RRC, SDAP, PDCP, RLC, MAC, and baseband PHY) remain active and functional.

2. Why is RFsimulator useful for testing the 5G protocol stack?

It eliminates the cost, licensing, and hardware complexity of SDRs/antennas while offering a deterministic, reproducible environment ideal for debugging signaling flows and core-RAN integration.

3. Why might latency and throughput differ between RFsimulator and a real 5G deployment?

RFsimulator is bounded by general-purpose CPU speed and OS scheduling jitter rather than real-time hardware clocks, and it omits wireless channel impairments (interference, fading, path loss) that dynamically reduce throughput and trigger HARQ retransmissions in real networks.

4. What would need to change if you wanted to test a physical UE instead of OAI nrUE?

WE would need to replace RFsimulator with a supported SDR (such as a USRP) and antennas connected to the gNB, operate in an RF-shielded enclosure or licensed frequency band, and provision a physical programmable SIM/USIM card with matching IMSI, K, and OPc values in the CN5G database.

## 9. Final Analysis

Answer each question in three to five sentences.

1. Describe the complete process from starting the OAI 5GC to successful user-plane connectivity.

First, OAI CN5G containers are launched via Docker Compose, initializing the core network functions (AMF, SMF, UPF, AUSF, UDM). Next, the gNB starts and establishes an N2 control-plane association with the AMF via NG Setup. The nrUE then connects to the gNB over RFsimulator, synchronizes with broadcast signals, establishes an RRC connection, and completes NAS Registration and authentication with the AMF/AUSF. Finally, a PDU Session is established, creating the GTP-U tunnel to the UPF and bringing up the `oaitun_ue1` interface (`10.0.0.2`), enabling end-to-end IP pings to the External DN (`192.168.70.135`).

2. Explain the difference between an RFsimulator TCP connection and a 5G PDU Session.

The RFsimulator TCP connection is a simulation artifact on port 4043 that transports raw baseband IQ samples between `nr-softmodem` and `nr-uesoftmodem` in place of physical antennas. In contrast, a 5G PDU Session is a logical 3GPP user-plane service connecting the UE to an external data network via GTP-U tunnels across the gNB and UPF. The TCP socket emulates the physical radio medium, whereas the PDU Session carries the actual user IP traffic over that medium.

3. Based on your measurements, how did packet size affect RTT and packet loss?

In my measurements, increasing the ICMP payload from 56 bytes to 512 bytes and 1200 bytes caused the average RTT to increase steadily from **15.303 ms** to **19.265 ms** and **23.131 ms**, yielding a net difference of **7.828 ms** between Scenario C and Scenario A. Packet loss remained at **0%** across all three scenarios. This shows that larger payloads incur additional baseband processing and serialization overhead without causing packet drops in the lossless TCP-based simulator.

4. Describe the registration failure you introduced and explain how you diagnosed and recovered from it.

I introduced a controlled failure by changing the UE's `--uicc0.imsi` parameter from `001010000000001` to the unprovisioned value `001010000000099`. While the UE still synchronized at the physical layer and entered `NR_RRC_CONNECTED`, inspecting the nrUE logs revealed `FGS_REGISTRATION_REJECT` at the NAS layer, and `ip -4 addr show oaitun_ue1` confirmed that no tunnel interface was created (`Device "oaitun_ue1" does not exist.`). Restoring the valid IMSI (`001010000000001`) allowed the UE to register and establish its PDU session (`10.0.0.2`), which was verified by pinging `192.168.70.135` with `0%` packet loss.

5. Identify two limitations of this simulated environment and explain how they might affect experimental results.

First, RFsimulator bypasses real wireless channel effects (path loss, multipath fading, interference) and RF hardware impairments, which leads to artificially low packet loss (0%) and stable radio conditions compared to real deployments. Second, running the entire core and RAN in software on a single host makes timing and throughput sensitive to CPU load and OS scheduling jitter rather than real-time hardware constraints, meaning observed RTT values reflect host compute performance rather than true air-interface latency.

## 10. Submission Checklist

Submit one Markdown or PDF report containing:

- Completed 5G SA connection verification table.
- gNB and nrUE connection screenshots.
- RFsimulator TCP connection evidence.
- Baseline Ping measurement.
- Three packet-size comparison results.
- RTT difference calculation.
- Controlled failure and recovery evidence.
- RFsimulator versus physical 5G comparison.
- Answers to the final analysis questions.

All measurements and log evidence must come from your own experimental environment.

## 11. Grading Rubric

| Item | Points |
|---|---:|
| Complete 5G SA deployment | 15 |
| RFsimulator TCP connection analysis | 15 |
| End-to-end user-plane verification | 15 |
| Packet-size experiment and analysis | 20 |
| Controlled failure and recovery | 20 |
| Simulation limitations and final analysis | 15 |
| **Total** | **100** |

Vote TOP3：https://forms.gle/Mvza68DFBzPcZXfW6
