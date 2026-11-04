---
title: Lab 2(student)

---

# Lab 2: gNB TDD Traffic Analysis

## 1. Goal

In this lab, you will compare three 5-second UDP iperf3 tests. You will learn how TDD slot allocation can affect downlink and uplink performance.

You will also read the broadcast TDD configuration from SIB1 in Wireshark, draw the downlink/uplink time allocation, and relate the configuration to the iperf3 results.

You do not need to understand every packet. Follow the steps, complete the tables, and answer the short questions.

## 2. Test Scenarios and Files

| Scenario | TDD setting | Traffic direction | Main idea |
| --- | --- | --- | --- |
| A | DL-heavy | Downlink | The TDD setting favors the traffic direction |
| B | DL-heavy | Uplink | There are fewer opportunities for uplink traffic |
| C | Balanced | Uplink | More uplink opportunities are available than in B |

[Download the lab files from Google Drive](https://drive.google.com/drive/u/0/folders/1gTgosNkWFuak_sXbHFTxqaRqXb15Wz9T).

### Two Types of Packet Captures

Two types of packet captures are provided in this lab:

- **Configuration captures:** Recorded separately during initial cell access to show the broadcast SIB1 messages for the two TDD settings. Use these files to read and draw the common TDD configuration. Only two configuration captures are required because Scenarios A and B share the DL-heavy setting.
- **Scenario captures:** Recorded during the iperf3 tests. Use these files to analyze user-plane packets and the TCP control connection. Separate captures are provided for A, B, and C because each scenario uses a different combination of TDD setting and traffic direction.

The configuration captures are reference recordings for the corresponding settings, not simultaneous recordings of the original iperf3 runs. The scenario-to-configuration mapping below is supplied by the instructor; it cannot be established from the iperf3 JSON alone. Configuration captures are not used to calculate test throughput, loss, jitter, RTT, or packet intervals.

### Configuration Captures — Task 4 Only

| TDD setting | Applies to | Configuration capture |
| --- | --- | --- |
| DL-heavy | Scenarios A and B | `tdd-dl-heavy-sib1.pcapng` |
| Balanced | Scenario C | `tdd-balanced-sib1.pcapng` |

### Performance Files — Tasks 1–3 and 5–8

| Scenario | iperf3 JSON | Scenario capture |
| --- | --- | --- |
| A | `scenario-a-downlink.json` | `scenario-a-dl-heavy-downlink.pcapng` |
| B | `scenario-b-uplink.json` | `scenario-b-dl-heavy-uplink.pcapng` |
| C | `scenario-c-uplink.json` | `scenario-c-balanced-uplink.pcapng` |

> The JSON files report the traffic direction and performance results. They do not contain the gNB TDD configuration. Use the configuration captures for SIB1 and the scenario captures for traffic analysis.

## 3. Task 1 — Confirm the Traffic Direction

Open each JSON file and find:

```text
start → test_start → reverse
```

- `reverse: 1` means downlink in this lab.
- `reverse: 0` means uplink in this lab.

Complete the table:

| Scenario | Reverse value | Direction |
| --- | ---: | --- |
| A | 1 | DL |
| B | 0 | UP |
| C | 0 | UP |

**Question:** Does the traffic direction shown in the JSON match the scenario description? Show the proof.

Yes, the traffic direction shown in each JSON file matches the scenario description provided in the lab instructions.

A. 
<img width="1433" height="725" alt="image" src="https://github.com/user-attachments/assets/6dec5ef1-cb19-4ed1-a7a3-6026541500c5" />

B. 
<img width="1433" height="725" alt="image" src="https://github.com/user-attachments/assets/c5c77473-d9d0-4a67-9cb3-06bb4fb58481" />

C. 
<img width="1433" height="725" alt="image" src="https://github.com/user-attachments/assets/8b9ba42d-f334-493c-bef8-a35b393ee212" />




## 4. Task 2 — Compare Throughput

In each JSON file, find:

```text
end → sum → bits_per_second
```
A. bits_per_second":	90654195.8358403
<img width="1433" height="725" alt="image" src="https://github.com/user-attachments/assets/daf51b58-a8e4-45e0-a136-f45575e41d3a" />

B. bits_per_second":	109117249.69037457
<img width="1433" height="725" alt="image" src="https://github.com/user-attachments/assets/37f940e7-a68a-4960-bdee-739b2fe16b6f" />

C. bits_per_second":	124416749.13023271
<img width="1433" height="725" alt="image" src="https://github.com/user-attachments/assets/42235bb7-3118-4a6d-b9b4-81e3d217a7cb" />


Convert the value to Mbps:

```text
Throughput (Mbps) = bits_per_second ÷ 1,000,000
```


Complete the table:

| Scenario | Direction | Throughput (Mbps) |
| --- | --- | ---: |
| A | Downlink | 90.65419584 |
| B | Uplink | 109.1172497 |
| C | Uplink | 124.4167491 |

Calculate how much C improves over B:

```text
Improvement (%) = (C - B) ÷ B × 100
```
14.02115563% 

Answer:

1. What is the downlink throughput in Scenario A?

90.65 Mbps (90,654,195.84 bps / 1,000,000).

2. What is the uplink throughput in Scenario B?

109.12 Mbps (109,117,249.69 bps / 1,000,000).

3. Is the uplink throughput higher in B or C?

The uplink throughput is higher in Scenario C (124.42 Mbps vs. 109.12 Mbps).

4. By approximately what percentage does C improve over B?

Scenario C improves over Scenario B by approximately 14.02%.

> Use the JSON `bits_per_second` value. Do not recalculate throughput using the other time fields.

## 5. Task 3 — Check the Trade-off

In each JSON file, find:

```text
end → sum → lost_percent
end → sum → jitter_ms
```

Complete the table:

| Scenario | Throughput (Mbps) | Packet loss (%) | Jitter (ms) |
| --- | ---: | ---: | ---: |
| B | 109.1172497 | 0.23565878306653645 | 0.11619665995310689 |
| C | 124.4167491 | 2.133919261135111 | 0.16204804777679407 |

B. 
<img width="1433" height="725" alt="image" src="https://github.com/user-attachments/assets/ab691b3d-d676-4023-a470-45de0acc9550" />

C. 
<img width="1433" height="725" alt="image" src="https://github.com/user-attachments/assets/2493e4fc-eb1b-4cf3-8b3b-f7c76970bc42" />

Answer:

1. Does C have higher uplink throughput than B?

Yes. Scenario C achieves higher uplink throughput than Scenario B (124.42 Mbps vs. 109.12 Mbps).

2. Does C have lower packet loss than B?

No. Scenario C has higher packet loss than Scenario B (2.13% vs. 0.24%).

3. What trade-off, if any, is visible when changing from B to C?

Compared with Scenario B, Scenario C has higher throughput, higher packet loss, and higher jitter. These results suggest a trade-off between throughput performance and link stability: while allocating more uplink resources in Scenario C provides more transmission opportunities and increases overall throughput, it also introduces greater queueing variance (higher jitter) and higher packet drop rates (packet loss) under heavy load.

A simple answer format is:

> Compared with Scenario B, Scenario C has ______ throughput, ______ packet loss, and ______ jitter. These results suggest ______.

Use the measured values. If one result improves while another worsens, explain that trade-off. Do not assume that increasing UL resources always increases packet loss.

## 6. Task 4 — Read SIB1 and Draw the TDD Configuration

Use these **two configuration captures** for this task:

- `tdd-dl-heavy-sib1.pcapng`: Reference configuration for Scenarios A and B.
- `tdd-balanced-sib1.pcapng`: Reference configuration for Scenario C.

These files were recorded separately from the original iperf3 tests. Use them to examine the supplied reference settings.

### 4.1 What Is SIB1?

A gNB broadcasts system information so that a UE can learn how to access the cell.

- **MIB (Master Information Block):** Provides basic information, including parameters needed to find SIB1.
- **SIB1 (System Information Block Type 1):** Provides cell-access and common radio configuration information. In this TDD lab, it includes `tdd-UL-DL-ConfigurationCommon`.

You will read the **common TDD configuration in SIB1**, not decode every MIB/SIB field. This configuration describes DL, UL, and flexible time resources; it is not a record of the actual data scheduled in every slot.

### 4.2 Enable MAC-NR Decoding and Find SIB1

These captures contain NR MAC messages carried over UDP. **Enable MAC-NR-over-UDP decoding before applying the SIB1 filter.** Without this decoder, the packets may appear only as UDP and the SIB1 filter may return no results.

1. Open `tdd-dl-heavy-sib1.pcapng` in Wireshark.
2. Open **Analyze → Enabled Protocols**. Locate **MAC-NR over UDP** (`mac_nr_udp`) in the heuristic dissectors list and enable it. Depending on the Wireshark version, the heuristic list may be shown separately. Apply the change and reload the capture if needed.
3. Apply this display filter:

   ```text
   nr-rrc.systemInformationBlockType1_element
   ```


4. Select a SIB1 packet. In the packet details, expand:

   ```text
   NR Radio Resource Control (RRC) protocol
     → BCCH-DL-SCH-Message
       → message
         → c1
           → systemInformationBlockType1
             → servingCellConfigCommon
               → tdd-UL-DL-ConfigurationCommon
   ```

5. Read `referenceSubcarrierSpacing`, then expand `pattern1` and record:

   ```text
   dl-UL-TransmissionPeriodicity
   nrofDownlinkSlots
   nrofDownlinkSymbols
   nrofUplinkSlots
   nrofUplinkSymbols
   ```
For tdd-dl-heavy-sib1.pcapng

<img width="1433" height="900" alt="image" src="https://github.com/user-attachments/assets/ba422bb2-15e0-443d-bbad-5fdf24d149c0" />
<img width="1433" height="900" alt="image" src="https://github.com/user-attachments/assets/887974d2-c2fc-400e-9ed8-a027ac30d6cb" />

For tdd-balanced-sib1.pcapng
<img width="1433" height="900" alt="image" src="https://github.com/user-attachments/assets/7959a288-911e-4af5-80ec-f84314c7c3d9" />




6. Check whether `pattern2` is also present.
7. Repeat for `tdd-balanced-sib1.pcapng`.

Record the **decoded labels and units** shown in Wireshark. For example, record `30 kHz` or `5 ms`, not the enumeration number displayed in parentheses.

You can also locate packets containing the TDD configuration with:

```text
nr-rrc.tdd_UL_DL_ConfigurationCommon_element
```

Confirm that the selected TDD fields are inside **SIB1**. If a filter is not recognized in your version, try `nr-rrc` and locate `systemInformationBlockType1` manually.

> **Troubleshooting:** If packets still appear only as UDP, check that the **MAC-NR over UDP heuristic dissector** is enabled, rather than only the MAC-NR protocol. If the file still does not decode, ask the instructor to check the settings. Do not infer TDD parameters from packet timing. Graphical menu labels may vary by version.

### 4.3 Record the TDD Parameters

Complete the table for `pattern1`:

| Item | DL-heavy: A/B | Balanced: C |
| --- | --- | --- |
| Configuration capture filename | tdd-dl-heavy-sib1.pcapng | tdd-balanced-sib1.pcapng |
| SIB1 packet number | 2 | 2 |
| `referenceSubcarrierSpacing` (kHz) | 30 | 30 |
| `dl-UL-TransmissionPeriodicity` (ms) | 5 | 2.5 |
| `nrofDownlinkSlots` | 7 | 2 |
| `nrofDownlinkSymbols` | 6 | 6 |
| `nrofUplinkSlots` | 2 | 2 |
| `nrofUplinkSymbols` | 4 | 4 |
| Is `pattern2` present? | no | no |

If `pattern2` is present, add another table containing its period and four slot/symbol counts. It uses the same reference SCS.

Take **one screenshot per configuration** showing the selected SIB1 packet and the expanded TDD fields. Include `pattern2` in an additional screenshot if it is present and does not fit.

dl heavy 
<img width="1433" height="900" alt="image" src="https://github.com/user-attachments/assets/2211ad33-337f-4ffa-8023-9d7971f1c28b" />

balanced 
<img width="1433" height="900" alt="image" src="https://github.com/user-attachments/assets/ea25a3c6-3c0b-442d-abd8-a70989123ac5" />


### 4.4 Draw the TDD Time Allocation

Draw one diagram for DL-heavy and one for balanced. **Use the same 0–5 ms time axis for both diagrams.** Derive each repeating period from SIB1 and repeat the shorter pattern as needed to fill the 5 ms interval. Mark every repeating-period boundary.

A spreadsheet, a drawing tool, or a hand-drawn diagram is acceptable. Include the diagrams as images in your report.

#### DL-Heavy 

```mermaid
gantt
    title DL-Heavy TDD Time Allocation (5 ms Period)
    dateFormat mm:ss.SSS
    axisFormat %S.%L ms

    section DL-Heavy (5 ms)
    Slot 0 (D)               :active, d0, 00:00.000, 00:00.500
    Slot 1 (D)               :active, d1, 00:00.500, 00:01.000
    Slot 2 (D)               :active, d2, 00:01.000, 00:01.500
    Slot 3 (D)               :active, d3, 00:01.500, 00:02.000
    Slot 4 (D)               :active, d4, 00:02.000, 00:02.500
    Slot 5 (D)               :active, d5, 00:02.500, 00:03.000
    Slot 6 (D)               :active, d6, 00:03.000, 00:03.500
    Slot 7 (Mixed 6D 4F 4U)  :crit, m7, 00:03.500, 00:04.000
    Slot 8 (U)               :done, u8, 00:04.000, 00:04.500
    Slot 9 (U)               :done, u9, 00:04.500, 00:05.000
```

#### Balanced 

```mermaid
gantt
    title Balanced TDD Time Allocation (2.5 ms Period - 2 Repetitions in 5 ms)
    dateFormat mm:ss.SSS
    axisFormat %S.%L ms

    section Period 1 (0.0 - 2.5 ms)
    Slot 0 (D)               :active, d0, 00:00.000, 00:00.500
    Slot 1 (D)               :active, d1, 00:00.500, 00:01.000
    Slot 2 (Mixed 6D 4F 4U)  :crit, m2, 00:01.000, 00:01.500
    Slot 3 (U)               :done, u3, 00:01.500, 00:02.000
    Slot 4 (U)               :done, u4, 00:02.000, 00:02.500

    section Period 2 (2.5 - 5.0 ms)
    Slot 5 (D)               :active, d5, 00:02.500, 00:03.000
    Slot 6 (D)               :active, d6, 00:03.000, 00:03.500
    Slot 7 (Mixed 6D 4F 4U)  :crit, m7, 00:03.500, 00:04.000
    Slot 8 (U)               :done, u8, 00:04.000, 00:04.500
    Slot 9 (U)               :done, u9, 00:04.500, 00:05.000

```



For the normal cyclic prefix used in this exercise, each reference slot contains **14 OFDM symbols**, numbered **0–13**. Use the SIB1 **reference SCS** to construct the common pattern:

| Reference SCS | Reference slot duration |
| --- | ---: |
| 15 kHz | 1 ms |
| 30 kHz | 0.5 ms |
| 60 kHz | 0.25 ms |
| 120 kHz | 0.125 ms |

```text
Number of reference slots in a pattern = Pattern period ÷ Reference slot duration
```

For each pattern:

1. Place `nrofDownlinkSlots` full DL slots at the beginning.
2. If `nrofDownlinkSymbols` is nonzero, mark that many symbols at the beginning of the next slot as DL.
3. Place `nrofUplinkSlots` full UL slots at the end.
4. If `nrofUplinkSymbols` is nonzero, mark that many symbols at the end of the slot immediately before the full UL slots as UL. If there are no full UL slots, use the last slot of the pattern.
5. Mark all remaining symbols as **F (flexible)**. The partial DL and partial UL portions may be in the same slot or in different slots.

Use **D = downlink**, **U = uplink**, and **F = flexible**. Include a legend, the common 0–5 ms time scale, slot indices, and repeating-period boundaries. You may restart the local slot index at zero at each period boundary, but label the boundaries clearly. Expand any mixed slot to show all 14 symbols. Do not automatically label flexible symbols as UL or guard time.

If `pattern2` is present, draw `pattern1` followed by `pattern2`; the combined sequence repeats. Label each pattern boundary and show the full combined duration.

First, count the symbols over **one complete repeating sequence** for each configuration. The two sequences may have different durations, so their raw UL symbol counts alone cannot be used to compare resources per unit time:

```text
Configured DL symbols = 14 × Full DL slots + Partial DL symbols
Configured UL symbols = 14 × Full UL slots + Partial UL symbols
Flexible symbols = Total symbols - Configured DL symbols - Configured UL symbols
Configured UL symbol share (%) = Configured UL symbols ÷ Total symbols × 100
```

For two patterns, sum the counts and durations of both patterns before calculating the share. These are symbol-count shares of the common configuration, not exact airtime measurements or measured throughput shares.

| TDD setting | Repeating duration (ms) | Total reference slots | DL symbols | UL symbols | Flexible symbols | Configured UL symbol share (%) |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| DL-heavy | 5 | 10 | 104 | 32 | 4 | 22.86% |
| Balanced | 2.5 | 5 | 34 | 32 | 4 | 45.71% |

Next, count the symbols over the **same 5 ms interval** shown in your diagrams. Multiply each per-sequence count by the number of complete repetitions in 5 ms. For these captures, 5 ms contains a whole number of repetitions for both configurations.

| TDD setting | Repeating duration (ms) | Repetitions in 5 ms | DL symbols in 5 ms | UL symbols in 5 ms | Flexible symbols in 5 ms |
| --- | ---: | ---: | ---: | ---: | ---: |
| DL-heavy | 5 | 1 | 104 | 32 | 4 |
| Balanced | 2.5 | 2 | 68 | 64 | 8 |

**Question:** Can two patterns have the same UL symbol count per period but provide different numbers of UL symbols per unit time? Explain using your two tables.

Yes. As shown in Table 1, both the DL-heavy and Balanced configurations contain the exact same number of uplink symbols per repeating sequence (32 UL symbols per period).    wireless lab2 (1).pdf + 1 However, because the Balanced pattern has a shorter repeating duration of 2.5 ms compared to 5 ms for DL-heavy, it completes 2 full repetitions within a standard 5 ms timeframe. As shown in Table 2, this provides 64 UL symbols per 5 ms in the Balanced setting versus only 32 UL symbols per 5 ms in the DL-heavy setting. Therefore, the shorter periodicity doubles the uplink transmission opportunities per unit time (45.71% UL share vs. 22.86% UL share), even though their per-period UL symbol counts are identical.

### 4.5 Connect SIB1 to the Performance Results

Use the supplied mapping between the reference configuration captures and scenarios. Complete this table using Tasks 1–3 and your SIB1 analysis:

| Scenario | Reference TDD setting | JSON traffic direction | Configured UL symbol share (%) | Throughput (Mbps) | Packet loss (%) |
| --- | --- | --- | ---: | ---: | ---: |
| A | DL-heavy | DL | 22.86% | 90.65 | 0.44% |
| B | DL-heavy | UP | 22.86% | 109.12 | 0.24% |
| C | Balanced | UP | 45.71% | 124.42 | 2.13% |

Answer:

1. Which decoded TDD parameters differ between DL-heavy and balanced?

The two parameters that differ in SIB1 are dl-UL-TransmissionPeriodicity (5 ms for DL-heavy vs. 2.5 ms for Balanced) and nrofDownlinkSlots (7 slots for DL-heavy vs. 2 slots for Balanced). The other parameters (referenceSubcarrierSpacing = 30 kHz, nrofDownlinkSymbols = 6, nrofUplinkSlots = 2, and nrofUplinkSymbols = 4) are identical across both configurations.

2. Which configuration provides more configured UL symbols per unit time? Support your answer with the diagram and calculated share.

The Balanced configuration provides more UL symbols per unit time. As calculated in Task 4.4, the Balanced pattern doubles the configured UL symbol share from 22.86% to 45.71%. Within the common 5 ms time scale, the DL-heavy diagram shows only 1 pattern repetition yielding 32 UL symbols, whereas the Balanced diagram shows 2 pattern repetitions yielding 64 UL symbols.

3. How does that difference help explain the B/C throughput comparison?

Doubling the UL symbol allocation per unit time in Scenario C provides twice as many time slots for the UE to transmit uplink data frames. This significant increase in physical layer transmission opportunities directly reduces uplink bottlenecking, enabling Scenario C to achieve higher throughput (124.42 Mbps) compared to Scenario B (109.12 Mbps).

4. Why can A and B use the same SIB1 TDD configuration even though their traffic directions differ?

SIB1 broadcasts the cell's common TDD frame allocation structure, defining available radio time resources rather than controlling actual user-plane traffic flows. Scenario A and Scenario B use the exact same cell-wide DL-heavy radio channel configuration, but test different application layer traffic directions (Scenario A generates Downlink data from server to UE, while Scenario B generates Uplink data from UE to server).

> More configured UL resources can provide more opportunities for uplink traffic, but they do not guarantee a proportional throughput increase. Scheduling, radio conditions, overhead, offered traffic, and other radio settings also affect the result. This comparison does not establish that the TDD pattern is the only cause of a performance difference. SIB1 does not show actual slot-by-slot data scheduling. Because the configuration captures were recorded separately, use them as references for the supplied settings, not as independent proof of what was broadcast during each original performance run.

### Optional Observation — PRACH Configuration Index

In the same SIB1, find:

```text
servingCellConfigCommon
  → uplinkConfigCommon
    → initialUplinkBWP
      → rach-ConfigCommon
        → setup
          → rach-ConfigGeneric
            → prach-ConfigurationIndex
```

Wireshark may omit or display the `setup` layer differently. You can also use this display filter, then confirm the field is inside SIB1:

```text
nr-rrc.prach_ConfigurationIndex
```

| TDD setting | SIB1 packet number | PRACH configuration index |
| --- | ---: | ---: |
| DL-heavy | 2 | 98 |
| Balanced | 2 | 98 |

PRACH is used to send a random-access preamble. Its configuration index is not the DL/UL slot ratio and does not directly explain iperf3 throughput. Equal indices in the two configurations are a valid observation. Drawing PRACH occasions requires additional parameters and the applicable TS 38.211 table; it is outside the required TDD drawing task.

## 7. Task 5 — Is the TDD Setting Suitable?

Complete the table using the supplied scenario mapping, the SIB1 reference configurations from Task 4, and your throughput results:

| Scenario | TDD setting | Traffic direction | Is the setting suitable for this direction? Why? |
| --- | --- | --- | --- |
| A | DL-heavy | Downlink | Yes. The DL-heavy configuration allocates a 74.3% downlink symbol share (104 out of 140 symbols in 5 ms). This provides abundant downlink transmission opportunities matching heavy download traffic, enabling a high throughput of 90.65 Mbps. |
| B | DL-heavy | Uplink | No. The DL-heavy setting limits uplink opportunities to a 22.86% symbol share (32 out of 140 symbols in 5 ms). Restricting uplink transmission opportunities under heavy uplink traffic limits performance to 109.12 Mbps. |
| C | Balanced | Uplink | Yes (More suitable than B). The balanced setting doubles the uplink resource allocation to a 45.71% symbol share (64 out of 140 symbols in 5 ms). Giving uplink traffic twice as many opportunities improves throughput to 124.42 Mbps. |

Use these ideas:

- More DL resources provide more downlink transmission opportunities.
- More UL resources provide more uplink transmission opportunities.
- A DL-heavy setting is suitable for downlink traffic.
- A DL-heavy setting may limit heavy uplink traffic.
- A balanced setting gives uplink traffic more opportunities than the DL-heavy setting in this lab.

> The configuration captures show the reference broadcast TDD settings. The iperf3 JSON reports performance; it does not contain TDD parameters. The scenario captures are used for traffic analysis and need not include SIB1.

**Question:** Why might Scenario C achieve better uplink throughput than Scenario B? Refer to your SIB1 diagrams and measured results.

Scenario C gets higher uplink throughput than Scenario B (124.42 Mbps vs. 109.12 Mbps, which is a 14.02% increase) because its TDD setting gives the UE twice as many chances to send data. As shown in the SIB1 diagrams: Scenario B (DL-heavy) has a longer 5 ms pattern with only 2 full Uplink slots, giving 32 Uplink symbols every 5 ms (22.86% share).     Scenario C (Balanced) has a shorter 2.5 ms pattern that repeats 2 times in 5 ms, giving 64 Uplink symbols every 5 ms (45.71% share). Because Scenario C doubles the number of Uplink symbols per unit of time, the UE spends less time waiting and can upload more data faster.


## 8. Task 6 — Find GTP-U Information

Open a **scenario capture** in Wireshark and enter this display filter:

```text
gtp && ip
```

Choose a packet that contains two IPv4 headers. In the packet details, expand:

1. the first `Internet Protocol Version 4` header;
2. `User Datagram Protocol`;
3. `GPRS Tunneling Protocol`; and
4. the second `Internet Protocol Version 4` header.

Record the following information from one packet:

| Item | Value |
| --- | --- |
| Scenario capture filename | scenario-a-dl-heavy-downlink.pcapng | scenario-b-dl-heavy-uplink.pcapng | scenario-c-balanced-uplink.pcapng |
| Packet number | 1831 | 2065 | 1430 |
| Outer source IP | 192.168.70.129 | 192.168.70.129 | 192.168.70.129 |
| Outer destination IP | 192.168.70.134 | 192.168.70.134 | 192.168.70.134 |
| Inner source IP | 10.0.0.6 | 10.0.0.6 | 10.0.0.6 |
| Inner destination IP | 192.168.70.135 | 192.168.70.135 | 192.168.70.135 |
| TEID | 0x00000011 | 0x00000012 | 0x00000013 |

Meaning:

- **Outer IP addresses:** The GTP-U tunnel endpoints.
- **Inner IP addresses:** The original UE/application packet.
- **TEID:** Identifies the GTP-U tunnel at the receiving endpoint.

Take one screenshot showing the selected packet and these fields.

#### scenario-a-dl-heavy-downlink.pcapng
<img width="1433" height="900" alt="image" src="https://github.com/user-attachments/assets/d7199ed8-842b-4301-a2d4-7f8a36634455" />
<img width="1433" height="900" alt="image" src="https://github.com/user-attachments/assets/3756e27b-f915-4a67-a25d-9734cc671f38" />
<img width="1433" height="900" alt="image" src="https://github.com/user-attachments/assets/42b4745f-ac8e-4cc7-91d7-24d5d2b13bdf" />

#### scenario-b-dl-heavy-uplink.pcapng
<img width="1433" height="900" alt="image" src="https://github.com/user-attachments/assets/4a3f7c69-d842-42be-91ff-64ca93781716" />
<img width="1433" height="900" alt="image" src="https://github.com/user-attachments/assets/e022cce7-6a74-468c-8406-1a522e14ebaf" />
<img width="1433" height="900" alt="image" src="https://github.com/user-attachments/assets/f0c6571f-1276-4a94-a272-cbf0feb87673" />

#### scenario-c-balanced-uplink.pcapng
<img width="1433" height="900" alt="image" src="https://github.com/user-attachments/assets/20222094-db1d-4bb5-9529-ac5abdfc867a" />
<img width="1433" height="900" alt="image" src="https://github.com/user-attachments/assets/185c7b96-38e8-43e6-8bb4-79258afd4d61" />
<img width="1433" height="900" alt="image" src="https://github.com/user-attachments/assets/771ab56e-3ff4-49f0-b500-2e78fc07a508" />


> Some GTP packets are echo or control-related packets. Select one that contains an inner IPv4 packet.

## 9. Task 7 — TCP Retransmissions

Use the **scenario captures** for this task.

The performance traffic is UDP, but iperf3 also uses a small TCP control connection.

Apply this Wireshark filter:

```text
tcp.analysis.retransmission
```

Record the number of displayed packets:

| Scenario | Displayed TCP retransmissions |
| --- | ---: |
| A | 14 | <img width="1433" height="900" alt="image" src="https://github.com/user-attachments/assets/bddeb226-9f82-4dc8-9530-ef0214c9f888" /> |

| B | 12 | <img width="1433" height="900" alt="image" src="https://github.com/user-attachments/assets/c5692dbd-b85f-4a98-a0f9-07ee3696ffb9" /> |

| C | 12 | <img width="1433" height="900" alt="image" src="https://github.com/user-attachments/assets/6031b20b-039c-496c-928d-ad5ad4cec9a8" /> |


> Report the number displayed by Wireshark using the specified filter. Counts may vary with Wireshark analysis settings. Include screenshots showing the filter and displayed count for each scenario. The filter includes any TCP flows that Wireshark can decode in the capture; a displayed retransmission is not, by itself, proof of loss in the UDP test.

**Question:** Do these TCP retransmissions directly represent lost UDP performance packets?

No, these TCP retransmissions do not represent lost UDP performance packets.
The main test data is sent using UDP, which does not retransmit lost packets. The retransmissions caught by the filter come from the separate TCP control connection that iperf3 uses to start, manage, and end the test. Therefore, a retransmission on the TCP control connection is not proof of lost UDP data packets.

## 10. Task 8 — RTT and Packet Interval

Use a **scenario capture** for both parts of this task.

### TCP RTT

Apply:

```text
tcp.analysis.ack_rtt
```

Select one packet from the iperf3 TCP control connection and record its ACK RTT:

| Scenario | Packet number | Example TCP ACK RTT |
| --- | ---: | --- |
| A | 1833 | 485.000 microseconds |

This value is the RTT of the TCP control connection. It is not the RTT of the UDP data packets.

<img width="1433" height="900" alt="image" src="https://github.com/user-attachments/assets/49500477-f9ef-4953-beb3-1cbb3bb68c4e" />

### Packet Interval

Apply a display filter to select UDP data packets from the same flow.

Select two consecutive, distinct UDP data packets in the filtered packet list. Avoid duplicated observations caused by merged captures; use the same capture point/interface when possible.

In the packet details of the second packet, find:

```text
Time delta from previous displayed frame
```
<img width="1433" height="900" alt="image" src="https://github.com/user-attachments/assets/4b563e3a-f7f7-4478-9296-7ae356bb03b5" />


Record the scenario, display filter, packet numbers, and time interval.

| Scenario | Display filter | Packet numbers | Time interval |
| --- | --- | --- | --- |
| A scenario-a-dl-heavy-downlink.pcapng | tcp.analysis.ack_rtt && udp | 1833 - 1842 | 18.162000 milliseconds |

**Note:** The time interval depends on the applied display filter. Make sure the selected packets are distinct data packets, not duplicated observations from different capture points. Do not use their interval to infer the TDD slot pattern.

## 11. Final Questions

Answer each question in two or three sentences:

1. Does Scenario A use a TDD setting that matches its traffic direction?

Yes, Scenario A uses a DL-heavy TDD setting for downlink traffic. This setting gives 74.3% of the time to downlink, helping download speed reach 90.65 Mbps.

2. Why is Scenario B expected to have limited uplink resources? Cite a parameter or count from the DL-heavy SIB1 reference configuration.

Scenario B has limited uplink space because its DL-heavy setting gives only 2 full uplink slots (nrofUplinkSlots: 2). This leaves only 32 uplink symbols every 5 ms, giving the UE very few chances to upload data.

3. How much does uplink throughput change from B to C?

Uplink throughput goes up from 109.12 Mbps in Scenario B to 124.42 Mbps in Scenario C. This is an improvement of about 14.02% because Scenario C gives twice as much uplink time.

4. What negative result, if any, is visible in C? Support your answer with packet loss or jitter values.

Scenario C causes higher packet loss and slightly higher jitter. Packet loss jumps from 0.24% in Scenario B to 2.13% in Scenario C, while jitter goes from 0.116 ms to 0.162 ms.

5. Why can increasing UL resources improve uplink throughput?

Giving more uplink resources gives the UE more time slots to send data. The UE waits less in line, so it can upload more data per second.

6. Is adding more UL resources always the best solution? Explain using throughput and packet loss.

No, adding more uplink time is not always best because it can make the connection unstable. Even though throughput increased in Scenario C, packet loss also got almost ten times worse (2.13%).

7. Suggest one simple follow-up test that could improve throughput without producing too much packet loss.

You can test different iperf3 sending rates in Scenario C to find the safest speed with lower packet loss. You could also test flexible slots (F) to handle uplink traffic bursts better.

8. What can the configuration captures tell you that the iperf3 JSON cannot? Why are separately recorded configuration captures not direct proof of the configuration during an earlier test?

Configuration captures show actual 3GPP SIB1 parameters like subcarrier spacing and slot patterns, which are not in iperf3 JSON files. They are not direct proof because they were recorded in a separate test run, so settings could have changed in between.

## 12. Submission Checklist

Submit one Markdown file containing:

- the completed direction table;
- the throughput table and B-to-C calculation;
- the B/C packet-loss and jitter table;
- the SIB1 TDD parameter table, including filenames and packet numbers;
- one SIB1 TDD screenshot per configuration, plus `pattern2` screenshots if needed;
- two TDD diagrams: DL-heavy and balanced, with D/U/F labels and mixed-slot symbol details;
- the per-sequence symbol-count / UL-share table, the common 5 ms comparison table, and the configuration-to-performance table;
- the Task 4.5 answers and the TDD suitability table;
- one GTP-U screenshot and its completed table;
- the TCP retransmission counts and screenshots;
- one TCP ACK RTT example;
- one packet-interval example; and
- answers to the final questions.

The PRACH observation is optional and carries no required points. Include all referenced image files alongside the Markdown file, or submit a ZIP containing the report and images.

## 13. Grading Rubric

| Item | Points |
| --- | ---: |
| Traffic direction | 5 |
| Throughput values and calculation | 20 |
| B/C packet-loss and jitter comparison | 15 |
| SIB1 TDD parameter extraction and screenshot evidence | 10 |
| TDD diagrams, symbol counts, and UL shares | 10 |
| TDD suitability and connection to measured performance | 10 |
| GTP-U fields and screenshot | 15 |
| TCP retransmission, RTT, and packet interval | 10 |
| Clear final answers | 5 |
| **Total** | **100** |

## References

These references support the field names and interpretation. Reading the full specifications is not required.

- [Wireshark NR RRC display filter reference](https://www.wireshark.org/docs/dfref/n/nr-rrc.html): SIB1 and TDD display-filter fields.
- [3GPP TS 38.331, Release 18](https://www.etsi.org/deliver/etsi_ts/138300_138399/138331/18.08.00_60/ts_138331v180800p.pdf): SIB1, TDD-UL-DL-ConfigCommon, and TDD-UL-DL-Pattern definitions.
- [3GPP TS 38.213, Release 17, Section 11.1](https://www.etsi.org/deliver/etsi_ts/138200_138299/138213/17.06.00_60/ts_138213v170600p.pdf): Interpretation of common TDD slot and symbol allocation.

