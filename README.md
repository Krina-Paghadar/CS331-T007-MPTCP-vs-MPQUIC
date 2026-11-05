# MPTCP vs MP-QUIC: A Comparative Study of Multipath Transport Protocols

**Course:** CS 331: Computer Networks  
**Team ID:** T007  
**Project ID:** CS331-T007-MPQUICvsMPTCP   

---

## 1. Team Members and Division of Responsibilities

| Member Name | Roll Number | Primary Responsibilities |
| :--- | :--- | :--- |
| **Kaushal Rathi** | 24110290 | QUIC and MP-QUIC protocol mechanics (RFC 9000/9002, draft-ietf-quic-multipath-21); lead architectural comparison; packet number space and loss recovery analysis. |
| **Krina Paghadar** | 24110169 | Multipath TCP architecture (RFC 8684, RFC 6824); subflow lifecycle and two-level sequence mapping; Linux upstream kernel status and historical adoption analysis. |
| **Pratik Kumar Dhakar** | 24110277 | Coupled congestion control theory (RFC 6356, LIA/OLIA/BALIA), fairness metrics, packet scheduling algorithms; testbed emulation methodology; end-to-end byte tracing. |
| **Swamini More** | 24110211 | Published empirical literature synthesis (CoNEXT 2017, MultipathTester 2019); application-layer implications (DASH/HLS video, VoIP, bulk transfer); synthesis of recommendations. |

---

## 2. Project Overview and Scope

Modern mobile and edge computing devices are increasingly multihomed, equipped simultaneously with multiple physical network interfaces such as Wi-Fi and 5G/LTE cellular. However, traditional transport protocols (standard single-path TCP and single-path QUIC) bind each transport connection strictly to a single network path (defined by an IP 4-tuple: source IP, source port, destination IP, destination port). If an active link fails or signal degrades, connection breakage or costly re-establishment is unavoidable.

This project delivers a comprehensive, rigorous comparative study between the two leading multipath transport solutions:
1. **Multipath TCP (MPTCP v1, RFC 8684)** — an in-kernel extension to TCP maintaining backwards compatibility via TCP options.
2. **Multipath QUIC (MP-QUIC, draft-ietf-quic-multipath-21)** — a modern, user-space, encrypted multipath extension layered over UDP.

### Strict Scope Definition: Theory and Literature Study Only
This project is an **in-depth theory, specification, and published literature study**. The team has performed a first-principles comparative deconstruction of the official specifications, RFCs, and published peer-reviewed empirical studies. **The team has not authored protocol software, configured active multipath kernels, or conducted live physical/emulated experiments.**

| What We Did | What We Did NOT Do |
| :--- | :--- |
| Studied RFC 8684 (MPTCP v1), RFC 6824 (v0), RFC 6356 (Coupled CC), RFC 9000/9002 (QUIC), and draft-ietf-quic-multipath-21. | Did **not** write or modify any transport protocol code. |
| Deconstructed protocol handshakes, sequence spaces, path management, and failure recovery from primary RFC/draft specifications. | Did **not** run an active physical or emulated testbed (no Mininet, NetEm, or iperf3 experiments conducted). |
| Analyzed the mathematical foundations of coupled congestion control (LIA, OLIA, BALIA) and packet scheduling (MinRTT, BLEST, redundant). | Did **not** collect live network measurements, packet captures, or empirical throughput/latency numbers. |
| Synthesized published empirical results from peer-reviewed literature (CoNEXT 2017, MultipathTester 2019, RFC 8041) under their original setups. | Did **not** generate synthetic benchmark plots or claim published figures as our own measurements. |
| Investigated real-world deployment bottlenecks: middlebox interference, UDP throttling, kernel vs. user-space deployment, and socket APIs. | Did **not** deploy production client/server multipath proxies or mobile endpoints. |

---

## 3. Primary Sources and Verified References

All analyses, comparisons, and claims in this repository and report are traced directly to primary IETF specifications and peer-reviewed literature:

### IETF Specifications and Standards Track Documents
1. **RFC 8684:** Ford, A., Raiciu, C., Handley, M., Bonaventure, O., & Paasch, C. (March 2020). *TCP Extensions for Multipath Operation with Multiple Addresses* (MPTCP v1).
2. **RFC 6824:** Ford, A., Raiciu, C., Handley, M., & Bonaventure, O. (January 2013). *TCP Extensions for Multipath Operation with Multiple Addresses* (MPTCP v0, Obsoleted by RFC 8684).
3. **RFC 6356:** Raiciu, C., Handley, M., & Wischik, D. (October 2011). *Coupled Congestion Control for MPTCP*.
4. **RFC 6182:** Ford, A., Raiciu, C., Handley, M., & Barre, S. (March 2011). *Architectural Guidelines for Multipath TCP Development*.
5. **RFC 9000:** Iyengar, J., & Thomson, M. (May 2021). *QUIC: A UDP-Based Multiplexed and Secure Transport*.
6. **RFC 9002:** Iyengar, J., & Swett, I. (May 2021). *QUIC Loss Detection and Congestion Control*.
7. **draft-ietf-quic-multipath-21:** Liu, Y., Ma, Y., De Coninck, Q., Bonaventure, O., Huitema, C., & Piraux, M. (17 March 2026). *Multipath Extension for QUIC* (IETF Working Group Draft).
8. **RFC 8041:** Bonaventure, O., Paasch, C., & Froentjes, G. (February 2017). *Use Cases and Operational Experience with Multipath TCP*.

### Peer-Reviewed Publications and Empirical Studies
9. **CoNEXT 2017:** De Coninck, Q., & Bonaventure, O. (December 2017). *Multipath QUIC: Design and Evaluation*. In *Proceedings of the 13th International Conference on emerging Networking EXperiments and Technologies* (CoNEXT '17), pp. 160–166.
10. **MultipathTester (MNM 2019):** De Coninck, Q., & Bonaventure, O. (April 2019). *MultipathTester: Comparing MPTCP and MPQUIC in Mobile Environments*. In *IEEE/IFIP Network Operations and Management Symposium (NOMS)*.
11. **IMC 2011 (Middleboxes):** Honda, M., Nishida, Y., Raiciu, C., Greenhalgh, A., Handley, M., & Tokuda, H. (November 2011). *Is It Still Possible to Extend TCP?*. In *ACM Internet Measurement Conference (IMC)*.
12. **NSDI 2012:** Raiciu, C., Paasch, C., Barre, S., Ford, A., Honda, M., Duchene, F., Bonaventure, O., & Handley, M. (April 2012). *How Hard Can It Be? Designing and Implementing a Deployable Multipath TCP*. In *USENIX NSDI*.
13. **Scheduler Study (Paasch 2014):** Paasch, C., Ferlin, S., Alay, O., & Bonaventure, O. (November 2014). *Experimental evaluation of multipath TCP schedulers*. In *ACM CSWS*.
14. **Internet Adoption Scan (2021):** From Single Lane to Highways: Analyzing the Adoption of Multipath TCP in the Internet (arXiv:2106.07351).

---

## 4. Repository Structure

```text
CS331-T007-MPTCP-vs-MPQUIC/
│
├── README.md                          # Repository overview, team roles, scope boundaries, and primary sources
├── mptcp-mpquic-understanding-plan.md  # Complete 323-question foundational study roadmap and question bank
├── mptcp-mpquic-plan-condensed.md     # Condensed 4-session execution plan and cross-training matrix
│
├── code/
│   └── README.md                      # Transparent statement explaining absence of code and environment blockers
│
├── report/
│   ├── CS331_T007_Report.docx         # Technical Report matching template specifications
│   ├── CS331_T007_Report.pdf          # Final Technical Report PDF
│   └── Final_Project_Report_Template_1.docx # Reference course template
│
├── ppt/
│   ├── CS331_T007_Presentation.pptx   # 12-slide technical presentation with comprehensive speaker notes
│   └── CS331_T007_Presentation.pdf    # Presentation exported to PDF format
│
└── AI_Used/
    └── README.md                      # Index table tracking generative AI assistance and prompt log references
```

---

## 5. Summary of Key Findings

1. **Architectural Trade-offs:** MPTCP v1 maintains backwards compatibility with existing legacy socket applications at the cost of strict 40-byte TCP option limits, vulnerability to middlebox tampering (stripping unknown options or mangling sequence numbers), and OS kernel coupling. In contrast, MP-QUIC operates in user space over UDP with encrypted packet headers, eliminating middlebox interference and allowing agile protocol deployment, at the cost of higher per-packet CPU overhead and firewall UDP drop policies.
2. **Head-of-Line (HOL) Blocking:** MPTCP enforces a single, ordered byte stream across all subflows via connection-level Data Sequence Numbers (DSN), meaning packet loss or high jitter on one subflow blocks application delivery across all subflows. MP-QUIC decouples transport streams, restricting HOL blocking to within individual streams, though single-stream transfers remain vulnerable to path delay divergence.
3. **Loss Detection and Retransmission:** MPTCP relies on per-subflow TCP sequence numbers and duplicate ACKs/RTOs. MP-QUIC (draft-21) mandates dedicated, monotonically increasing packet number spaces per path, eliminating retransmission ambiguity and preventing RTT miscalculation when returning `PATH_ACK` frames over alternate subflows.
4. **Adoption Realities:** MPTCP upstreaming into the Linux kernel (kernel 5.6+) has improved availability, yet widespread public Internet adoption remains low (<0.1% of top web servers) due to enterprise middleboxes, lack of client-side multi-homing support in public APIs, and mobile OS policies reserving multipath for closed system services (e.g., Apple Siri, Apple Music). MP-QUIC remains actively progressing through the IETF standards track (draft-ietf-quic-multipath-21), with production deployments awaiting finalized RFC status and operating system socket standardization.

