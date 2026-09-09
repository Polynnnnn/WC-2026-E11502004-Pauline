---
title: 2026 Wireless Communications (ET6207701)
tags: [Teaching]

---

# 2026 Wireless Communications (ET6207701)
###### tags: `Teaching`

:::danger
## Announcement
<font size=5>**Please**</font>
1. Create a page on **GitHub** for your [personal information](https://hackmd.io/@2xIzdkQiS9K3Pfrv6tVEtA/SJPZBxE5ex/edit); 
2. The course materials will put in moodle.
3. Please [fill this table](#Student-Class-Activity-Records) and join the LINE group if you want to take this course

:::

:::success
**Instructor:** Prof. Ray-Guang Cheng (Email:<crg@gapps.ntust.edu.tw>)
**TA:**
- Karl (Email:M11502203@mail.ntust.edu.tw)
- Henry (Email:M11502205@mail.ntust.edu.tw)

**Venue:** IB-602-2
**Time:** 8:10 ~ 11:10, Wed.

### Please Scan the QR code to join this HackMD page and LINE group
![wireless2026](https://hackmd.io/_uploads/rJSoEmadzg.jpg)

:::
    
## Outline
[TOC]



## 🏆 Course Evaluation & Peer Review Mechanism
- Reference Avg. Score: GPA 3.1~3.8 (77~85.67)

### 📊 Grading Breakdown
*   **Lab Assignments (8 Labs $\times$ 7% each)**: **56%**
*   **Final Written Examination**: **30%** *(In-person, proctored exam covering core 5G & O-RAN theoretical principles)*
*   **Class Q&A / Activity**: **14%** *(1 point per active question or answer in class, registered weekly)*

---

### 🔄 GitHub Lab Submission & Peer Review (Top 3) Policy

#### 1. Individual Git Versioning & Submission
For each of the **8 scheduled labs**, students are required to maintain a personal, dedicated **GitHub Repository**. 
*   **Requirements**: Students must document their entire implementation process, including full 5W1H logic, packet captures, CLI logs, topologies, and systematic troubleshooting logs.
*   **Friction & Integrity**: TAs will monitor **Git commit histories** to track incremental progress. Direct copy-pasting of large, monolithic AI-generated files without commit progression will be heavily penalized.
*   **Deadline**: 12:00 PM (Noon) on the Monday following the lab session. The repository branch must be locked to **Read-Only** after the deadline.

#### 2. Mutual Peer Review (Top 3 Recommendation)
To foster social learning, constructive friction, and peer-to-peer critique:
*   Following each lab deadline, every student must review their peers' public GitHub repositories.
*   **Top 3 Selection**: Each student must identify the **Top 3** peer repositories they found most exemplary.
*   **Justification**: For each selected peer, the reviewer must write a detailed peer review card outlining:
    1. *What specific qualities make this repository outstanding (e.g., exceptional scripting, elegant network parsing, or clear system diagrams)?*
    2. *What constructive improvement or follow-up experiment can be proposed for their setup?*

#### 3. Normalized Ranking Multiplier
Final lab scores are subjected to a peer-weighted ranking curve. The final grade for each lab is scaled according to your percentile class ranking (calculated from consolidated teacher, TA, and peer evaluation scores):

$$\text{Final Assignment Score} = \text{Raw Lab Grade} \times \text{Multiplier}$$

| Percentile Rank | Multiplier | Grading Band Description |
| :--- | :--- | :--- |
| **Top 90% – 100%** | **$\times$ 1.0** | Exceptional clarity, original analysis, and active peer reviews. |
| **Top 80% – 89%** | **$\times$ 0.9** | Fully functional setup with good documentation and screenshots. |
| **Top 70% – 79%** | **$\times$ 0.8** | Completed core tasks with minor gaps in analysis or evidence. |
| **Others (<70%)** | **$\times$ 0.7** | Bare-minimum execution, late commits, or lack of peer evaluation effort. |

## ToDo list
- Create a GitHub account.
- Provide your github account & repository to be used in this course in this [Google form](https://docs.google.com/forms/d/e/1FAIpQLSfkQXLx0mBsjb5zsYd6cJjgSlUgNjaN9wdQ8b_U3FzLXDa_ig/viewform?usp=header).
- Create your own repository using this format: WC-[year]-[student ID]-[English Name].
  - Ex: WC-2026-M11302832-Joshevan
- Copy the content of the template folder to your own branch & update your profile information in your README.md file.
---

### 1. Q&A
1. You will get 1 point per week if you raise a question or answer teacher's question **during class.**
2. Please fill this [google form](https://docs.google.com/forms/d/e/1FAIpQLSfO6z18kfEj4ocI1RLmmhjuMDYkszV7nJY7jZG4ZQnstwFZxQ/viewform?usp=dialog) after you raise a question during class (**Submission Deadline: 23:59 on Wed.**)

:::warning
**Key points for raising questions in the class**
* Focus on **clarifying doubts**.
* Ask **appropriate and relevant questions**.
* Treat **questioning as a skill** you can improve with practice.
* Share what you **already understand** to help the instructor explain better.
* Remember that **asking questions gets easier and less stressful over time**.


*Ref: 
[Outsmart Your Brain](https://www.simonandschuster.com/books/Outsmart-Your-Brain/Daniel-T-Willingham/9781982167172)
Why Learning is Hard and How You Can Make It Easy, 
By Daniel T. Willingham*
:::


### 2. Labs
#### Basic Requirements 
- [x] **Submit on time**: 
    - set your page to <font color=red>READ ONLY</font> and
    - **DON'T** modify it after the <font color=red>DEADLINE</font>
    - The <font color=red>DEADLINE</font> for each LAB is 12:00 noon next Monday.
    - <font color=red>show us your best version on github</font>
- [x] **Format:**
    - Copy the template for each lab and paste on your personal page.
    - [example template](https://github.com/Karlyoo/WC-2026-M11502203-Karl/blob/main/template.md)  
- [x] **Vote**:
    - For each assignment, you need to vote for the three best submissions based on your personal judgment. The three submissions receiving the most votes will earn bonus points. 


---
#### LAB1:  Analyzing UE–gNB Connectivity in an OAI 5G SA Network
- [assignment description](https://hackmd.io/@Z4OmT2gcTXeLxBPXrn-2SQ/r1YMe9M_Gg) 
- **Goal:** 
    - In this lab, you will use Wireshark to analyze how a UE establishes an RRC connection with an OAI gNB and then registers with the 5G Core.
- **Requirment and Rule:**
    - Rule: 
      1. Please provide proof for each answer using a screenshot or log.
      2. You will receive full points if you provide the correct answer for each question.
    - Requirment:
      Submit a Markdown report containing:
       - Completed tables
       - Answers to all questions
       - Packet numbers
       - Required screenshots
       - Final sequence diagram
       - use this [template](https://hackmd.io/jSE9_InoSbeYTfySOX3Szg?both) in your personal page to show your result
  - [Top3](https://docs.google.com/forms/d/e/1FAIpQLSeY8uVnBUwJ6l6CwQ6arx3JHthTJupHBeA2WwyD-EUIYqHHrg/viewform?usp=header):
     - Top1(3pts): 
     - Top2(2pts): 
     - Top3(1pt):       
---

#### LAB2: gNB TDD Traffic Analysis 
- [assignment description](https://hackmd.io/@Z4OmT2gcTXeLxBPXrn-2SQ/BJkbO0juze)
- **Goal:**
In this lab, you will compare three 5-second UDP iperf3 tests. You will learn how TDD slot allocation can affect downlink and uplink performance.

- **Requirment and Rule:**
    - Rule: 
        1. Please provide proof for each answer using a screenshot or log.
        2. You will receive full points if you provide the correct answer for each question.
          3. Paste your study note link on your personal hackmd home page's `Deliverable`.
    - Requirment:
     Submit one Markdown file
- **Reference:**
    - [PCAP file: 5G E2E CallFlows for HW in NTUST](https://drive.google.com/file/d/1C610NTzzaABf3sbSMwe1fln1Gx0JCwn8/view?usp=sharing)
    - [SSC Modes – Session and Service Continuity in 5G](https://www.techplayon.com/ssc-modes-session-and-service-continuity-in-5g/)
#### LAB3: O-RAN basic
- **Goal:**
    - The network is deployed using OpenAirInterface (OAI) with an F1-split gNB architecture, where the gNB is separated into a Central Unit (CU) and a Distributed Unit (DU). A FlexRIC Near-RT RIC and a monitoring xApp are also deployed to demonstrate basic O-RAN functionality.
    - Students will observe and analyze the communication between different network components, including CU, DU, 5G Core, Near-RT RIC, and UEs, using packet captures and Wireshark. The lab also introduces important protocols such as F1AP, NGAP, GTP, RLC, and E2AP.

---

#### LAB4: O-RAN Advanced
- **Goal:** 
    - Based on Lab3, we already learned O-RAN architecture include CU, DU, RIC. In this Lab, we will show you how the xApps connect to the Near-RT RIC, what is xApp, and how do we use it to control the RAN.
- **Ruquirement and Rule**
    - Rule:
        1. Please provide proof for each task using a screenshot or log.
        2. Make sure the xApp is successfully connected to the Near-RT RIC before sending the subscription request.
    - Ruquirement
    - An architecture diagram annotated with RAN, RIC, and interface relationships
        - xApp registration result
        - Service Model subscription result
        - Received E2 indication/message
        - Required screenshots or logs
---

#### LAB5: KPM service model Monitoring xApp using callbacks

- **Goal:**
    - In this lab, you will develop and run a monitoring xApp that connects to the Near-RT RIC and subscribes to the KPM Service Model to receive UE performance measurements through callbacks.

- **Ruquirement and Rule**
    - Rule:
        1. Please provide proof for each task using a screenshot or log.
        2. Verify that the xApp successfully connects to the Near-RT RIC and receives KPM measurements.
    - Ruquirement
        - xApp connection result
        - KPM subscription result
        - Received monitoring data
        - Explanation of the callback mechanism
        - Required screenshots or logs
---

#### LAB6: Building a KPM+RC xApp for RAN Slicing
- **Goal**
    - In this lab, you will build a KPM+RC xApp that monitors UE throughput using the KPM Service Model and dynamically adjusts RAN slicing resources through the RC Service Model.

- **Ruquirement and Rule**
    - Rule:
        1. Please provide proof for each task using a screenshot or log.
        2. Verify that the xApp can successfully receive UE throughput measurements and send RAN control requests.
    - Ruquirement
        - KPM subscription result
        - UE throughput measurements
        - RC control request and response
        - PRB allocation changes
        - Required screenshots or logs
---

#### LAB7: SLA rApp
- **Goal**
    - In this lab, you will use the BubbleRAN rApp SDK to create an SLA policy and send it to the Non-RT RIC through the R1 interface. The policy is then forwarded through A1 to the Near-RT RIC, where an xApp enforces the SLA on the RAN.

- **Ruquirement and Rule**
    - Rule:
        1. Please provide proof for each task using a screenshot or log.
        2. Verify that the xApp can successfully receive UE throughput measurements and send RAN control requests.
    - Ruquirement
        - KPM subscription result
        - UE throughput measurements
        - RC control request and response
        - PRB allocation changes
        - Required screenshots or logs
---

#### LAB8: Slicing rApp
- **Goal**
    - In this lab, you will develop and run a Slicing rApp that sends a slicing policy to the Non-RT RIC through the R1 interface. The policy is forwarded through A1 to the Near-RT RIC, where an xApp enforces the slice by limiting the maximum downlink PRB allocation.

- **Ruquirement and Rule**
    - Rule:
        1. Please provide proof for each task using a screenshot or log.
        2. Compare the UE throughput before and after applying the slicing policy.
    - Ruquirement
        - rApp execution result
        - Slicing policy configuration
        - UE throughput before slice enforcement
        - UE throughput after slice enforcement
        - Deployed slicing xApp status
        - Required screenshots or logs

---
## Key knowledge for Lab

| Lab                                 | Basic Knowledge to Teach Before the Lab                              | Students Should Understand                                                                                             |
| ----------------------------------- | -------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **LAB1 – UE–gNB Connectivity**      | 5G SA architecture, UE/gNB/5GC, RRC, NAS, NGAP, Wireshark basics     | How a UE goes from being disconnected to **RRC Connected**, and then completes **5G Registration**                     |
| **LAB2 – gNB TDD Traffic Analysis** | TDD, DL/UL slots, OFDM, SCS, PRB, iperf3                             | Why changing the DL/UL resource allocation can affect network throughput                                               |
| **LAB3 – O-RAN Basic**              | O-RAN architecture, CU/DU split, Near-RT RIC, xApp, E2 interface     | What O-RAN adds compared with a traditional 5G RAN, and where the CU, DU, RIC, and xApp are located                    |
| **LAB4 – O-RAN Advanced**           | xApp lifecycle, E2 Node, E2 Service Model, E2 Subscription procedure | How an xApp discovers an E2 Node, subscribes to RAN information, and receives E2 Indication messages                   |
| **LAB5 – KPM Monitoring xApp**      | E2SM-KPM, KPI/measurement, callback, asynchronous programming        | What is subscribed to in a KPM subscription, why callbacks are triggered, and what the received measurements represent |
| **LAB6 – KPM + RC xApp**            | E2SM-RC, RAN slicing, PRB, closed-loop control                       | How KPM is used for monitoring, RC is used for control, and how they form a **monitor → decide → control** loop        |
| **LAB7 – SLA rApp**                 | Non-RT RIC, rApp, R1, A1, policy, SLA                                | The difference between an rApp and an xApp, and how a policy from the Non-RT RIC can influence the Near-RT RIC         |
| **LAB8 – Slicing rApp**             | Network slicing, PRB allocation, A1 policy, SLA vs. slicing policy   | How an rApp defines slice resources through policies and how those policies can ultimately affect UE throughput        |


---
## Schedule
[Theory Lecture] ──> (Establishes Model)──> [Hands-on Sandbox Lab] ──(Captures Packets & Logs)──> [GitHub Documentation & Peer Critique]



| Week | Date    |                                                      Topic/Slide                                                      | Assignment  | Slide Link                                                                                                                                                                                                                 |
| ---- |:------- |:---------------------------------------------------------------------------------------------------------------------:| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1    | Sep. 9  |  **Opening**  |                | [Opening]()                                                            |
| 2    | Sep. 16  | **Area 6: Emerging O-RAN Paradigms & AI-RAN**<br>• Traditional RAN disaggregation (CU-DU-RU split).<br>• O-RAN Alliance principles: *Openness* & *Intelligence*.<br>• SMO, Non-RT RIC, Near-RT RIC, and 3 Control Loops.<br>• AI-RAN vision: Spectral efficiency via NVIDIA AI Aerial. |                              |                |                                                                                |
| 3    | Sep. 23 |  5G SA Network                                                                                                  |  Lab1              |                                                                                                                       |
| 4    | Sep. 30 |5G Network Data plane  | Lab2           |*Peer review check for Lab 1.*|
| 5    | Oct. 7 |**Area 7 & Area 1: RF, TRX & Wave Propagation**<br>• RF TRX Block Diagram: Modulation, filtering, channel coding.<br>• Wave propagation: Reflection, diffraction, scattering.<br>• Large-scale fading models: Path loss and shadowing. | |*Peer review check for Lab 2.* |
| 6    | Oct. 14  |**Area 1: Small-Scale Fading, mmWave & MIMO**<br>• Multipath delay spread vs. Coherence bandwidth.<br>• Doppler spread vs. Coherence time.<br>• mmWave attenuation, beamforming, and MIMO multiplexing. | |*(Review of mathematical path-loss calculations).* |
| 7    | Oct. 21 |   OAI building                                        | lab3               |                                                                                                           |
| 8    | Oct. 28 |  CU/DU spilt                                                                                                        |   lab4            |*Peer review check for Lab 3.* |                                                                                                                                                                                                                          |
| 9    | Nov. 4 | **Area 2: Multiple Access & OFDM Frames**<br>• Multiple access evolution: FDMA, TDMA, CDMA, OFDMA, SDMA.<br>• OFDM symbol mathematical model and Cyclic Prefix (CP) design.<br>• 5G NR frame structures, Subcarrier Spacing (SCS), and PRBs. | |*Peer review check for Lab 4.* | 
| 10   | Nov. 11  |  **Area 2: 5G NR User-Plane Protocols & Scheduling**<br>• DL User-Plane Protocol Stack: SDAP, PDCP, RLC, MAC.<br>• MAC scheduling, HARQ error correction, dynamic link adaptation.<br>• RRC state machine: Connected, Idle, and the new Inactive state. |
| 11   | Nov. 18 |                                          Monitor xApp                                             |    Lab 5            |  |
| 12   | Nov. 25 |                     Slice xApp                      |     Lab 6           |*Peer review check for Lab 5.* |       
| 13   | Dec. 2 | **Area 3 & Area 4: Core SBA & Security Frameworks**<br>• Core Network Evolution: Control/User Plane Separation (CUPS).<br>• 5GC Service-Based Architecture (SBA): AMF, SMF, UPF.<br>• FCAPS management framework.<br>• AAA security, EAP-802.1X, and CCMP (WPA2/AES) evolution. |  |*Peer review check for Lab 6.* |       
| 14   | Dec. 9  |                               SLA rApp                                | Lab 7               |                                                                                                                       |
| 15   | Dec. 16  |                              Slice rApp                               | Lab 8 | *Peer review check for Lab 7.* | 
| 16   | Dec. 23 | **Final In-Person Comprehensive Written Examination (30%)** | |*Peer review check for Lab 8.* | 

## Online Courses 
- [O-RAN course](https://drive.google.com/drive/folders/1b1LF2S6VQM1W9Om8Z5hxFxaqcZ-x_xVC)
- [Wireless Communications Onramp](https://matlabacademy.mathworks.com/details/wireless-communications-onramp/wireless)
- [Matlab Online Course](https://www.terasoft.com.tw/academia/Campuswidelicense/index.asp)
- [Matlab AI Course](https://www.terasoft.com.tw/academia/MATLAB_tutorials_AI_map.asp)


### Student Class Activity Records

Active students list:    
<font color=red>Template: </font>[Copy the template and create your own page on github](https://hackmd.io/@2xIzdkQiS9K3Pfrv6tVEtA/SJPZBxE5ex/edit)


| Name                           | Student ID | your own page Link                                        |
| ------------------------------ | ---------- | --------------------------------------------------------- |
| 謝秉祐                 | M11502203  | https://github.com/Karlyoo/WC-2026-M11502203-Karl/blob/main/template.md |
                
|||||


## Reference
::: success
#### Studying Note
- [Ian](https://onedrive.live.com/?cid=dab4e603c8a7479c&id=DAB4E603C8A7479C%2113185&authkey=%21AGX3xf%5FbDY8sgO8)

#### Basic Skills
- [5-Minute Presentation](https://www.thebalancesmb.com/mastering-the-art-of-the-5-minute-presentation-2951697)
- [How to Read a Paper]( https://web.stanford.edu/class/ee384m/Handouts/HowtoReadPaper.pdf)
- [Tricks to Read and Understand 3GPP Specifications](http://www.3glteinfo.com/tricks-to-read-and-understand-3gpp-specifications/)
- [How to Write a Report](https://www.openpolytechnic.ac.nz/current-students/study-tips-and-techniques/assignments/how-to-write-a-report/)
- [10 Tips for Better Teamwork](https://www.thebalancecareers.com/tips-for-better-teamwork-1919225)

#### Background: Simulator
- [MAC Layer](https://www.is-wireless.com/academy/simulation-software/lte-mac-lab/)
- [PHY Layer](https://www.is-wireless.com/academy/simulation-software/lte-phy-lab/)

#### Background: Knowledge for LTE
- [LTE](https://www.youtube.com/channel/UCf5srFJ-JofnE8r-bn1o1VA/videos)

#### Background: Knowledge for Open RAN**
- [5G Book: Understanding 5G](https://comms.viavisolutions.com/Understanding-5G-vi101673)
- [Fundamentals of mmWave communication](https://youtu.be/WOE_nKBKUsE?feature=shared) 
- [5G-era Mobile Network Cost Evolution](http://bit.ly/3595Swj)
- [Introduction to Open RAN](https://www.brighttalk.com/webcast/16515/359818/introduction-to-open-ran-informational-overview-of-open-ran-initiatives)
- [5G 101 Part 1](https://bit.ly/2sMuM7E)
- [5G 101 Part 2](https://bit.ly/390oDp3)
- [5G NR Logical Architecture and its Functional Split Options](https://bit.ly/2uDv5CW)
- Voice Over 5G – Evolution, Deployment, Technology and Testing Aspects ([Video](https://event.on24.com/wcc/r/2985778/BA6C29764E5F6FF1A58B34B3EDE2E03A?mode=login&email=crg@mail.ntust.edu.tw),[Slide](https://on24static.akamaized.net/event/29/85/77/8/rt/1/documents/resourceList1612344233266/rswebinarvonr202101271612344231934.pdf))
- [IEEE WCET Handbook](https://www.comsoc.org/media/6771/download).
- [Core Technology for 4G](https://www.slideshare.net/yousaf885/session3-kang)
- [5G Fundamentals: Functional Split Overview - Huber+Suhner](https://www.hubersuhner.com/en/documents-repository/technologies/pdf/fiber-optics-documents/5g-fundamentals-functional-split-overview)
![](https://i.imgur.com/JnniPK3.jpg)
- [SIP](https://www.onsip.com/voip-resources/voip-solutions/sip-call-flow-explained)
![](https://i.imgur.com/LmzFBUv.png)
#### Seminars/Workshops
- [Open RAN Global Forum](https://attendees.bizzabo.com/491978/agenda?date=1695081600000)

#### [Maximize Spectral Efficiency with AI-Native RAN and NVIDIA AI Aerial](https://developer.nvidia.com/blog/maximize-spectral-efficiency-with-ai-native-ran-and-nvidia-ai-aerial?ncid=so-nvsh-556337-vt26&es_id=f4f5ec5cd1)

:::

## [IEEE WCET Major Areas of Expertise](https://www.comsoc.org/media/6771/download)
#### Area  1  (11‐15%)  ‐ RF Engineering,  Propagation, Antennas, and Signal  Processing: Tasks and knowledge related to: antennas, RF engineering,  transmission, reception, propagation, channel modeling, and signal processing. 
:::spoiler Details
Evaluate  system  performance and  reliability;  calculate  path loss; evaluate  the effects  of  different  fading and empirical path loss models; calculate and evaluate the effects on the received signal of path‐related impairments;  determine  parameters  related  to  antennas  or  antenna  arrays;  generate  and  evaluate 
coverage and interference prediction maps; develop and analyze procedure to optimize the coverage of a radio; make RF system measurements. 
:::

#### Area  2  (19‐23%)  ‐  Wireless  Access  Technologies: 
Tasks  and  knowledge  related  to  wireless  access networks, especially the physical, MAC, and link layers. 
:::spoiler Details
Analyze  building  blocks,  multiple  access,  mobility  management,  and  spectrum implications  in  wireless access system design; analyze design considerations to optimize capacity/coverage; design and analyze a wireless  access  system; analyze  the  required  bandwidth  for  a wireless  system  and  tradeoffs;  analyze wireless access technology standards, their features, and evolution. 
:::

#### Area  3  (19‐23%)  ‐  Network  and  Service  Architecture:  
Tasks  and  knowledge  related  to  network infrastructure,  including  core  networks; service  frameworks  such  as  IMS;  and application  architectures such as voice, video streaming, and messaging. All‐IP services architecture as in 3GPP Rel 6 and beyond, 
including Enhanced Packet Services (EPS) as in 3GPP Rel 8 LTE (Long Term Evolution) and EPC (Enhanced Packet Core). 

:::spoiler Details
Analyze service  platforms,  IP  addressing  schemes  for  various  technologies;  design  and  test  quality  of service  (QoS); select and  test a load‐balancing scheme; analyze IP  routing and ad hoc  routing and mesh protocols; perform capacity planning, error  tracking, and  trace analysis; analyze  the evolution of mobile 
networks to enable IP multimedia. 
:::

#### Area  4  (19‐23%)  ‐  Network  Management  and  Security:  
Tasks  and  knowledge  related  to  fault, configuration, account,  performance, maintenance,  security management, management availability, and operation support systems (examples include network service assurance and provisioning). 

:::spoiler Details
Design  a  fault  monitoring  system  and  a  performance  monitoring  system;  develop/specify  types  and methods  of alarm  reporting;  compute availability and  reliability metrics; assess  the  potential impacts  of known security attacks; plan corresponding solutions to known security attacks. 
:::

#### Area 5 (8‐12%) ‐ Facilities Infrastructure, Standards and Regulations
Tasks and knowledge related to the specification,  design,  implementation,  and  operation  of  facilities  and  sites,  and  externally  imposed compliance requirements and conformance testing, including interoperability. 

:::spoiler Details
Determine  power  consumption;  analyze  electrical  protection  requirements  and  design  the  electrical protection  layout  for  a  wireless telecommunications  facility;  determine  the  required  antennas  for  the facility and  their  positions;  develop a  specification  for  the  required  structure  for a wireless  base  station facility;  determine  the  required  cable,  antennas,  and  materials  to  implement  an  in‐building  wireless network; evaluate equipment compliance with industry standards, codes, and site requirements. 

Assess service and equipment quality; prepare specifications  for purchasing services and equipment and evaluate  the  responses;  verify  compliance  with  regulatory  requirements;  select  and  analyze  frequency assignments;  perform  standardized  homologation  tests  as  required  by  regulatory  or  standardization 
bodies;  evaluate  compliance  with  health,  safety,  and  environmental  requirements;  perform conformance/interoperability  analyses  of  systems  and  components;  analyze  the  use  of  licensed  vs. unlicensed spectrum; obtain licenses and permits.
:::

#### Area  6  (11‐16%)  –  Emerging  New  Paradigms  and  Services 
Tasks  and  knowledge  related  to  ongoing 
developments  in  protocols  and  architectures  for  emerging  new  standards  in  wireless  (5G,  802.11)  and service requirements and application scenarios. 

:::spoiler Details
Analyze new network and service provisioning architectures (e.g. 5G); emerging standards in W‐WAN and W‐LAN  (especially  recent  developments  of  IEEE  802.11);  network  virtualization  and  slicing;  Internet  of Things  (IoT);  Machine  Type  Communications  (MTC);  evolution  of  the  Evolved  Packet  Core;  analyze  the evolution of wireless systems to support emerging applications.
:::


#### Area  7  (8‐12%)  ‐  Fundamental  Knowledge: 
Basic  knowledge  that  a  wireless  communications  engineer would use in order to perform tasks across all domains. 

:::spoiler Details
Apply basic concepts related to electrical engineering, communications systems, and general engineering management.
:::


### Area 1 — RF Engineering, Propagation, Antennas, and Signal Processing 
:::success
<font size=4>**Tasks:**</font>
**T1.01**  Calculate link budgets to evaluate system performance and reliability based on received signal level and fade margin (examples might include satellite, microwave link, base station to mobile station, wireless LAN and PAN); calculate path loss for various RF transmission systems (examples might include between isotropic or dipole reference antennas, base station to mobile station, base station to repeater, earth station to satellite, LOS/NLOS paths, and clutter losses). 

**T1.02**  Calculate the capacity of various multiple‐antenna schemes, and analyze the tradeoffs involved in selecting from among alternative schemes (calculations might include analysis of pre‐coding techniques). 

**T1.03** Evaluate the effects of different fading models (examples might include Rayleigh and lognormal) and empirical path loss models on the received signal strength in various signal propagation environments (examples might include flat terrain, rolling hills, urbanized areas, and indoor environments (such as buildings or tunnels) with losses caused by walls, ceilings, and other obstructions). 

**T1.04**  Calculate and evaluate the effects on the received signal of path‐related impairments, such as Fresnel Zone blockage, delay spread, and Doppler shift of a signal received by a moving receiver. 

**T1.05**  Calculate the polarization mismatch loss for various antenna systems (examples might include fixed microwave systems, cellular and mobile radio systems, and satellite systems). 

**T1.06**  Evaluate receive diversity gain for selection, equal gain, and maximal ratio diversity system configurations. 

**T1.07**  Determine parameters related to antennas or antenna arrays (examples might include pattern, beamwidth, gain, SAR‐reduction features, distance from an antenna or array at which far field conditions apply, spacing, beam forming, tilt, and sectorization) and analyze the effects of these parameters on coverage.

**T1.08** Determine appropriate antenna location at base station sites to prevent inter‐system and intra‐system interference effects, taking into account required radiation patterns and mutual coupling effects. 

**T1.09** Generate and evaluate coverage and interference prediction maps (examples might include maps for cellular, mobile radio, and WLAN systems). 

**T1.10** Develop and analyze a procedure to optimize the coverage of a radio system using propagation modeling and “drive test” measurements.

**T1.11** Develop a block diagram of an RF system (examples might include cellular, land mobile, and WLAN) employing standard modules (examples might include filters, couplers, circulators, and mixers) and/or using lumped or distributed matching networks, microstrips, and stripline. 

**T1.12** Make and analyze RF system measurements (examples might include swept return loss to determine antenna system performance, transmitter output power (peak or average, as appropriate), signal‐to‐noise ratio at a receiver front end, and co‐channel and adjacent‐channel interference for specific types of signal spectra). 

<font size=4>**Knowledge of:**</font>
**K1.01** different types of losses (examples might include transmission line loss, antenna gain, connector losses, and path loss)

**K1.02** procedures to calculate antenna gain and free space path loss

**K1.03** statistical fading models and distance‐power (path loss) relationships in different propagation environments

**K1.04** the effects of outdoor terrain and indoor structures such as walls, floors, and ceilings on signal propagation

**K1.05** common deterministic, statistical, and empirical propagation models (examples might include free space, Okumura, Longley‐Rice, and ray‐tracing) and software modeling tools (examples might include EDX Signal, ATDI, PathLoss, and similar radio network planning tools) used to implement them 

**K1.06** topographical maps and digital terrain databases

**K1.07** indoor and outdoor coverage calculation and verification techniques  

**K1.08** Es/N0, Eb/N0, RSSI, NF, and other system parameters 

**K1.09**  the relationship between receiver noise figure, noise temperature, and receiver sensitivity and the relationship between sensitivity under static conditions and the degradation of effective receiver sensitivity caused by signal fading in different propagation conditions 

**K1.10** external noise sources and their impact on the S/N ratios of received signals, and techniques for measuring the impact of external noise 

**K1.11**  basic antenna system design and use including antenna types (examples might include 
omnidirectional, panel, parabolic, dipole array, indoor antennas), antenna patterns, gain and EIRP, EIS, ERP, TIS, TRP, antenna size, antenna polarization, receive and transmit diversity, antenna correlation coefficients (examples might include MIMO antenna systems), and proper antenna installation to provide for coverage, interference mitigation, and frequency reuse 

**K1.12** adaptive antenna methods and techniques, including null‐steering, selection diversity, optimal‐ratio combining, adaptive antennas, spatial multiplexing, space‐time coding, and MIMO techniques

**K1.13** subscriber unit, mobile, and device antennas and their performance characteristics, including SAR‐reduction characteristics  

**K1.14** use of test equipment such as network analyzers, spectrum analyzers, and TDRs 

**K1.15** co‐channel and adjacent channel interference analysis and measurement methods and techniques; multi‐user detection and interference‐cancellation schemes and their limitations  

**K1.16** filters, power dividers, combiners, and directional couplers  

**K1.17** signal processing techniques, including matched filtering, adaptive filtering, adaptive equalization, and Rake processing 
:::

### Area 2 — Wireless Access Technologies 
:::success
<font size=4>**Tasks:**</font>
**T2.01** Analyze multiple access schemes for various technologies.

**T2.02** Analyze spectrum implications in wireless access system design (examples might include applications, TDD/FDD, inter‐modulation, LOS/NLOS, coverage/capacity). 

**T2.03** Analyze design considerations and perform system design to eliminate coverage holes and to optimize capacity/coverage in urban/indoor areas.

**T2.04** Design and analyze a wireless access system (examples might include AP placement and channel selection) according to given bandwidth requirements, coverage, and other considerations. 

**T2.05** Test devices with respect to interference issues in various operating environments (examples might include TDMA, CDMA, WCDMA, WLAN, 802.15). 

**T2.06** Perform interference analysis (examples: co‐site interference in TDMA, CDMA, WCDMA, WLAN, 802.15, and GSM; effect of interference on capacity in cellular, WLAN, WAN, ad hoc and sensor networks). 

**T2.07** Compute the required bandwidth for a wireless system given certain network conditions (examples might include BER, flow count, and protocols in use).

**T2.08** Analyze the tradeoffs (examples might include bandwidth versus BER) of various error detection and correction techniques. 

**T2.09** Analyze the tradeoffs and capacity implications of mitigation techniques for time‐varying channels, including channel estimation; time‐ and frequency‐recovery and tracking; modulation/demodulation; pre‐coding; and power control schemes (examples: scheduling algorithms, bandwidth versus power efficiency analysis).

**T2.10** Calculate frequency re‐use factor. 

**T2.11** Design fundamental elements/attributes of wireless network systems (examples might include cellular, 802.16, WLAN, and satellite). 

**T2.12** Analyze the steps involved in the process of handover/handoff for various wireless systems 
(examples might include UMTS, CDMA2000, 802.16, and WLAN).  

**T2.13** Analyze the tradeoff between the size of a paging area and the location update frequency.  
<font size=4>**Knowledge of:**</font>
**K2.01** multiple access and multiplexing schemes (examples might include TDMA, CDMA, OFDMA, FDMA, and SDMA) 

**K2.02** technology standards and their evolution (examples might include WCDMA, CDMA2000, LTE, 802.11, 802.15, and 802.16)  
K2.03 error detection and correction, ARQ, HARQ, Turbo Coding, link‐adaptation, modulation/ 
demodulation, and pre‐coding techniques  

**K2.04** objectives of channel‐estimation and power‐control schemes and their operation  

**K2.05** handover/handoff/mobility management, including inter‐technology handover/handoff 

**K2.06** paging functions  

**K2.07** the major components of a wireless network topology  

**K2.08** LEOS, MEOS and geostationary satellites, their bands, and their usage for broadcasting
:::

### Area 3 — Network and Service Architecture 
:::success
<font size=4>**Tasks:**</font>
**T3.01** Analyze service platforms including service enablers (examples might include messaging, positioning, and location), service creation/delivery (examples might include Open Service Access and Parlay), and service‐oriented architecture (SOA). Design and engineer various VAS (CRBT, SMS, VMS, Alerts, etc.) services on wireless network CORE. Design optimum network services for data traffic. 

**T3.02** Analyze IP addressing schemes for various technologies (examples might include Mobile IP, RObust Header Compression (ROHC) as in VoIP over HSPA or LTE, IPv4, and IPv6). 

**T3.03**  Design and test quality of service (QoS) (examples might include design and plan for adequate resources, selecting priority schemes, prioritization of differentiated services, queuing strategies, mapping of QoS classes between network and transport layers and call admission control) for VoIP and IMS‐based 
services. Calculate Capacity and Grade of Service (GOS) for a cellular network e.g., GSM/WCDMA/LTE networks. Provision QoS for differentapplications per 3GPP standards, e.g. through QCI, ARP, etc. for LTE/EPC networks. 

**T3.04** Select and test a load‐balancing scheme. 

**T3.05** Analyze IP routing (examples might include interpreting an IP routing table). 

**T3.06** Analyze ad hoc routing and mesh protocols, and suitability for various deployment scenarios. 

**T3.07** Perform capacity planning using traffic engineering principles.

**T3.08** Perform error tracking and trace analysis on protocol control messages for specific systems. 

**T3.09** Analyze the evolution of mobile networks to enable IP multimedia services (including circuit‐ 
switched to packet‐switched network evolution). 

**T3.10** Analyze intra‐ and inter‐domain roaming (examples might include roaming within a country or in different countries in 3GPP networks). Analyze service continuity across domains (e.g., VoIP in LTE and circuit‐switched voice in GSM/W‐CDMA networks).

**T3.11** Analyze the functioning of TCP/IP major transport protocols (examples might include TCP, UDP, and RTP) in the context of wireless communications and limitations of PING/Ack. 

**T3.12** Develop a simple block diagram‐level design for a network operations center (examples might include digital cellular, web‐based mobile content, multimedia broadcast, and SMS). 

<font size=4>**Knowledge of:**</font>
**K3.01** IMS (IP multimedia subsystems) and its architecture, including session control and switching plane; knowledge of different VAS in wireless domain 

**K3.02** VoIP/IP‐multimedia protocols 

**K3.03** wireless service enablers evolution, including call processing architecture/framework, feature development/enhancement, as well as applications such as presence, location, etc. policy rules, decisions, charging and enforcement 

**K3.04** location and positioning techniques 

**K3.05** load balancing principles in the context of wireless communications, and methods to avoid single point of failure through active/active or active standby, and concept of self organizing networks (SON) 

**K3.06** IP routing and mobile IP networking and addressing schemes including WLAN systems. IP evolution in wireless access ‐ backhaul and packet core connectivity 

**K3.07** error tracking and trace analysis techniques for dropped cells, access failures and other network related problem reports 

**K3.08** circuit switched and packet switched data and packet cellular networks and the differences between them; knowledge of various data capable technologies ‐ 1xRTT, EVDO, GPRS/EDGE, LTE 

**K3.09** roaming and roaming controls 

**K3.10** TCP/IP including transport protocols including WLAN systems 

**K3.11** Access Point Name and its functionality 

**K3.12** heterogeneous architecture for single‐hop and multi‐hop wireless networks
:::

### Area 4 — Network Management and Security
:::success
<font size=4>**Tasks:**</font>
**T4.01**  Design a fault monitoring system (examples might include using SNMP TRAP/NOTIFICATION, and 
using 2G OAM&P standards at Network Element Layer (NEL), Equipment Management Layer (EML), and 
Network Management Layer (NML)). 

**T4.02**  Design a performance monitoring system (examples might include using SNMP GET/SET and 
performance measurement on radio layer, BTS and RNC, usage and traffic analysis and accounting, 
monitoring SAACH frame error rate in 3GPP networks). 

**T4.03** Develop/specify types and methods of alarm reporting for an installation, and other OAM&P. 

**T4.04** Compute availability and reliability metrics from both the “network performance” and “system designer” perspectives (related to equipment failure). 

**T4.05**  Assess the potential impacts of known security attacks on wireless systems (examples might include virus, worm, DoS, network sniffing, flooding and impersonation; additional examples might include SIM/USIM card cloning, attempting bank transaction using prepaid cellular handsets, integrity of SMS, multi subscription of USIM card etc). 

**T4.06** Plan corresponding solutions to known security attacks (examples might include stolen SIM card, stolen PIN, use of different handsets using the same SIM card etc). 

**T4.07** Monitor, log, and audit security‐related data (including tasks such as streaming system logs to third party box for analysis and reporting). 

**T4.08** Analyze security vulnerabilities and prepare/recommend corrective actions; develop comprehensive test plan for network security testing. 

**T4.09** Design and plan a migration to a new network management scheme (including impacts on OSS, BSS, and billing); design proper access levels (user management) and its implementation. 

**T4.10** Analyze wireless accounting and billing schemes including inter‐operator accounting. 

**T4.11** Design and establish VPN communications from client to host. 

**T4.12** Design a secure system using state‐of‐the‐art solutions 

<font size=4>**Knowledge of:**</font>
**K4.01** quality of service (QoS) monitoring and control 

**K4.02** fault management 

**K4.03** configuration management including licensing mechanisms, feature addition/integration, system initialization and installation, policy‐based management, role‐base access control, level of security offered OTA by standard cellular and wireless systems, and architectures for service management 

**K4.04**  authentication, authorization, and accounting (AAA) principles and mechanisms and APN security; CAVE, A3/A8 and other authentication algorithms ‐ separating mobile from subscription data; cellular authentication schemes based on HLR, VLR, SIM card 

**K4.05** types of security attacks on wireless networks (examples might include use of stolen SIM card, fraudulent techniques to use handsets in non‐designated areas) 

**K4.06**  protocols to secure wireless networks (examples might include Application Security, Web security and Secure Socket Layer, VPN, RADIUS, DIAMETER, HLR/VLR and encryption methods based on cellular algorithms), and Self Organizing/Optimizing networks for next generation networks 

**K4.07** security‐violation events logging and monitoring, attempts towards billing fraud, SIM card manipulation and detection, etc. and different security testing tools 

**K4.08** security issue management and resolution (examples might include management of A‐key, OTAP 
and HLR/VLR updates, monitoring handoff and reauthentication during call) 

**K4.09**  network management protocols (examples might include simple network management protocol (SNMP), network scanning for BTS identification, interface measurements, data quality measurements, video quality measurements, verification of test mobile phones, acquisition of calibration data for planning tools) 

**K4.10** performance metrics pertinent to various access networks (examples might include Carrier to Interface (C/I) matrix; recommended changes to neighbor list to ensure appropriate cell handovers and others)

**K4.11** IP security, Encapsulation Security Payload (ESP), Internet Key Exchange, and digital signature; root authentication keys in removable UIM, Data Subscriber Authentication ‐ DSA over the air interface 

**K4.12** MIB, RMON, and Internet Control Messaging Protocol (ICMP) 

**K4.13**  intrusion detection systems, DDoS attacks, and traceback techniques; GSM security IMSI/TMSI, RAND, SRES‐HLR and AuC checking methods, network controlled policies, on‐line and off‐line charging for pre‐paid subscribers 

**K4.14** operational process models (examples might include ITIL and eTOM); writing A‐key into mobile − manual and over‐the‐air procedures 

**K4.15** hot billing during call, hot billing after call, and similar cases 

**K4.16** OTAP (Over the air provisioning methods), USIM (Universal SIM) card architecture, Kasumi security algorithm 

**K4.17** mobile money transaction methods, near‐field communications and security 

**K4.18** knowledge of state‐of‐the‐art network security solutions
:::

### Area 5 — Facilities Infrastructure, Standards and Regulations
:::success
<font size=4>**Tasks:**</font>
**T5.01** Determine the power consumption of a unit of communications equipment (examples might include tower amplifier modules, pressurization systems for waveguides).
**T5.02** Determine the power consumption for a facility containing communications equipment (examples might include base station amplifier racks, microwave system rack etc.).
**T5.03** Design a DC power plant to support the facility for a given required reserve time.
**T5.04** Analyze the electrical protection requirements (includes grounding/earthing, bonding, shielding, and
lightning protection) and design the electrical protection layout for a wireless telecommunications facility.
**T5.05** Design a wireless communication facility layout plan with considerations for heating, air conditioning, ventilation, and structural issues.
**T5.06** Determine the required antennas for the facility, including specification of the antenna system from RAN to Antenna. Identify and size common types of antenna, amplifiers, and cable for a given scenario.
**T5.07** Determine the required antenna positions on a structure (examples might include towers located in remote/extreme conditions such as mountain tops, arctic areas, etc.).
**T5.08** Design the waveguide/transmission line layout between the communications electronics and the antenna(s).
**T5.09** Coordinate with other users when implementing a communications system in a shared location.
**T5.10** Develop a specification for the required structure for a wireless base station facility based on the
required antenna sizes and elevations above ground.
**T5.11** Determine the required cable, antennas, distributed antenna systems, and materials to implement an in‐building wireless network.
**T5.12** Determine the required number of racks on which to mount the equipment and the rack layout and placement, taking into account the maintainability of the equipment.
**T5.13** Evaluate equipment compliance with industry standards, codes, and site requirements such as NEBS/ETSI specifications as well as ANSI, IEC, local/city regulations, right of way, and other applicable standards.
**T5.14** Design a site‐specific alarm and surveillance system.
**T5.15** Prepare specifications for purchasing services and equipment, and evaluate the responses, including relevant country‐specific standards (examples might include preparing request for proposals for introducing new services/licenses and evaluating submitted proposals for implementation of universal services projects).
**T5.16** Verify compliance with regulatory requirements (examples might include licensing, standards, rules, and regulations).
**T5.17** Select and analyze frequency assignments.
**T5.18** Evaluate compliance with health, safety, and environmental requirements.
**T5.19** Perform conformance/interoperability analyses of systems and components, including self organizing and self optimizing networks for NGN.
**T5.20** Analyze the use of licensed vs. unlicensed spectrum.
**T5.21** Obtain and draft licenses and permits where required, including software, hardware, product
licenses (open source, GNU, IP, patent laws).
**T5.22** Perform market analysis, study of market indicators, and pricing of telecom services.

<font size=4>**Knowledge of:**</font>
**K5.01** procedures to determine the power consumption of wireless communications equipment (examples might include satellite earth station facility, ship/small island based facility, etc.)
**K5.02** how to determine the power required to support a site (examples might include solar and wind based support for tower sites, considerations of bird nests, heated radome, etc.)
**K5.03** the application of AC and DC power systems (examples might include urban towers based on roof tops, tunnels and bridges)
**K5.04** the application of alternative energy sources to wireless communications facilities (examples might include use of solar, wind power, or bio‐mass in rural areas)
**K5.05** heating, ventilation, and air conditioning (HVAC) requirements
**K5.06** equipment racks, rack mounting spaces, and related hardware
**K5.07** electrical protection (including grounding/ earthing, bonding, shielding, and lightning protection)
**K5.08** basic waveguides and transmission lines (examples might include elliptical waveguides, multiple cables runs, pressurization and sealing of connectors, etc.)
**K5.09** tower specifications and standards (examples might include wind load calculation based on Effective Plate Area, alignment kits, and elevation angle measurements)
**K5.10** physical security requirements
**K5.11** alarm and surveillance systems
**K5.12** effects of environmental exposure (examples might include corrosion, temperature, and UV susceptibility)
**K5.13** NEBS/ETSI specifications as well as ANSI, IEC, and other applicable standards, codes, and other relevant site‐specific requirements
**K5.14** where to find expertise in structural engineering, fire suppression, and other building systems
**K5.15** regulatory requirements and telecom laws (examples might include international, national, and local); emerging standards and network evolution (examples might include convergence of networks, IMT‐ advanced); regulatory pillars (examples might include transparency, free competition) and mandates (examples might include consumer protection, universal service); international organizations and corresponding structure and functions (examples might include the role of ITU and its subdivisions)
**K5.16** spectrum licensing (examples might include leasing options, primary and secondary assignments in license)
**K5.17** spectrum characteristics, availability, and management including formal methods of measurements to report non‐compliance to regulatory bodies
**K5.18** local and site‐specific rules/codes (examples might include the National Electric Code in the US and analogous codes in other countries) and engineering regulations (examples might include when engineering work needs to be sealed by a Professional Engineer)
**K5.19** electrical and RF safety (examples might include UL, EC, CSA, and IEEE C.95)
**K5.20** frequency assignment databases and online tools (examples might include verification of registered
users in the area, experimental bands and their usages)
**K5.21** health, safety, and environmental issues (examples for RF safety might include SAR limits for different countries [e.g., American limits vs. European limits for accepted SAR‐values] and their different ways to measure it)
**K5.22** equipment type approval processes/requirements
**K5.23** how to identify and locate appropriate industry technical standards, applicable codes, and other
pertinent requirements
:::

### Area 6 — Emerging New Paradigms and Services
:::success
<font size=4>**Tasks:**</font>
**T6.1** Analyze new network and service provisioning architectures
**T6.2** Design, configuration and dimensioning of an 4G LTE and LTE‐A system: protocols and architecture
**T6.3** Understand the evolution of cellular networks towards 5G
**T6.4** Design solutions for network virtualization and slicing
**T6.5** Evolution of Wireless WAN and LAN standards: IEEE 802.11, IEEE 802.15, LoRA, etc.
**T6.6** Design of modern WLAN solutions (recent evolutions of IEEE 802.11 beyond ac/ad)
**T6.7** Understand the requirements and deployment scenarios of the Internet of Things (IoT)
**T6.8** Understand the requirements and deployment scenarios of Machine Type Communications (MTC)
**T6.9** Understand the requirements and deployment scenarios of Vehicle Communications (V2X)
**T6.10** Adapt solutions to the evolution of the Evolved Packet Core
**T6.11** Analyze the evolution of cellular wireless systems (RAN and core)
**T6.12** Analyze the evolution of wireless systems to support emerging applications

<font size=4>**Knowledge of:**</font>
**K6.1** Knowledge of 4G LTE and LTE‐A protocols and architecture
**K6.2** Knowledge of 5G New Radio standard
**K6.3** Knowledge of the 5G architecture, including network slicing and virtual network functions
**K6.4** Knowledge of application scenarios for wireless networks (IoT, MTC, V2X)
**K6.5** Knowledge of WiFi and its recent evolutions (IEEE 802.11b/a/g, to .11n/ac, to modern versions)
**K6.6** Knowledge of 5G RAN and EPC architectural components and protocols
:::

### Area 7 — Fundamental Knowledge
:::success
<font size=4>**Knowledge of:**</font>
#### Knowledge related to electrical engineering
**K7.1** fundamental AC/DC circuit analysis
**K7.2** mathematics including linear algebra, probability, statistics, and Boolean arithmetic
**K7.3** operation of complex test instruments, including oscilloscopes, spectrum analyzers, network analyzers, TDRs, and signal generators
**K7.4** frequency spectrum and Fourier transforms
**K7.5** basic printed circuit board design considerations
**K7.6** transmission theory and lines, antennas, and basic electromagnetic wave theory and applications
**K7.7** power calculations (examples might include dB, dBm, and dBx)
**K7.8** basic concepts of queuing theory and traffic analysis
**K7.9** basic signal processing (examples: analog and digital processing; quantization; linear filtering theory, concepts, and design)
**K7.10** basic concepts related to optical communications basic electronic system‐level block diagrams basic power supply design
#### Knowledge related to communication systems
**K7.13** basic communications and information theory (analog and digital)
**K7.14** basic telephony (including signaling, switching, and transmission)
**K7.15** noise impairments
**K7.16** basic EMI, EMC, and interference
**K7.17** frequency allocations and reuse
**K7.18** modulation techniques for analog (examples might include AM, FM, and PM)
**K7.19** modulation techniques for digital (examples might include FSK, PSK, and QAM)
**K7.20** wireless multiple‐access schemes (examples might include FDMA, TDMA, CDMA, and variants)
**K7.21** basic satellite communications
**K7.22** digital data transmission formats (examples might include E1/T1 and OC‐n/SDH)
**K7.23** basic components of RF circuitry
**K7.24** basic RF circuit design, including filter design
**K7.25** basic RF coupling, radiation, and antenna theory concepts
**K7.26** measurements for RF circuits and sub systems, such as output power, receiver sensitivity, noise figure, linearity performance, and spectral performance

#### Knowledge of general engineering management:
**K7.27** project management methods and processes 
**K7.28** fundamental engineering economics
**K7.29** design and configuration for ease of maintenance
**K7.30** documentation and configuration control schemes
**K7.31** IEEE Code of Ethics
:::
