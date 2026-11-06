# MPTCP vs MP-QUIC: A Comparative Study of Multipath Transport Protocols

**Course:** CS 331: Computer Networks  
**Team ID:** T007  
**Project ID:** CS331-T007-MPQUICvsMPTCP  

---

## Team Members

| Member Name | Roll Number | Focus Area |
| :--- | :--- | :--- |
| **Kaushal Rathi** | 24110290 | QUIC and MP-QUIC protocol mechanics (RFC 9000/9002, draft-ietf-quic-multipath-21) |
| **Krina Paghadar** | 24110169 | Multipath TCP architecture (RFC 8684, RFC 6824) and Linux upstream kernel analysis |
| **Pratik Kumar Dhakar** | 24110277 | Coupled congestion control theory (RFC 6356), fairness, and scheduling algorithms |
| **Swamini More** | 24110211 | Empirical literature synthesis (CoNEXT 2017, MultipathTester 2019) and application QoE |

---

## Overview

This project presents a comparative study of **Multipath TCP (MPTCP v1, RFC 8684)** and **Multipath QUIC (MP-QUIC, draft-ietf-quic-multipath-21)**. We analyze how both protocols leverage multihomed devices (e.g., simultaneous Wi-Fi and Cellular) to achieve bandwidth aggregation and seamless handover, comparing their architectural trade-offs, loss detection, congestion control, and application-layer Quality of Experience (QoE) for video streaming, file transfer, and VoIP.

---

## Repository Structure

```text
CS331-T007-MPTCP-vs-MPQUIC/
│
├── README.md                          # Repository overview and team details
│
├── report/
│   ├── CS331_T007_Report.pdf          # Final Project Report (PDF)
│   ├── CS331_T007_Report.docx         # Final Project Report (DOCX)
│   └── Final_Project_Report_Template_1.docx # Course report template
│
├── ppt/
│   └── CS331_T007_Presentation.pptx   # Presentation slides (PPTX)
│
└── AI_Used/
    ├── Kaushal_AI_usage.md            # AI usage log for Kaushal Rathi (24110290)
    ├── Krina_AI_usage.md              # AI usage log for Krina Paghadar (24110169)
    ├── Pratik_AI_Usage.md             # AI usage log for Pratik Kumar Dhakar (24110277)
    └── AI_Used_Swamini.md             # AI usage log for Swamini More (24110211)
```

---

## Key References

- **MPTCP v1:** RFC 8684 — *TCP Extensions for Multipath Operation with Multiple Addresses*
- **MP-QUIC:** draft-ietf-quic-multipath-21 — *Multipath Extension for QUIC*
- **Coupled Congestion Control:** RFC 6356 — *Coupled Congestion Control for MPTCP*
- **QUIC Core:** RFC 9000 & RFC 9002
- **CoNEXT 2017:** De Coninck & Bonaventure — *Multipath QUIC: Design and Evaluation*
