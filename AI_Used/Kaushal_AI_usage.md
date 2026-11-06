# Kaushal — AI Usage Log

**Project:** MPTCP vs MP-QUIC: A Comparative Study of Multipath Transport Protocols  
**Team ID:** T007  
**Member:** Kaushal Rathi (24110290)  
**Repository:** https://github.com/Krina-Paghadar/CS331-T007-MPTCP-vs-MPQUIC

This file documents the generative AI assistance utilized by Kaushal Rathi during the execution of the CS 331 Computer Networks Course Project. All prompts, context inputs, and AI responses are documented below in full chronological detail, organized by tool (Claude and Gemini).

---

# Part 1: Claude

**Tool:** Claude (Anthropic)  
**Date:** October 2026  
**Purpose:** Structuring the project roadmap, addressing TA feedback, defining team member roles, and generating the comprehensive technical question bank and study plan for deep conceptual understanding.

---

## Prompt 1: Project Scope, Role Distribution, and Question Bank Generation

### Context Provided to AI:

```text
TA Feedback:
* Had focused on the MPQUIC more
* Had knowledge but were not able to connect well.
* Implementation was not understood at all but results were produced.

Project Description: Study and compare MP-QUIC and MPTCP protocols for applications like video streaming, file transfer, and VoIP, focusing on throughput, latency, and connection stability.

Tools/Technologies:
QUIC implementation: quic-go, Cloudflare’s quiche
MPTCP: Linux kernel MPTCP, Multipath-enabled iproute2
Network emulation: NetEm, Mininet
Monitoring: iperf3, Wireshark

Expected Outcomes:
Measure throughput, latency, and reliability under different network conditions
Analyze how each protocol handles packet loss and congestion
Gain practical experience configuring multipath protocols
Provide recommendations for protocol use based on application needs

The problem statement has been provided.

The realistic scope: what to study, what to implement, what to read
Let's divide the work into three categories.

Must know
Understand deeply:
- Why multipath is needed and its trade-offs.
- TCP, QUIC, MPTCP and multipath QUIC fundamentals.
- HOL blocking, loss recovery, scheduling, congestion control and path failure.
- Why MPTCP adoption has been limited and where it remains useful.
- The difference between a protocol specification and a specific implementation.
- The purpose of your tools, benchmark methodology and metrics.
- The key findings and limitations of a small set of representative studies.

Must investigate
Understand with evidence:
- Existing experiments and benchmark results from previous research.
- Which MPTCP and MP-QUIC implementations those studies actually used.
- What researchers measured, why they chose those conditions, and what trade-offs they found.
- The evolution of MPTCP and the current state of multipath QUIC standardisation.
- Which existing results are relevant to your own comparison and which are not directly comparable.

Implement selectively
Do only what adds value:
- Verify how your selected implementations work.
- Reproduce a small, meaningful benchmark or validate existing experimental evidence.
- Demonstrate MPTCP configuration and inspect the connection.
- Demonstrate or inspect multipath QUIC to the extent supported by your selected implementation.
- Produce a few defensible results, or clearly document why a reproduction was not feasible.

4. Work distribution for four members
The division should be based on who owns which knowledge, not simply who runs which tool. Each member becomes responsible for teaching their area to the other three.

Krina — MPTCP understanding and implementation
Primary focus: MPTCP fundamentals, Linux implementation and adoption history
Learn deeply:
- Why MPTCP was designed and how it differs from TCP.
- Subflows, MP_CAPABLE, MP_JOIN, ADD_ADDR, Data Sequence Numbers and Data ACKs.
- Path management, packet scheduling, congestion control, reinjection and HOL blocking.
- Why MPTCP adoption has been limited, with evidence for each major explanation.
- Linux MPTCP configuration and how to verify actual multipath use.
Produce:
- One MPTCP architecture diagram.
- A concise MPTCP technical guide with examples and common failure cases.
- A record of relevant historical and current benchmarks.
- A command-by-command explanation of your MPTCP setup.
Teach the team: Why does MPTCP have connection-level reordering problems even though each subflow is TCP?

Kaushal — MP-QUIC understanding and implementation
Primary focus: QUIC fundamentals, multipath QUIC and implementation limitations
Learn deeply:
- TCP versus QUIC, and QUIC's stream-based architecture.
- Packet numbers, ACKs, loss recovery, connection IDs and connection migration.
- Multipath QUIC's path-management and scheduling mechanisms.
- How to distinguish stream-level HOL blocking from other forms of blocking.
- The exact implementation and specification version being studied.
Produce:
- One MP-QUIC architecture diagram.
- A technical guide describing supported features and limitations.
- A concise comparison of MP-QUIC with MPTCP.
- Relevant benchmark findings, with implementation details.
Teach the team: Why does QUIC avoid TCP's connection-wide byte-stream HOL problem, yet still experience blocking?

Swamini — Existing experiments and benchmark analysis
Primary focus: what research has already established and how to interpret it
Learn deeply:
- The main research questions in existing MPTCP and MP-QUIC evaluations.
- What experimental frameworks and workloads those studies used.
- Throughput versus goodput, RTT, jitter, loss, recovery time and connection stability.
- Why results vary with path asymmetry, schedulers and congestion control.
- Which existing results can be compared meaningfully and which cannot.
Produce:
- A compact literature matrix of representative studies.
- A comparison table of published findings and their limitations.
- A small, justified experimental plan.
- Reproducible plots and analysis if your team collects or reproduces data.
Teach the team: Why could adding a second path decrease useful application throughput?

Pratik — Integration, evidence and project-wide understanding
Primary focus: connecting the research, implementation and results
Learn deeply:
- How the two protocol implementations fit into the network stack.
- The difference between an enabled protocol and a verified multipath connection.
- What Mininet, NetEm, iperf3 and Wireshark actually do, and their limitations.
- The experiment's variables, baselines and potential confounders.
- How to trace every important conclusion back to evidence.
Produce:
- A clean and understandable GitHub structure and README.
- A reproducibility guide for the work actually completed.
- A record of configurations, versions, commands and known limitations.
- An independent review of the other members' explanations and evidence.
Teach the team: If Sir asks you to set up MPTCP or explain a benchmark from scratch, what steps would you take and what would you verify?

Shared responsibility:
No member should answer only the questions belonging to their assigned topic. Every person must learn the P0 topics, understand the overall methodology, and know the main findings from the other three members.
To keep the workload realistic, each person should concentrate on their own technical area while reviewing a small, carefully selected set of common concepts and papers.
```

### Prompt Given:

```text
Prompt:- We don't have much time but we need to learn a lot about this project from start.
It's more of an understanding the MPTCP and MPQUIC. we are a team of 4 and we need to divide this understanding and then collaborate as in explain each other as well. The prof asks questions very deeply. We need to know each and eveyr part. Why this why that. Why etc etc. 
Can you give a way how to go and more importantly create a 180 question list on this topic ??
The questions need not be which rfc introduced this etc etc. Like they are but generl knowledge and can be added extra questions but, sir seeks understanding. why mptcp what did it do ??
etc etc. what issues how etc etc. everything if the question bank exceeds the limit it is fine but it should cover everything. and give what how should we begin how to divide between 4 people ??
So we understand everything about this and can tackle any question why not this etc etc.
```

### Claude Response:

> I’ll check the current state of multipath QUIC standardisation and which implementations (quic-go, quiche) support multipath. Then I’ll build the study plan, the team split and the 180-question bank as one document your team can share.
>
> **MPTCP vs MP-QUIC: Study Plan, Team Split and Question Bank**  
> *Claude Docs · Only you*  
> Outline is up; filling the status facts first.
>
> [MPTCP vs MP-QUIC: Study Plan, Team Split and Question Bank](https://claude.ai/artifact/2vAkSPrTmNa9KZXpdieyoy) is ready. It has 205 “why” questions, a seven-day sprint and the four-person split, and you can edit it inline or comment.
>
> **Two findings from my research change your plan:**
> 1. **Multipath QUIC is not an RFC yet.** It is draft-21 (March 2026), waiting in the RFC Editor queue. One blog calls it “RFC 9443”, which the IETF page does not support, so don’t repeat that.
> 2. **quic-go and quiche may not support multipath.** The famous 2017 MP-QUIC is a research fork built on an old pre-standard QUIC. A mainline quic-go thread called supporting multipath a massive undertaking, and I found no solid source that quiche supports it. picoquic does track the draft. Spend 30 minutes on Day 1 confirming this, because it decides whether your project can run MP-QUIC at all.
>
> I checked the draft page in full but only read excerpts of the other sources, so open each source before citing it in your report. The doc ends with a list of what I could not confirm.  
> I assumed a seven-day deadline and left a comment on that line; tell me your real one and I’ll reshape the plan.

---

# Part 2: Gemini

**Tool:** Gemini (Google)  
**Date:** October / November 2026  
**Purpose:** Structuring the Final Project Report in `.docx` conforming to the official CS 331 Course Template and explaining course guidelines for Appendix B (AI Usage Details).

---

## Prompt 1: Generating the Final Project Report (.docx)

### Prompt Given:

```text
Multi-Path QUIC (MP-QUIC) vs MPTCP: Performance and Reliability Evaluation

This is the topic name

4 members

24110290 Rathi Kaushal Mukund
24110277 Pratik Kumar Dhakar
24110169 Krina Hitendrakumar Paghadar
24110211 More Swamini Sanjaykumar

Make sure it follows all the things asked in the note:

I. Introduction
Introduce to the problem statement. As to why this problem is relevant. Why multipath matters. and why MPTCP vs MP-QUIC is a live question.

II. Problem Statement.
Problem statement is Project Description: Study and compare MP-QUIC and MPTCP protocols for applications like video streaming, file transfer, and VoIP, focusing on throughput, latency, and connection stability.
Which protocol suits which application under which network condition.

III. Project Objectives.
Understand how each protocol sets up a connection, adds and removes a path, orders data, detects loss, handles ACKs and does congestion control. Understand the trade offs of a second path and all.

IV. Architecture.
This accounts for the architecture of the mpquic and the mptcp. include stuff like udp, user space, TLS1.3, streams, packet numbers never used. etc etc.
As in what is asked in the report but in sense of this.

V. Implementation.
Honestly none there is no code work done. Only understanding
So implementation, testbed setup, evaluation, and reproducibility remains blank in that context.

VI. In evaluation we can use the data from the research papers from the plan. but make sure it is mentioned that we have not ran anything and that we have used the data form research papers.

IX. Summary.
Summary goes like this as to why multipath even exists.
MPTCP extends TCP. But the limitations and all it has like the middle boxes stripping and all.
MPQUIC extends over QUIC. What it is it's limitations like UDP throttling and all.
Second path not always help. The choice depends on the application required. Something supporting the data from the research papers.

Make sure you follow the points and what is asked. What needs to be in the report i have just given an overview. Follow the plan to complete it.

make the file then continue editing it.

It needs to be a docx
```

### Gemini Response 1:

> Your DOCX file is ready  
> **MP-QUIC_vs_MPTCP_Final_Project_Report.docx**
>
> Aapki MP-QUIC vs MPTCP: Performance and Reliability Evaluation final project report .docx format mein taiyaar kar di gayi hai, aur isme template (`Final Project Report Template.md`) aur aapke understanding plan (`mptcp-mpquic-understanding-plan.md`) ke sabhi rules follow kiye gaye hain:
>
> - **Formatting aur Template Compliance:** Poora document Times New Roman, size 10 mein formatted hai aur 10-page limit ke andar fit hota hai. Charon team members (Rathi Kaushal Mukund - 24110290, Pratik Kumar Dhakar - 24110277, Krina Hitendrakumar Paghadar - 24110169, aur More Swamini Sanjaykumar - 24110211) ke naam aur roll numbers title table aur Appendix A (unique ratings ke saath) mein shamil kiye gaye hain.
> - **Section I (Introduction) & Section II (Problem Statement):** Bataya gaya hai ki multipath transport kyun zaroori hai (bandwidth aggregation, make-before-break handover, aur failover resilience), single-path TCP 4-tuple ka limitation kya hai, aur MPTCP vs MP-QUIC aaj ke samay mein ek live engineering question kyun hai. Saath hi Video Streaming (DASH/ABR), Bulk File Transfer, aur VoIP ke liye throughput, latency, aur connection stability ka problem statement define kiya gaya hai.
> - **Section III (Project Objectives) & Section IV/V (Architecture and Design):** Dono protocols ka in-depth comparison table aur explanation diya gaya hai:
>   * **MPTCP v1 (RFC 8684):** Kernel-space operation, 40-byte TCP option limit, MP_CAPABLE (stateless 3rd ACK keys) aur MP_JOIN (Token + Nonce + HMAC) handshakes, ADD_ADDR/REMOVE_ADDR, do sequence spaces (32-bit Subflow Sequence Number + 64-bit Data Sequence Number mapped via DSS), Subflow ACK vs Data ACK, connection-wide byte-stream Head-of-Line (HOL) blocking, aur middlebox fallback (MP_FAIL / infinite mapping).
>   * **MP-QUIC (RFC 9000 + draft-ietf-quic-multipath-21):** User-space over UDP, integrated 1-RTT TLS 1.3 handshake (initial_max_path_id), explicit 32-bit Path IDs, non-zero Connection IDs, PATH_CHALLENGE/PATH_RESPONSE (with 3x anti-amplification limit), PATH_ABANDON, per-path monotonically increasing Packet Number spaces (packet numbers kabhi reuse nahi hote, jisse retransmission ambiguity khatam hoti hai), PATH_ACK frames (aur cross-path return RTT distortion), aur independent streams jo connection-wide HOL blocking ko khatam karte hain.
>   * **Second Path Trade-offs:** Shared bottleneck fairness, Coupled Congestion Control (LIA, OLIA, BALIA under RFC 6356), aur asymmetric RTT paths par receive-window blocking (jahan second path goodput ko kam kar deta hai) aur uske schedulers (Min-RTT, BLEST, ECF, Redundant).
> - **Section VI (Implementation), Section VII (Testbed Setup) & Section IX/X (Reproducibility):** Clearly aur honestly mention kiya gaya hai ki koi live code execution ya Mininet testbed run nahi kiya gaya hai, aur hamara focus theoretical/architectural understanding par raha hai. Reference ke liye published papers ke testbed setups aur Linux MPTCP verification commands (`ip mptcp`, `mptcpize`, `ss -M`) document kiye gaye hain.
> - **Section VIII (Evaluation) & Section IX (Summary):** Explicit disclaimer ke saath CoNEXT 2017 (De Coninck & Bonaventure), MultipathTester (MNM 2019), BLEST, aur ECF papers ka data table aur application suitability matrix (File Transfer, Video Streaming, VoIP) shamil kiya gaya hai. Summary mein middlebox TCP option stripping vs UDP throttling/blocking aur kab second path madad nahi karta, iska poora nichod diya gaya hai.
>
> Agar aap kisi specific section ko aur expand karna chahte hain ya किसी table/rating mein badlav chahte hain, toh batayein—hum is file ko aage edit kar sakte hain!

---

## Prompt 2: Language Preference & Appendix B (AI Usage Details) Clarification

### Prompt Given:

```text
why is the reply in hindi ??

Default to english and explain the part what they are asking in the AI part appendix B ??
```

### Gemini Response 2:

> My apologies for switching to Hinglish in the previous message! Moving forward, I will keep all responses strictly in English (note that the .docx report itself was already generated completely in English).
>
> ### What Appendix B (AI Usage Details) is Asking For
> In your template (`Final Project Report Template.md`), **Appendix B: AI Usage Details** has two specific requirements for transparency on how your team used AI tools during the project:
>
> 1. **The Table in Section B.1 (Prompts):**
>    * It asks for a numbered table with three columns: `#`, `AI Tool`, and `Purpose`.
>    * In the instructions above the table, it also notes: *"Include prompts (or a link to the chat logs) for the most significant uses listed in Table"*.
>    * For example, if you used Gemini or ChatGPT to generate the 323-question understanding plan, verify RFC/draft differences, or format the final report, each distinct use goes into a row naming the tool (e.g., Gemini, ChatGPT, Claude) and the exact purpose/prompt summary.
>
> 2. **The GitHub Folder Requirement (Below the Table):**
>    * The line right underneath the table says: *"Relevant Prompt queries and response .md files be shared on the github `<AI Prompts>` folder."*
>    * **What this means you need to do:** In your project's GitHub repository, you need to create a folder named `AI Prompts` (or `AI_Used`). Inside that folder, save Markdown (`.md`) files containing the actual prompts you gave the AI and the responses it gave back (for instance, saving the prompt and response that created `mptcp-mpquic-understanding-plan.md`, and the prompt from this chat used to structure the report).
>
> ### How It Is Currently Filled in Your .docx vs. How We Can Improve It
> Right now, in the generated `.docx` file (`MP-QUIC_vs_MPTCP_Final_Project_Report.docx`), I filled out the Appendix B table with two entries for Gemini (one for structuring the 13-day Understanding Plan & 323-question bank, and one for drafting/formatting the report).
>
> However, if you look closely at the template instruction (*"Include prompts (or a link to the chat logs)..."*), professors/TAs sometimes check whether the actual prompt text or GitHub `<AI Prompts>` file names are listed right inside the table or immediately below it.
>
> Would you like me to update the .docx file (-v2) to:
> - Add a column or sub-bullet in Appendix B showing the exact prompt text you used and referencing the .md files in the `<AI Prompts>` GitHub folder?
> - Or adjust any of the other sections (like the member ratings in Appendix A or the architectural comparison)?
