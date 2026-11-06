AI Used for the Project: MPTCP vs MP-QUIC
Student Name: Swamini More
Roll Number: 24110211
Course: Computer Networks
Project Title: MPTCP vs MP-QUIC: Performance and Reliability Evaluation

## Prompt:
10/24/2026, 11:46:10 AM

these are the plan for the project of mptcp and mpquic we have as part of our Computer networks course. explain me in detail the plan in simple and my role and what all i have to do

[Attachment: mptcp-mpquic-understanding-plan.md]

[Attachment: mptcp-mpquic-plan-condensed.md]

## Response:
10/24/2026, 11:45:18 AM · gpt-6

> **Scheduling Four Sessions and Exact Reading**
>
> 
>
> Worked for 26s

# MPTCP vs MP-QUIC project - complete explanation of your plan and your role

I've gone through both plans. The main thing to understand is that **your team is preparing to understand, compare, and defend two networking protocols in a viva**, not simply to implement a program and show that it runs.

Your individual responsibility is to understand the research evidence, explain why multipath networking can sometimes perform worse instead of better, and connect those findings to practical applications such as video streaming and voice calls.

I'll explain the project from the basics first, then break down exactly what you have to do.

## 1\. What is this project about?

Imagine your laptop or phone has two ways to access the internet\:

[![Ağ Kurulumu Temelleri: Başlangıç Rehberi - İstanbul Teknoloji Blog | Ethernet.com.tr](https://images.openai.com/static-rsc-4/kNUb2kPzNxOLTTP4MvdIiUTWNsgCcA14aWXEEqNPtPWfrgt83ryL0kzXjnXznV9DUF7e4gx2kJzagVr4m0fuKLGEpsvWdOKiw3gFk0qBvRaAPMtK6gB02aRqQtdlGSV-iItg7hljGC3Ya35IwQgAYmL-eAflTU02rQyEfH4PAOpCXTmb_CVh-nxOLJ8-hlh0?purpose=fullsize)](https://ethernet.com.tr/blog/ag-kurulumu-temelleri-baslangic-rehberi/)

**Path 1: Wi-Fi**

Fast, perhaps 100 Mbps, but with variable delay

[![Transmission Cellular Tower Antenna Landscape](https://images.openai.com/static-rsc-4/PVNw_Y2kPni3R9Y029_CSk37nrEWE07Hznj2c2LHHwTWJOkYsB6uJRReOH5Qa61N8IMO3EgwzJv3OxrWRR6y5pRvDd2OWo3_aGph0Ce-mSmrjcj4MaLflzuvfOPG4H8MIVWQiUxf02fm-_mlh1Unhp2QuVrH-PpyKWlA0lgKqr2AbhtLIZnxDDyyHnkvqxOh?purpose=fullsize)](https://media.gettyimages.com/id/1324035452/vector/transmission-cellular-tower-antenna-landscape.jpg?b=1&c=iGcsXzwfUGTDecVSS_dcMTo5lYlNBvl1E2Ok33d255w%3D&k=20&s=612x612&w=0)

**Path 2: Mobile data**

Perhaps 40 Mbps, with a different delay and reliability

---

**Multipath transport**

Tries to use multiple network paths for one logical connection.

Ordinarily, a connection uses one path. If that path becomes slow or fails, the connection can suffer even if another usable path exists.

A *multipath transport protocol* tries to solve this by allowing one logical connection to use multiple network paths.

There are three main goals\:

- **Aggregation\:** use multiple paths to improve the amount of useful data delivered.
- **Failover\:** continue sending data through another path if one fails.
- **Handover\:** transition between paths, for example, when a phone moves from Wi-Fi to cellular data.

Your project compares two approaches.

[![4.1 Models of Computation - Introduction to Computer Science | OpenStax](https://images.openai.com/static-rsc-4/N92aMnOx6VC70AUcxEe-MJGYhu525lhSoHtfbLqZ0zmqzUJvD1AU12pknDiBXhs8l4kV92VasX9gYxeXEtPMS7F0Nauzm31lag1_EWDw7Eetd_3fbdbqLMKBZdc8cZSbJ-EARLicDugE6-dbbgXcTIT2K1h_hilojbJYn7AX7YlZGLAMQxU6nAvrVF9taxz3?purpose=fullsize)](https://openstax.org/books/introduction-computer-science/pages/4-1-models-of-computation)

**MPTCP - Multipath TCP**

It extends TCP so that one logical connection can contain multiple TCP sub-connections, called *subflows*\. It aims to retain compatibility with applications that use TCP.

---

[![What Is HTTP/3 and How Does It Differ from HTTP/2? | Gcore](https://images.openai.com/static-rsc-4/GsHESmlCVBT_r9G1QSbJsPm_viQp3RCGmcTNwVAOXPbl5PahuzzYtKg8uQPCYWm8vBJts505YUKcoUAR679MfvxCektoZzzZxEPdc0We16ojF31m9xF46jT67sPEKuniwq7fJHErEQ7ow1U0M7tFtcdEc48pmotBg2Eofq89my8fn2gBImwIx9oLezYjfbEV?purpose=fullsize)](https://gcore.com/learning/what-is-http-3/)

**MP-QUIC - Multipath QUIC**

It extends QUIC's connection model to support multiple paths. QUIC runs over UDP, integrates TLS-based security, and supports multiple independent streams within a connection.

The question is not simply *which protocol is faster?* It is\:

**Under which conditions does each protocol work better, why does it behave that way, and what are the trade-offs?**

That is the central question running through your entire project.

## 2\. Understand the project in simple terms

Think of sending a large parcel using two delivery routes.

- Route A takes 10 milliseconds.
- Route B takes 100 milliseconds.
- Route A can deliver packets quickly, while Route B is much slower.

If you send alternating parts of a message over both routes, the later parts sent through Route A may arrive before earlier parts sent through Route B.

The receiver then has to wait for the missing earlier data before it can deliver the complete ordered message.

So, although you used two routes, the application might receive the data more slowly than if you had used Route A alone.

This is one of the most important ideas in your project: **more available network capacity does not automatically mean more useful application throughput.**

Your team needs to understand the mechanisms behind that outcome, the differences between MPTCP and MP-QUIC, and the evidence from research papers that supports the conclusions.

## 3\. What exactly is your role, Swamini?

The condensed plan assigns you the **research, performance analysis, and application-recommendation part** of the project. You have the lightest workload by design, but you still have to understand the central technical concepts well enough to defend your conclusions.

Your work has three connected parts.

**Part A - Existing research**

Questions Q159-163, Q167-168, Q171-172

Read research papers and understand what previous researchers discovered about MPTCP and MP-QUIC, the conditions they tested, and the limitations of their results.

---

**Part B - Congestion control, fairness and scheduling theory**

Q265-279 in the original plan

Understand why sending data over multiple paths can sometimes reduce useful throughput, and how a transport should share network capacity fairly.

---

**Part C - Applications and Quality of Experience (QoE)**

You lead Q177-190, with Q281 also highlighted

Explain what the protocols mean for video streaming, file downloads, voice calls and other applications. Recommend when aggregation or backup-only use makes more sense.

You also need to produce a diagram, a half-page cheat sheet, written answers, and a shared comparison/review contribution. The plan specifically asks you to draw a **“second path hurts” timeline** and to review Pratik's cheat sheet.

### Your main question

Your teach-back question - the one you should be able to explain without notes - is\:

> Why could adding a second network path decrease useful application throughput?

This is the question around which your research and technical preparation should be organised.

Here's a simple example of how to answer it.

Suppose a file is being sent over Wi-Fi and mobile data. Wi-Fi has a 10 ms round-trip time, while mobile data has a 100 ms round-trip time. If the receiver needs data in order, a chunk sent over the slower path might arrive late. Later chunks that arrive on Wi-Fi may have to wait in a buffer.

The second path consumes capacity, introduces more reordering, and can delay delivery of the complete data stream. If the scheduling and recovery mechanisms do not handle this well, the combined connection can deliver useful data more slowly than the best single path.

Your job is to go beyond that explanation: understand the mechanisms, examine published evidence, identify when the effect occurs, and explain what alternative design could avoid it.

## 4\. Your exact question list

The condensed plan is the current workload allocation. The original file contains the complete 323-question bank, which you can use when you need more detail.

| Priority | Questions | What you need to learn |
|--------|--------|--------|
| Your main research work | Q159-163 | Research questions, paper methodology, implementation details and platforms |
| Key published findings | Q167-168 | When aggregation succeeds or fails; handover and failover performance |
| Evidence and limitations | Q171-172 | Research limitations and the debate over whether QUIC needs multipath |
| Technical theory | Q265-279 | Congestion control, fairness, RTT differences, scheduling and goodput |
| Applications | Q177-190 | Video, file transfer, VoIP and practical recommendations |
| Deeper application questions | Q280-290 | QoE, streaming, bulk transfer, mobile networks and energy considerations |
| Deeper literature | Q291-297 | Protocol history and research validity; optional in the condensed plan |
| Shared viva preparation | Q1-28, Q177-205, Q298-300 | Fundamentals, applications, viva questions and tracing data end to end |

**Important distinction\:** the condensed plan makes Q159-163, Q167-168 and Q171-172 your specific research must-do list. It makes Q177-190 your lead responsibility, while Q177-205 is shared by everyone. Q265-279 is part of the original, more extensive plan; the condensed version explicitly highlights only Q265-269, Q274 and Q276 as your must-do technical questions, with the others available as reference.

You are also responsible for teaching the other three team members your assigned topics. They should be able to explain the key ideas afterward, not merely repeat your words.

## 5\. What you need to understand technically

Let's break your three areas into things you can actually study.

### A. Research papers: what did other people discover?

You are not expected to read every networking paper ever published. The condensed plan asks you to focus on the abstract and results of two sources first.

[![A Multipath Extension to the QUIC Module for ns-3 - Shemol106 - 博客园](https://images.openai.com/static-rsc-4/-TtDwBTzhKcm3Os3QmsjhiMhlqcrCA_-UiCw4HuTGuuqJvCYXf8UolLtVyPhHt81jN7rRRKuM6Fd1noJgba_TUqy0WhCjFXkbnyHxRDouL6xdlMj8PSM3osjlUWj5bUj0g7nUtAcrfTYrNhwaxrnO9Nn2FtnrmrC7x-gWddRlkHObQvGK5jXDekTnpnYZweB?purpose=fullsize)](https://www.cnblogs.com/shemol/articles/18313156)

**1\. CoNEXT 2017 - Multipath QUIC: Design and Evaluation**

Start with the abstract, experimental setup and results.

Find out\:

- Which implementations were compared?
- What happened in networks with and without packet loss?
- What did the authors conclude?
- What limitations prevent you from applying those results directly to current MP-QUIC?

---

[![Streaming High-Quality Mobile | PDF | Computer Network | Transmission Control Protocol](https://images.openai.com/static-rsc-4/KxD0WHlckEnebuHf8H5wRNskKa5waS-IoGLq9sLbubLJ2e-1amyBGD9b22W_1mpN0ODaPZ-QcXA0JehMNOLiRxZcEBiWreq9knQ8LSiyvrYU-fBFUdaEVb2aNZV8vxuZ7MUEHVn66MR6i7lWLoq40EQGx5rzqLdLkDMQBL94sGiDrYtmtRbi0-KmeHbseoMw?purpose=fullsize)](https://www.scribd.com/document/992123983/Streaming-High-Quality-Mobile)

**2\. MultipathTester - MNM 2019**

Begin with the abstract and learn what the researchers measured on mobile devices.

Find out\:

- What scenarios were tested?
- How was performance measured?
- Why might a real phone behave differently from a network simulated on one computer?

The paper titles and the precise findings should be verified against the original publications before you cite them. Your plan explicitly warns against relying on unverified figures.

For each paper, make a small research record\:

| Field | What to record |
|--------|--------|
| Research question | What were the authors trying to find out? |
| Implementation | Which MPTCP or MP-QUIC build and version? |
| Test setup | Real device, emulator or other environment? |
| Network conditions | Delay, bandwidth, packet loss and number of paths |
| Workload | File transfer, video or other traffic |
| Metrics | Throughput, goodput, latency, loss or recovery time |
| Findings | What did the results actually show? |
| Limitations | What prevents generalising the result? |

This is your **literature matrix**\. It helps you defend a statement with evidence instead of saying, “I read that MP-QUIC is faster.”

### B. Congestion control, fairness and scheduling

This is the technical foundation of your own special topic.

First, learn these terms\:

- **Throughput\:** how much data is transferred per unit of time.
- **Goodput\:** how much useful application data is delivered, excluding protocol overhead and redundant or retransmitted data.
- **RTT\:** round-trip time - how long it takes a signal to travel to the other endpoint and for a response to return.
- **Congestion control\:** how a sender adjusts its transmission rate to avoid overwhelming the network.
- **Fairness\:** whether flows sharing a bottleneck receive reasonable shares of the available capacity.
- **Scheduler\:** the mechanism that chooses which path should carry the next piece of data.

Consider this example\:

### The “second path hurts” example

Illustrative values, not experimental results.

**Fast path**

# 100 Mbps

RTT: 10 ms

**Slow path**

# 40 Mbps

RTT: 100 ms

**Best path alone**

Data arrives quickly and in the required order. In this simplified example, its capacity is 100 Mbps.

**Both paths used poorly**

The slow path delays some earlier data. Later data accumulates in a receive buffer, and the application waits for the missing data.

---

**Your question\:** how should the scheduler and congestion controller behave to avoid this outcome without sacrificing the benefit of multipath?

The combined nominal capacity in this example is 140 Mbps, but that does not mean the application will receive 140 Mbps of useful data. The actual outcome depends on the path conditions, protocol, congestion control, scheduling and buffering.

You should be able to explain\:

1. Why running a separate congestion controller on each path can be unfair when both paths share the same bottleneck.
2. Why RTT differences cause reordering.
3. Why a scheduler that always uses the lowest-RTT path might not achieve the best total throughput.
4. Why sending duplicate data can improve reliability but reduce goodput.
5. Why a backup-only strategy can sometimes be preferable to aggregation.

For reading, your condensed plan points you to RFC 6356 on coupled congestion control. The original plan also recommends the work on LIA, OLIA, BALIA and scheduler evaluations. Start with the fundamentals and only go deeper when your must-do answers require it.

### C. Applications and recommendations

You lead this part, so you need to turn the technical ideas into recommendations.

| Application | What matters most | Important trade-off to investigate |
|--------|--------|--------|
| Video streaming | Rebuffering, stable delivery and quality | Can a backup path prevent interruptions better than aggregating both paths? |
| Large file transfer | Completion time and goodput | Does aggregation improve useful transfer speed, or does reordering offset the gain? |
| VoIP / voice calls | Delay, jitter and packet loss | Does using both paths increase jitter or help maintain the call during a failure? |
| Mobile handover | Continuity while changing networks | Can a new path be established before the old path disappears? |

Your final recommendation should not simply state “MPTCP is better” or “MP-QUIC is better.”

Instead, it should say something like\:

- For a particular workload and network condition, protocol A may be preferable because of a specific mechanism.
- Protocol B may be preferable under a different condition.
- The recommendation is supported by a particular paper, a measured result or a clearly labelled hypothesis.
- A result that contradicts the hypothesis would make you reconsider the recommendation.

That last point matters because your plan requires you to identify what evidence would change your mind.

## 6\. What should you read, and in what order?

Keep the scope manageable. Your condensed plan intentionally reduces your reading workload.

## 1

**Learn the shared fundamentals**

Understand TCP reliability, RTT, congestion, loss, goodput and why multipath exists. Everyone must prepare Q1-28.

## 2

**Read your two research sources**

Start with the CoNEXT 2017 MPQUIC paper and the MultipathTester abstract. Extract the setup, results and limitations.

## 3

**Study the technical explanation**

Cover the must-do congestion-control and fairness questions, especially why the second path can hurt. Then connect these ideas to your research findings.

## 4

**Prepare your application recommendations**

Study video streaming, file transfer and VoIP. Write scenario-based answers for your teach-back.

## 5

**Create your deliverables and practise**

Finish your diagram, half-page cheat sheet and written answers. Exchange the cheat sheet with Pratik and practise answering questions without notes.

## 7\. What does the team schedule mean for you?

Your condensed plan replaces the original 13-day schedule with four sessions. Since today is October 24 and the deadline is November 4, use the shorter plan as your main schedule.

**Session 1**

Together

**Foundations - 3 hours**

Everyone studies Q1-28, answers them aloud and identifies gaps in understanding.

---

**Session 2**

Solo

**Your own block - 3-4 hours**

You prepare your research answers, technical explanations, diagram and cheat sheet, then send the cheat sheet to your reviewer.

---

**Session 3**

Together

**Teach-backs - 3.5 hours**

Each person teaches their topic. You explain your findings and applications, then answer follow-up questions. Kaushal leads the final comparison table, with Krina filling in the MPTCP side.

---

**Session 4**

Together

**Mock viva - around November 2-3**

Answer questions from your own area and the other members' areas. Fix weak answers and freeze the notes before the deadline.

On days without a session, spend at least 30 minutes answering one question from your own list and one cross-training question aloud.

The plan's deadline is November 4, with that date serving as a buffer. Confirm the team's actual meeting dates rather than assuming the older plan's daily schedule still applies.

## 8\. How should you answer questions in the viva?

The plan gives you a useful four-part structure. Use it for almost every technical question.

## 1

**What is it?**

Define the mechanism or concept in simple terms.

## 2

**Why does it exist?**

Explain the problem it solves and why the simpler alternative may fail.

## 3

**What does it cost?**

Discuss the trade-offs: delay, complexity, CPU, battery, fairness or useful throughput.

## 4

**How would you verify it?**

Name the relevant RFC or draft, research paper, measurement, trace or experiment. If you have not verified the claim, say so honestly.

For example, if Sir asks why a second path could hurt throughput, you should explain the reordering mechanism, why the scheduler may send data over a slower path, the cost of receiver buffering and blocking, and how you would verify the effect through a time-series trace or a well-designed comparison.

You are not expected to pretend you know everything. Your plan explicitly allows you to say **“not verified”** when you cannot support a claim.

## 9\. Your practical checklist

Use this as your personal progress tracker.

## Personal checklist

### /

[Copy checklist]

## 10\. What you should do first, starting today

Don't begin by trying to read all 323 questions. That will make the project feel much bigger than it needs to be.

Start with these three tasks\:

1. **Spend 30-45 minutes on the fundamentals.** Make sure you can explain multipath, RTT, congestion, throughput, goodput and head-of-line blocking.
2. **Read the CoNEXT 2017 paper abstract and results.** Write down the research question, setup, main finding and limitation. Do not copy a result until you've checked its context.
3. **Draft your “second path hurts” diagram.** Show data travelling along a fast and a slow path, the out-of-order arrivals, the receiver's buffer, and the delay before the application receives the complete ordered data.

Then build your literature matrix and write your assigned answers in your own words.

One final clarification: the current plan explicitly parks hands-on work - Mininet setup, NetEm configuration, iperf3 benchmarks and building QUIC stacks - for later if time remains. For now, your priority is **understanding, evidence, diagrams, teach-back and viva preparation**, not setting up a network experiment.

## Prompt:
10/24/2026, 2:36:20 PM

what are my final deliverables

## Response:
10/24/2026, 2:36:17 PM · gpt-6

> **Searching files for relevant information**
>
> 
>
> Worked for 9s

According to the **condensed MPTCP vs MP-QUIC plan**, your final deliverables are mainly a set of research answers, one technical diagram, a short cheat sheet, and a teach-back/viva preparation package. Your individual role is to explain **why adding a second network path can sometimes reduce useful application throughput**, and to lead the team's application-level recommendations.

## 1\. Your individual deliverables

**1\. Written answers to your assigned questions**

Prepare clear answers for **Q159–163, Q167–168, Q171–172, and Q177–190**, plus **Q281**\. Your main focus is the research findings, limitations, and application recommendations. fileciteturn5file0

---

**2\. One technical diagram: “Why the second path can hurt”**

Draw a timeline showing data sent across a fast, low-RTT path and a slower, high-RTT path. Show how out-of-order arrivals, buffering, and delayed delivery to the application can reduce useful throughput—even when the paths' nominal capacities add up to more.

---

**3\. A short personal cheat sheet**

The condensed plan asks each team member to prepare a **half-page cheat sheet**\. Include your key concepts, main research findings, important limitations, evidence sources, and likely viva follow-up questions.

---

**4\. Your teach-back**

Be ready to explain your assigned topic to the other three team members using your diagram, answer their “why?” questions, and let another member restate your explanation. The plan allocates you a 40-minute teach-back slot.

## 2\. Your most important shared deliverable: the recommendation table

For Q177–190, you lead the section that turns the research into practical conclusions. Prepare a final table like this\:

| Application / scenario | What matters most | Recommendation | Evidence strength |
|--------|--------|--------|--------|
| Large file transfer | Useful throughput | Depends on path conditions and scheduler | Published evidence / reasoning |
| Adaptive video streaming | Rebuffering and timely segment delivery | Compare aggregation with backup-only use | Evidence to verify |
| VoIP / real-time communication | Latency, jitter and packet loss | Evaluate low-latency or redundant scheduling | Evidence to verify |
| Sudden path failure | Recovery and continuity | Compare failover behaviour | Evidence to verify |
| One path has much higher RTT | Reordering and buffering | Test whether using both paths helps or hurts | Evidence to verify |

This is a **working template**, not your final scientific conclusion. Fill in each recommendation using the assigned papers and clearly distinguish published findings from predictions or your own measurements. Your plan explicitly requires this evidence distinction. fileciteturn5file9

## 3\. What the whole team must complete

These are shared team outcomes, not deliverables that belong only to you\:

- [ ] Answer the fundamentals questions, **Q1–28**, without notes.
- [ ] Understand the application and viva questions, **Q177–205**\.
- [ ] Be able to trace one byte through MPTCP and MP-QUIC and draw their side-by-side protocol stacks, **Q298–300**\.
- [ ] Participate in the comparison table for **Q133**\.
- [ ] Review Pratik's cheat sheet and resolve your review comments.
- [ ] Complete the mock viva and aim for a score of at least 2 on every shared-core question. fileciteturn5file2

## 4\. What you should have ready by the deadline

Your personal completion checklist is\:

### Your deliverables tracker

of

**Important\:** The condensed plan does not specify a separate formal report, poster, or software implementation as a required final deliverable. Its stated goal is research-based understanding, defensible explanations, diagrams, cheat sheets, team teach-backs, and viva readiness. Hands-on benchmarking is parked as optional work for now. The plan's deadline is **4 November 2026**\. fileciteturn5file2

## Prompt:
10/24/2026, 5:10:18 PM

for us lets work according to the older plan not condensed one so that i cover everything of my part and nothing is left, now give me my own complete plan to finish this off stepwise what to do first then what etc in short and the outcomes according to plan and final over project, give proper steps to finish correctly everything assigned to me

## Response:
10/24/2026, 5:09:27 PM · gpt-6

> **Remembering**
>
>
> ****
>
> 
>
> **Reviewed MPTCP plan, workload, question ranges, reading, and diagrams**
>
> 
>
> Worked for 21s

# Your complete MPTCP vs MP-QUIC project plan

We'll follow the **older, full plan** and use the condensed plan only as a reference—not as a reason to drop your original work. Your individual workload is\:

- **Part 9 — Q159–176\:** research methods, findings, and evidence.
- **Part 16 — Q265–279\:** congestion control, fairness, and scheduling.
- **Part 17 — Q280–290\:** application behaviour and quality of experience.
- **Part 18 — Q291–297\:** history, literature comparison, and research limitations.
- **Part 10 — Q177–190\:** your lead section on applications and recommendations.
- **Part 21 / shared viva preparation\:** especially Q281 and your cross-training questions.
- **Team responsibilities\:** prepare your technical diagram, written guide, research evidence, teach-backs, and review Pratik's guide/literature matrix as assigned.

Your central question is\:

**Why can adding a second network path sometimes reduce useful application throughput, and when should MPTCP or MP-QUIC use multiple paths?**

The full plan aims for understanding and defensible research—not merely memorising answers. We'll work in order, make each output before moving on, and track what is complete.

## Step-by-step execution plan

Follow these steps in order. Don't start by trying to answer all 323 questions at once.

## 1

**Set up your research workspace**

Create a folder called `MPTCP_MPQUIC_Swamini` with these subfolders\:

- `01_Research_Papers`
- `02_Q159-176_Research`
- `03_Q265-279_Theory`
- `04_Q280-290_Applications`
- `05_Q291-297_Literature`
- `06_Diagrams`
- `07_Final_Guide_and_Viva`

**Outcome\:** one organised place for all your work, with a question tracker and a list of unanswered questions.

---

## 2

**Research the existing work — Q159–176**

Read the assigned CoNEXT 2017 MPQUIC paper, MultipathTester paper, deployment study, RFC 8041, and scheduler literature. Build a literature matrix recording implementation/version, topology, path conditions, workload, metrics, congestion control, scheduler, findings and limitations.

**Outcome\:** 18 written answers and a sourced research matrix. Every numerical claim has its setup and source.

---

## 3

**Master congestion control, fairness and scheduling — Q265–279**

Read RFC 6356 and the assigned LIA, OLIA, BALIA, scheduler-evaluation, BLEST and ECF papers. Understand AIMD, bottlenecks, RTT differences, reordering, fairness, retransmission and redundant scheduling.

**Outcome\:** 15 written answers, a comparison of scheduling/congestion-control approaches, and your explanation of why a second path can reduce goodput.

---

## 4

**Understand application behaviour — Q280–290**

Study DASH/HLS, adaptive bitrate, startup delay, rebuffering, jitter buffers, RTP, MOS, bulk transfers, mobile Wi-Fi/cellular trade-offs, battery/data costs and satellite paths.

**Outcome\:** 11 written answers and an application-to-metric map explaining when aggregation, failover, handover or redundancy is useful.

---

## 5

**Complete the deeper literature and history — Q291–297**

Build the multipath-transport timeline, explain earlier approaches and deployment challenges, assess two papers' validity, compare the 2017 MPQUIC design with the later IETF draft, and verify claims against primary sources.

**Outcome\:** seven written answers, a research timeline and a limitations/validity assessment.

---

## 6

**Lead the application recommendations — Q177–190**

Use your research to compare file transfer, video, VoIP and path-failure scenarios. Cover asymmetric RTT, random loss, blocked UDP, legacy applications, deployment issues and evidence strength.

**Outcome\:** 14 written answers and the final recommendation table. State what evidence supports each recommendation and what result would change your conclusion.

---

## 7

**Create your diagrams and final guide**

Draw the “second path hurts” timeline, a conceptual aggregation-versus-RTT-ratio graph clearly marked as illustrative, and the literature matrix. Combine your answers into a readable guide, then make the half-page cheat sheet.

**Outcome\:** your complete individual research package, ready for review and teaching.

---

## 8

**Cross-training, teach-back and viva**

Practise Q167, Q168, Q172, Q177, Q180, Q181, Q183, Q184, Q185 and Q281. Prepare your explanation of the central question, teach your block, close gaps raised by the team, and participate in both mock vivas and the final dry run.

**Outcome\:** you can explain your reasoning without notes, defend your sources and acknowledge what remains unverified.

## How to write every answer

Use the same four-part structure for every question, as required by the older plan\:

1. **What is it?** Define the concept or finding.
2. **Why does it matter?** Explain the problem it solves.
3. **What does it cost or what are its limitations?** Compare alternatives.
4. **How do we verify it?** Give the paper, RFC/draft section, or measurement that supports the claim.

For research questions, add the **exact experimental setup and limitations** whenever you report a result. If a claim isn't verified, mark it clearly rather than guessing.

## Your final individual deliverables

By the project deadline, **4 November 2026**, aim to have\:

- [ ] Written answers for Q159–176, Q265–297, and Q177–190.
- [ ] A literature matrix with sources, setups, results and limitations.
- [ ] A history timeline and research-validity assessment.
- [ ] A technical timeline showing how a second path can hurt useful throughput.
- [ ] An illustrative aggregation-versus-RTT graph.
- [ ] An application recommendation table with evidence strength.
- [ ] A complete individual guide and half-page cheat sheet.
- [ ] Your teach-back and cross-training answers prepared.
- [ ] All unresolved questions documented and the mock-viva gaps closed.

**Team-wide work you must also be ready for\:** Q1–28 fundamentals, Q177–205 applications and viva questions, Q298–300 end-to-end protocol understanding and stack comparison, plus the Q133 MPTCP-versus-MP-QUIC comparison.

The older plan explicitly parks implementation and benchmarking for now. First complete the research and theory properly; only take on hands-on experiments if the team finishes the required understanding work early.

## What we do first

Start with **Step 1**, then tackle **Q159–176** before moving into the other blocks. That gives us the evidence base for your later technical explanations and recommendations.

The best working method is to finish one question at a time: source → notes → four-part answer → verification → viva practice. That way, your final guide is built progressively, and you can see exactly what remains incomplete.

## Prompt:
10/24/2026, 5:16:39 PM

in this also include the parts that are for everyone i also need to do that ones too, so include that too in this plan so that i can be ready with everything ive been assigned to properly

## Response:
10/24/2026, 5:15:55 PM · gpt-6

> **Reviewed file content and details**
>
> 
>
> Worked for 16s

# Complete personal plan: MPTCP vs MP-QUIC

We'll follow the **older, full project plan**, including both your individual blocks and every section assigned to everyone. The goal is to prepare you to answer questions across the project—not just your own research topic—while giving extra depth to the areas you lead.

The original plan contains **323 questions (Q1–Q323)**\. You do not need to master all 323 to the same depth: it specifies different priorities for each section. We'll preserve those priorities while making sure every section assigned to you is covered.

## 1\. Everything you are responsible for

| Priority | Section | Questions | What you need to achieve |
|--------|--------|--------|--------|
| Shared core | Why multipath exists | Q1–14 | Explain the purpose, benefits and trade-offs of using multiple network paths. |
| Shared core | Transport fundamentals | Q15–28 | Understand TCP, reliability, congestion, loss and ordering. |
| Your research block | Existing research | Q159–176 | Read and critically compare the assigned research papers. |
| Your lead section | Applications and recommendations | Q177–190 | Explain what works best for file transfer, video, VoIP and failure scenarios, with evidence. |
| Shared core | Viva curveballs | Q191–205 | Defend choices, limitations and recommendations. |
| Shared core | Deeper transport foundations | Q206–221 | Strengthen the underlying networking concepts. |
| Your technical block | Congestion control, fairness and scheduling | Q265–279 | Explain the algorithms, their costs and why a second path can hurt goodput. |
| Your deeper application block | Applications and quality of experience | Q280–290 | Understand application-specific metrics, user experience and trade-offs. |
| Your deeper research block | Literature and history | Q291–297 | Assess the research record, validity, deployment and limitations. |
| Shared core | End-to-end tracing | Q298–309 | Trace data through the protocols and explain the relevant packet and stack behaviour. |
| Shared core | Adjacent technologies and “why not X?” | Q310–322 | Compare multipath with alternatives and defend design decisions. |
| Shared core | A–Z term drill | Q323 | Recall and explain the key terminology. |

You also need to learn the other members' protocol-specific material well enough for the team's teach-backs and comparison: **MPTCP design and deployment (Krina), QUIC and MP-QUIC (Kaushal), and methods/tools as theory (Pratik)**\. The older plan gives the non-owner sections different priorities, so we'll focus on the shared-core questions first and build the other sections to the level specified in the plan.

## 2\. Your complete study and execution sequence

The older schedule began on 21 October, so we'll adapt it to the current date, **24 October**, and preserve the original priorities. The dates below are a catch-up schedule, not the original team's dates.

### Phase 1

24 Oct

**Build your foundation — Q1–28 and Q206–221**

Study why multipath exists, TCP reliability, ACKs, loss recovery, congestion control, HOL blocking, receive windows, MTU and the differences between TCP and UDP.

**Outcome\:** answer Q1–28 aloud without notes; prepare a list of gaps and learn the deeper foundations in Q206–221.

---

### Phase 2

24–25 Oct

**Complete your research block — Q159–176**

Read the assigned papers and RFC 8041. Build the literature matrix, verify the key results, compare implementations and document limitations.

**Outcome\:** 18 answers, a completed first version of the matrix, source references and a research gap list.

---

### Phase 3

25–26 Oct

**Complete congestion control and scheduling — Q265–279**

Cover fairness, AIMD, LIA, OLIA, BALIA, shared bottlenecks, resource pooling, scheduler decisions, queueing delay and receive-buffer blocking.

**Outcome\:** 15 answers, a comparison of the main algorithms, and your first version of the “second path hurts” explanation.

---

### Phase 4

26 Oct

**Study applications and QoE — Q280–290**

Cover video adaptation, startup delay, rebuffering, jitter buffers, voice quality, file-transfer completion time, mobile networks, energy and satellite paths.

**Outcome\:** 11 answers and a table connecting application needs to the right performance metrics.

---

### Phase 5

26–27 Oct

**Finish your deeper literature block — Q291–297**

Study the multipath timeline, earlier transport approaches, deployment evidence, research validity and how MP-QUIC evolved from the 2017 research implementation to the IETF draft.

**Outcome\:** seven answers, a timeline, a limitations assessment and a fully sourced literature matrix.

---

### Phase 6

27 Oct

**Finish your lead section — Q177–190**

Work through video, file transfer, VoIP, asymmetric RTT, random loss, path failure, UDP-blocking firewalls, legacy applications and deployment recommendations.

**Outcome\:** 14 answers and a final recommendation table distinguishing published evidence, reasoning and any measurements actually performed.

---

### Phase 7

28 Oct

**Prepare the shared-core material — Q191–205**

Practise explaining why not to use either protocol everywhere, why not simply open multiple ordinary connections, how to assess a benchmark, and how to explain both protocols to a beginner.

**Outcome\:** 15 prepared answers and the ability to defend your recommendations and acknowledge uncertainty.

---

### Phase 8

28–29 Oct

**Learn the other members' protocols and methods**

Use Krina's material for MPTCP (Q29–74 and Q222–237), Kaushal's material for QUIC/MP-QUIC (Q75–116 and Q238–264), and Pratik's material for methods/tools (Q135–158) and adjacent technologies (Q310–322).

Start with the original plan's Tier 1 questions, then Tier 2. Don't spend all your time memorising specialist details before you can explain the shared fundamentals.

**Outcome\:** you can follow the team's teach-backs, ask meaningful follow-up questions and answer the important questions outside your own block.

---

### Phase 9

29–30 Oct

**Connect the protocols end to end — Q298–309**

Trace a 1 MB upload through MPTCP and MP-QUIC. Draw both stacks side by side, locate each mechanism, compare failure behaviour and explain how to verify that a second path actually carries data.

**Outcome\:** answers to all 12 questions, especially Q298–300, and a complete side-by-side stack diagram.

---

### Phase 10

30 Oct–2 Nov

**Review, teach and test yourself**

- **30 Oct\:** finalise your diagrams and guide; complete Q323 and your cross-training set.
- **31 Oct\:** mock viva 1—foundations and protocol theory.
- **1 Nov\:** mock viva 2—methods, research, applications and advanced questions.
- **2 Nov\:** final dry run; fix weak answers and freeze your notes.

**Outcome\:** every Tier 1 question is answerable at score 2 or higher, with a reason and a credible way to verify the claim.

---

### Buffer

3–4 Nov

**No new material**

Review the cheat sheet, research matrix, diagrams and unresolved points. Use the final day to correct mistakes rather than starting a new topic.

**Outcome\:** your final project preparation is complete by **4 November**\.

## 3\. Your shared-core question sets

These are the additional sections you must not forget, even though they are not your specialist blocks.

| Section | Required preparation |
|--------|--------|
| Q1–28 | Tier 1: answer without notes |
| Q177–205 | Tier 1: applications and viva curveballs |
| Q206–221 | Tier 2: deeper transport foundations |
| Q298–309 | Tier 1: end-to-end tracing; prioritise Q298–300 |
| Q323 | Tier 1: define each term in one or two sentences |

Also learn the **10 cross-training questions assigned to your block** for the other team members to ask you: Q167, Q168, Q172, Q265, Q269, Q274, Q276, Q281, plus Q177 and Q183 from Part 10.

For your own viva preparation, give extra attention to Q281 because it links your video QoE material to your core research question.

## 4\. Your final submission-ready package

By the end, organise your individual work into these files\:

01

**Swamini\_Research\_Answers.md**

Q159–176, Q265–297 and Q177–190

02

**Literature\_Matrix.xlsx**

Sources, implementations, setups, findings and limitations

03

**Technical\_Diagrams.pdf**

Second-path-hurts timeline, illustrative aggregation/RTT graph, and protocol stack comparison

04

**Application\_Recommendations.md**

Recommendations, conditions and evidence strength

05

**Swamini\_Viva\_Guide.md**

Shared-core answers, cross-training questions and four-beat explanations

06

**Half\_Page\_Cheat\_Sheet.pdf**

Highest-priority mechanisms, findings and caveats

These are **recommended file names and organisation**, not a claim that the course requires six separate uploads. The older plan explicitly asks for your written answers, diagram, one-page guide, literature matrix, cross-review and viva preparation; follow any separate submission instructions your instructor gives.

## 5\. What is first, right now?

Start with **Q1–28**, because the original plan treats these as a shared Tier 1 foundation. Then move into your own research block, Q159–176.

For every question, follow this repeatable process\:

1. Read the relevant primary source.
2. Write the answer in your own words using the four beats: *what it is, why it exists, what it costs, how to verify it*\.
3. Add the source or section supporting the claim.
4. Draw a timeline or small diagram when it helps.
5. Close your notes and answer aloud.
6. Put anything you cannot defend on your gap list.

The final goal is not just to have all the answers written down. It is to be able to explain **why the mechanism exists, why an alternative might be worse, what the trade-off is, and what evidence would prove your answer right or wrong**\.

## Prompt:
10/26/2026, 5:09:26 PM

ok so now lets start according to this plan correctly and finish all of this quickly but accurately, now lets start with the Q1-28, before that give me a structured folder to create so that my all work is structured and placed correctly

## Response:
10/26/2026, 5:08:33 PM · gpt-6

> **Remembering**
>
>
> ****
>
> 
>
> **Structuring study folders**
>
> I’m preparing a PowerShell command that creates the complete folder system under Documents, including administration, Q1–Q28, shared team materials, research, outputs, and tracking files.
>
> **Structured study folders**
>
> 
>
> **Reviewed MPTCP setup, project folder, deliverables, and structure**
>
> 
>
> Worked for 43s

We'll use the **older full plan** as our master plan and work through it systematically. First, we'll create one organized workspace for all your notes, research, diagrams, references, and viva preparation. Then we'll start Q1-28 in the same order as the plan.

The plan's rule for every answer is important: **what it is → what problem it solves → its cost or limitation → how you would verify it.** We'll use that structure from the beginning, rather than memorizing disconnected definitions.

## 1\. Create your project folder

I recommend putting it in your Windows **Documents** folder so it's easy to find and back up.

Open **PowerShell** and paste this entire command. It creates the folders and starter files without deleting or overwriting your existing work.

```powershell

$base = Join-Path $env:USERPROFILE "Documents\MPTCP_MPQUIC_Swamini"

$folders = @(
    "00_Project_Admin",
    "01_Foundations_Q1-28",
    "02_MPTCP_Reference",
    "03_MPQUIC_Reference",
    "04_Comparison_and_Scheduling",
    "05_Research_Q159-176",
    "06_Applications_Q177-205",
    "07_Congestion_Fairness_Q265-279",
    "08_Applications_Q280-290",
    "09_Literature_History_Q291-297",
    "10_End_to_End_Q298-309",
    "11_Adjacent_Technologies_Q310-322",
    "12_Diagrams",
    "13_Literature_Matrix",
    "14_Team_Guides_and_Reviews",
    "15_Viva_and_Cheat_Sheets",
    "16_Sources_Papers_RFCs",
    "17_Final_Deliverables"
)

New-Item -ItemType Directory -Path $base -Force | Out-Null

foreach ($folder in $folders) {
    New-Item -ItemType Directory -Path (Join-Path $base $folder) -Force |
        Out-Null
}

$files = @{
    "00_Project_Admin\Master_Progress_Tracker.md" = "# Master Progress Tracker`r`n`r`n| Section | Read | Answers written | Recall tested | Gaps resolved |`r`n|---|---|---|---|---|`r`n| Q1-14: Why multipath | | | | |`r`n| Q15-28: Transport fundamentals | | | | |`r`n| Q159-176: Research | | | | |`r`n| Q177-205: Shared applications and viva | | | | |`r`n| Q206-221: Deeper transport foundations | | | | |`r`n| Q265-297: Your specialist blocks | | | | |`r`n| Q298-309: End-to-end trace | | | | |`r`n| Q310-323: Other technologies and term drill | | | | |"
    "01_Foundations_Q1-28\Q1-14_Why_Multipath.md" = "# Q1-14 - Why Multipath Exists`r`n`r`nUse the four-beat answer structure: definition, purpose, cost/limitation, verification/evidence.`r`n"
    "01_Foundations_Q1-28\Q15-28_Transport_Fundamentals.md" = "# Q15-28 - TCP and Transport Fundamentals`r`n`r`nUse the four-beat answer structure: definition, purpose, cost/limitation, verification/evidence.`r`n"
    "05_Research_Q159-176\Research_Answers.md" = "# Q159-176 - Existing Research`r`n"
    "06_Applications_Q177-205\Applications_and_Viva.md" = "# Q177-205 - Applications, Recommendations and Viva`r`n"
    "07_Congestion_Fairness_Q265-279\Congestion_Fairness_Scheduling.md" = "# Q265-279 - Congestion Control, Fairness and Scheduling`r`n"
    "08_Applications_Q280-290\QoE_Notes.md" = "# Q280-290 - Applications and Quality of Experience`r`n"
    "09_Literature_History_Q291-297\Literature_History.md" = "# Q291-297 - Literature and History`r`n"
    "10_End_to_End_Q298-309\End_to_End_Trace.md" = "# Q298-309 - End-to-End Protocol Traces`r`n"
    "11_Adjacent_Technologies_Q310-322\Why_Not_X.md" = "# Q310-322 - Adjacent Technologies and Why Not X`r`n"
    "13_Literature_Matrix\Literature_Matrix.csv" = "Paper,Year,Protocol,Research question,Implementation/version,Topology,Path conditions,Workload,Metrics,Main findings,Limitations,Evidence/URL,Relevance to our project`r`n"
    "15_Viva_and_Cheat_Sheets\Viva_Gap_Log.md" = "# Viva Gap Log`r`n`r`n| Question | What I missed | Correct explanation | Evidence to check | Re-tested? |`r`n|---|---|---|---|---|"
    "16_Sources_Papers_RFCs\Source_Register.md" = "# Source Register`r`n`r`nRecord the exact title, author/organization, date/version, section/page, URL, and the claim supported. Mark anything not yet verified as NOT VERIFIED."
}

foreach ($entry in $files.GetEnumerator()) {
    $path = Join-Path $base $entry.Key
    if (-not (Test-Path $path)) {
        Set-Content -LiteralPath $path -Value $entry.Value -Encoding UTF8
    }
}

Write-Host "`nWorkspace created at: $base" -ForegroundColor Green
Write-Host "`nOpening project folder..."
Invoke-Item $base
```

After it runs, the folder should open automatically. The `-Force` option here creates missing folders; the script also checks before creating each starter file, so existing files with the same names are left alone.

## 2\. What goes where?

**`01_Foundations_Q1-28`**

Your first study block: why multipath exists, TCP fundamentals, answer drafts, diagrams, and corrections.

---

**`02`-`04` and `16_Sources_Papers_RFCs`**

Protocol reference notes and source material. Keep original papers and RFCs separate from your own explanations.

---

**`05`-`11`**

Your assigned research and specialist topics, plus the shared application, end-to-end, and adjacent-technology sections.

---

**`12_Diagrams` and `13_Literature_Matrix`**

The second-path-hurts timeline, protocol-stack comparison, throughput/RTT illustration, and evidence-backed paper comparison.

---

**`14`-`17`**

Team guides and review comments, viva practice and cheat sheets, source records, and final polished deliverables.

**Working rule\:** keep rough notes in the relevant topic folder, record every unresolved question in `Viva_Gap_Log.md`, and only move polished material into `17_Final_Deliverables`\. The suggested filenames are for our organization, not a claim that the course requires every file as a separate submission.

## 3\. Start studying: Q1-14 - Why multipath exists

These are the exact questions from Part 1 of your full plan. fileciteturn10file2

For each question, I'll give you a clear answer to understand first, followed by the important viva point. You can copy these into `01_Foundations_Q1-28\Q1-14_Why_Multipath.md`\.

### Q1. What problem does a multipath transport solve that single-path TCP or QUIC cannot? Give one example each for bandwidth, handover and resilience.

**Answer**

A conventional TCP or QUIC connection generally sends its traffic over one active network path at a time. A multipath transport can use multiple paths within one logical transport connection, allowing it to combine available capacity, maintain connectivity during a path change, or continue operating if one path fails.

- **Bandwidth aggregation\:** a laptop uses Wi-Fi and Ethernet to transfer a large file, potentially increasing throughput.
- **Handover\:** a phone moves from Wi-Fi to cellular while a download continues over the surviving or newly established path.
- **Resilience\:** if one path fails, traffic can continue over another available path.

**Limitation\:** the benefits depend on path quality, congestion, scheduling, and whether both endpoints and the implementation support multipath.

**Viva takeaway\:** multipath provides opportunities for higher throughput, continuity, and resilience; it does not guarantee all three simultaneously.

### Q2. Why not let applications open several ordinary TCP connections, one per interface? What does a multipath transport add that "many connections" does not?

**Answer**

An application can open multiple TCP connections, but these are separate transport connections. The application must coordinate them, distribute data, track progress, and potentially reorder data or recover from a failed connection.

A multipath transport provides a single logical connection across multiple subflows or paths. It coordinates data scheduling and connection-level delivery within the transport.

| Multiple ordinary TCP connections | Multipath transport |
|--------|--------|
| Separate TCP connections | One logical connection with multiple paths |
| Application may need to split and reassemble data | Transport coordinates data across paths |
| Independent connection state | Shared connection-level state plus path-specific state |
| Coordination and recovery may be application-specific | Multipath behavior is handled by the transport |

**Limitation\:** multipath transport is more complex to implement and debug, and it cannot remove the physical limitations of the paths.

**Viva takeaway\:** multiple connections offer parallelism; multipath transport adds coordinated use of multiple paths for one logical connection.

### Q3. Why does a plain TCP connection die when Wi-Fi drops and the phone switches to LTE? What exactly identifies a TCP connection?

**Answer**

A TCP connection is identified by a four-tuple\:

- Source IP address
- Source port
- Destination IP address
- Destination port

When a phone changes from Wi-Fi to LTE, its source IP address or network mapping may change. The resulting packets may no longer match the existing TCP connection's four-tuple, so the old connection generally cannot simply continue on the new path.

**Limitation\:** the old connection might survive if the addressing and network mapping remain compatible, but a normal TCP connection has no standard mechanism to transparently migrate its established connection state to a new four-tuple.

**Viva takeaway\:** the problem is not merely that the network interface changed; the connection's network identity or reachability may have changed.

### Q4. How do multihoming, ECMP load balancing and multipath transport differ? Why does ECMP not give one flow more than one path's capacity?

**Answer**

- **Multihoming\:** a host or network has multiple network connections or addresses.
- **ECMP (Equal-Cost Multi-Path)\:** routers distribute flows across equal-cost routes, commonly using a hash of packet or flow fields.
- **Multipath transport\:** the transport protocol coordinates multiple paths for one logical connection.

ECMP commonly keeps packets belonging to the same flow on one selected route to avoid excessive reordering. Therefore, one ordinary TCP flow usually does not automatically aggregate the capacity of several ECMP routes.

**Limitation\:** ECMP implementations vary, and packet-level load balancing can exist, but it can introduce reordering. Having multiple routes available does not mean a single transport connection uses all of them.

**Viva takeaway\:** multihoming provides options, ECMP distributes traffic in the network, and multipath transport coordinates path use at the transport layer.

### Q5. A multipath transport can aim for more throughput, more resilience, or balanced load. Describe a scenario where two of these goals conflict.

**Answer**

Imagine a phone with fast Wi-Fi and a slower cellular connection.

- Using both paths aggressively may increase aggregate throughput.
- Keeping cellular lightly used preserves battery and data allowance.
- Maintaining a ready-to-use cellular path may improve resilience if Wi-Fi fails.

The goals conflict because sending more data over cellular may improve aggregate throughput but consume more energy and mobile data. Conversely, keeping cellular idle or lightly used reduces costs but may limit aggregation.

**Limitation\:** the best trade-off depends on the application, path characteristics, data plan, energy cost, and failure risk.

**Viva takeaway\:** multipath policy is a trade-off, not simply a decision to maximize the number of active paths.

### Q6. List the costs of multipath: complexity, reordering, buffer demand, energy, middlebox risk, fairness. Which one hurts real-time traffic most, and why?

**Answer**

Multipath introduces several costs\:

- **Complexity\:** more connection state, scheduling decisions, and failure cases.
- **Reordering\:** data sent on different paths may arrive out of order.
- **Buffer demand\:** early-arriving data may need to wait for delayed data.
- **Energy\:** using multiple interfaces can consume more battery.
- **Middlebox risk\:** network devices may interfere with protocol behavior or path establishment.
- **Fairness\:** a multipath connection may compete unfairly with ordinary single-path flows.

For real-time traffic, **variable delay and reordering** can be especially harmful because audio and video have deadlines. Data arriving too late may be useless even if it is eventually delivered correctly.

**Limitation\:** the dominant cost varies by application; for a battery-powered device, energy may matter more than reordering.

**Viva takeaway\:** real-time applications care about timely delivery, not just eventual reliable delivery.

### Q7. Explain the exact mechanism by which a second path can make a transfer slower than the best single path.

**Answer**

Suppose a transport sends consecutive pieces of data over two paths\:

- Path A has a low RTT and delivers later-numbered data quickly.
- Path B has a much higher RTT and delays earlier-numbered data.

The receiver gets the later data first, but cannot deliver the missing earlier bytes to the application in order. The later data must wait in a receive buffer. If the buffer fills, the sender may be unable to send more data efficiently.

This can reduce useful application throughput, also called **goodput**, even though the second path carries traffic.

**The mechanism is\:**

1. Different path delays cause packet or data reordering.
2. Missing earlier data delays in-order delivery.
3. Out-of-order data consumes receiver buffer space.
4. Buffer pressure and scheduling decisions can limit further progress.
5. The resulting goodput can be lower than using only the best path.

**Limitation\:** this is a possible outcome, not an inevitable one. Scheduling, congestion control, buffer sizes, and the workload affect the result.

**Viva takeaway\:** adding path capacity does not guarantee higher goodput because data must still arrive in a form and order the application can use.

### Q8. When does multipath give almost no benefit?

**Answer**

Multipath may provide little benefit when\:

- One path is much slower or less reliable than the other.
- Both paths share the same bottleneck, so they do not provide independent capacity.
- The transfer is very small and finishes before multipath overhead pays off.
- The application is the bottleneck and cannot generate data quickly enough.
- The extra path has high loss or delay, causing reordering and buffering costs.
- The second path is expensive to activate in terms of energy or setup time.

**Limitation\:** a path that adds little throughput may still be useful as a backup for resilience.

**Viva takeaway\:** evaluate the goal first. A path that adds little bandwidth might still add reliability.

### Q9. What is a shared bottleneck, and why is it the central fairness problem for multipath? What does "do no harm" to single-path flows mean?

**Answer**

A **shared bottleneck** occurs when traffic from multiple paths passes through the same constrained link or queue. Although a multipath connection may use two distinct routes, both can compete for capacity at that common point.

If a multipath connection increases its aggregate sending rate, it may take more than a fair share of the shared bottleneck's capacity and reduce throughput for ordinary single-path TCP flows.

The "do no harm" goal means a multipath connection should not unfairly disadvantage competing single-path flows, particularly when they share a bottleneck.

**Limitation\:** fairness depends on the congestion-control algorithm, network topology, RTTs, and competing traffic; it cannot be guaranteed merely by opening multiple paths.

**Viva takeaway\:** two paths are not necessarily two independent resources.

### Q10. Define aggregation, failover and handover. Which one do video streaming, bulk file transfer and VoIP each need most?

**Answer**

- **Aggregation\:** using multiple paths to increase available throughput.
- **Failover\:** continuing over another path when the current path fails.
- **Handover\:** moving or shifting connectivity as a device changes its network attachment, such as from Wi-Fi to cellular.

Typical priorities\:

| Application | Likely priority | Why |
|--------|--------|--------|
| Bulk file transfer | Aggregation | Higher throughput can reduce completion time |
| Video streaming | Aggregation and resilience | Throughput helps maintain video quality; continuity helps avoid interruptions |
| VoIP | Handover and low-delay continuity | Late or missing audio harms conversation quality |

**Limitation\:** these are typical priorities, not universal rules. For example, live video may prioritize latency over aggregate throughput.

**Viva takeaway\:** the application determines which multipath benefit matters most.

### Q11. Why do short flows (a small web object) rarely benefit from multipath while long flows do?

**Answer**

A short flow may finish before the transport has fully established, scheduled, and benefited from multiple paths. Setup overhead and initial congestion-control behavior can consume much of the potential benefit.

A long flow has more time to use additional path capacity, so aggregation can reduce its completion time if the paths and scheduler are suitable.

**Limitation\:** short flows can still benefit from an already-established multipath connection or from resilience during a path failure.

**Viva takeaway\:** the potential gain from aggregation must be large enough to outweigh setup and coordination overhead.

### Q12. What does multipath cost a battery-powered phone? Why do some deployments keep cellular as backup only?

**Answer**

Using multiple interfaces can increase power consumption through radio activity, connection maintenance, packet transmission, and additional processing. Cellular data may also incur financial costs or data-cap restrictions.

A deployment may keep cellular as a backup so it can provide continuity when Wi-Fi fails without constantly using cellular capacity and energy.

**Limitation\:** the energy cost depends on the hardware, radio states, traffic pattern, and implementation. Keeping a backup path ready can itself consume some power.

**Viva takeaway\:** more paths can improve connectivity but may cost battery and mobile data.

### Q13. Why do both protocols treat path management (which addresses to use) and scheduling (which path carries the next data) as separate decisions? What is gained?

**Answer**

These are different problems\:

- **Path management** determines which paths can be established or maintained, using available addresses and network connectivity.
- **Scheduling** decides where to send data among the available paths.

Separating them lets the system change the set of usable paths independently from the policy used to distribute data. For example, a path manager may add a cellular path, while a scheduler decides to use it only when the Wi-Fi path is congested or unavailable.

**Limitation\:** good scheduling cannot fix a path that was never established or is not usable. Likewise, establishing more paths does not guarantee that the scheduler will use them effectively.

**Viva takeaway\:** path management answers "which paths are available?"; scheduling answers "which available path should carry this data?"

### Q14. Why put multipath in the transport layer rather than in link bonding, the network layer or the application? Give one advantage and one drawback of each place.

**Answer**

| Layer or approach | Advantage | Drawback |
|--------|--------|--------|
| Link bonding | Can combine links transparently below IP in suitable environments | Often requires support or configuration at the link/network infrastructure and may not work across arbitrary Internet paths |
| Network layer | Can choose or route packets over different paths | Requires routing support and careful handling of packet reordering and flow behavior |
| Transport layer | Can coordinate multiple paths for one logical connection and manage transport delivery | Requires protocol support at endpoints and must handle congestion, reordering, and compatibility |
| Application layer | Can customize decisions for application-specific needs | Each application may need to implement its own splitting, recovery, and reassembly logic |

**Viva takeaway\:** the transport layer offers a useful balance between application transparency and control over reliable data delivery, but it introduces endpoint and deployment complexity.

---

## 4\. Quick recall test before moving to Q15-28

Don't memorize every paragraph word for word. Close your notes and try these five prompts aloud\:

**Next in the plan: Q15-28, TCP and transport fundamentals.** These cover reliable delivery, head-of-line blocking, loss recovery, congestion control, buffers, middleboxes, and performance metrics. We'll treat them as a separate set in your `Q15-28_Transport_Fundamentals.md` file.

## Prompt:
10/26/2026, 11:32:05 PM

done now first give commands to put these completed ques in proper folder then will move to next part

## Response:
10/26/2026, 11:31:11 PM · gpt-6

Run these commands in **PowerShell** to save the completed Q1-14 and Q15-28 answers into the correct files in your project folder.

### Step 1 - Open your project folder in PowerShell

```powershell
$base = Join-Path $env:USERPROFILE "Documents\MPTCP_MPQUIC_Swamini"
Set-Location $base
```

### Step 2 - Check that the destination files exist

```powershell
Test-Path ".\01_Foundations_Q1-28\Q1-14_Why_Multipath.md"
Test-Path ".\01_Foundations_Q1-28\Q15-28_Transport_Fundamentals.md"
```

Both commands should return `True`\.

### Step 3 - Open the Q1-14 answer file

```powershell
notepad ".\01_Foundations_Q1-28\Q1-14_Why_Multipath.md"
```

Copy the **Q1-14 answers** from my previous response, paste them into Notepad, then press **Ctrl + S** and close it.

### Step 4 - Open the Q15-28 answer file

```powershell
notepad ".\01_Foundations_Q1-28\Q15-28_Transport_Fundamentals.md"
```

Keep this file ready for the next section. **Don't paste Q1-14 into this file**; it is reserved for Q15-28.

### Step 5 - Verify your saved file

After saving Q1-14, run\:

```powershell
Get-Content ".\01_Foundations_Q1-28\Q1-14_Why_Multipath.md" -TotalCount 8
```

You should see the heading and the start of your answers.

**Important\:** These commands create/open files but do not automatically transfer text from the chat. You need to copy the Q1-14 answers into the first file yourself.

Once that is saved, we're ready to proceed with **Q15-28: TCP and transport fundamentals**\.

## Prompt:
10/26/2026, 11:41:55 PM

give ques 1--14 to put in ".\01_Foundations_Q1-28\Q1-14_Why_Multipath.md" in proper format to directly paste here with right formatting then will move ahead

## Response:
10/26/2026, 11:41:03 PM · gpt-6

Copy the complete Markdown below into\:

`01_Foundations_Q1-28\Q1-14_Why_Multipath.md`

It is formatted as a standalone study note, with each question followed by a viva-ready answer, key takeaway, and examples where useful.

```markdown

# Part 1 - Why Multipath Exists and What It Costs
## Questions 1-14 | Tier 1: Core Viva Preparation

## Q1. Why do we need multipath transport? What are its main benefits?

**Answer:**

Multipath transport allows one logical transport connection to use more than one network path. For example, a device may be connected to both Wi-Fi and cellular data.

Its three main benefits are:

1. **Throughput aggregation:** Data can be transmitted over multiple paths simultaneously, potentially increasing the total throughput available to an application.
2. **Resilience:** If one path fails, communication can continue over another available path, provided the connection and application can tolerate the transition.
3. **Seamless handover:** When a device moves between networks, multipath transport can help maintain an ongoing connection instead of requiring the application to establish a completely new transport connection.

However, these benefits are not guaranteed. The paths may share a bottleneck, have different delays, or introduce additional overhead.

**Example:** A phone uses Wi-Fi and cellular data simultaneously. Wi-Fi provides most of the data transfer, while cellular connectivity provides an alternative if Wi-Fi becomes unavailable.

**Key takeaway:** Multipath aims to improve throughput, resilience, and continuity, but the actual benefit depends on the network conditions.

---

## Q2. Why not simply use multiple independent TCP connections instead of multipath transport?

**Answer:**

An application could open multiple independent TCP connections, but this is not equivalent to using a multipath transport protocol.

With independent TCP connections:

- Each connection has its own TCP state and congestion-control behavior.
- The application must manage multiple connections and coordinate their data if it wants to treat them as one logical transfer.
- The connections may compete unfairly with other traffic when they share a bottleneck.
- A change in network address may disrupt an individual connection.

With Multipath TCP (MPTCP), multiple TCP subflows can carry data belonging to one logical connection. MPTCP uses additional sequence-numbering and connection-management mechanisms to coordinate data across those subflows.

This allows the application to use a single logical byte stream while the transport manages multiple paths.

**Example:** Instead of making an application split a file into pieces and manage two separate TCP connections itself, MPTCP can use multiple subflows to carry data for the same connection.

**Key takeaway:** Multiple TCP connections are independent connections; MPTCP coordinates multiple subflows as part of one logical transport connection.

---

## Q3. What is the TCP 4-tuple, and why can changing from Wi-Fi to cellular break a TCP connection?

**Answer:**

A TCP connection is traditionally identified by a four-part tuple:

1. Source IP address
2. Source port
3. Destination IP address
4. Destination port

Together, these values identify the connection at the transport layer.

Suppose a device establishes a TCP connection over Wi-Fi. The connection uses the device's Wi-Fi IP address. If the device switches to cellular data, its source IP address may change.

The new source IP address produces a different 4-tuple. Ordinary TCP does not automatically treat this new tuple as the same existing connection, so packets may no longer belong to the established connection. The application may need to establish a new connection.

MPTCP can support address changes and additional subflows through its connection-management mechanisms, subject to implementation and network support.

**Example:**

- Before the switch: `Wi-Fi IP:port → Server IP:port`
- After the switch: `Cellular IP:port → Server IP:port`

The changed source address means the original TCP connection cannot ordinarily continue just by sending packets from the new address.

**Key takeaway:** A conventional TCP connection is tied to its connection tuple, whereas multipath protocols can provide mechanisms for maintaining a logical connection across paths.

---

## Q4. Distinguish multihoming, ECMP, and multipath transport.

**Answer:**

These concepts are related, but they solve different problems.

**1. Multihoming**

A device or network has multiple network interfaces or possible network connections. For example, a laptop may have both Ethernet and Wi-Fi.

Multihoming provides multiple connectivity options, but it does not automatically mean that a single transport connection uses all of them simultaneously.

**2. Equal-Cost Multipath (ECMP)**

ECMP is a network-layer forwarding technique. Routers can distribute traffic across multiple equal-cost routes, commonly using a hash of packet or flow fields.

In many ECMP implementations, packets from a particular flow remain assigned to one selected path to avoid excessive packet reordering. Therefore, ECMP does not necessarily split one transport flow across several paths.

**3. Multipath transport**

A multipath transport protocol can use multiple paths or subflows for one logical transport connection. It manages transport-level concerns such as data delivery, congestion control, and scheduling.

**Example:** A server may have two network interfaces (multihoming), its routers may use ECMP for forwarding different flows, and an MPTCP connection may use multiple subflows to transfer data.

**Key takeaway:** Multihoming provides multiple interfaces, ECMP distributes traffic at the network layer, and multipath transport coordinates paths for a transport connection.

---

## Q5. What are the main objectives of multipath transport, and can they conflict?

**Answer:**

The three main objectives are:

- **Throughput:** Use available paths to increase the rate at which useful application data is delivered.
- **Resilience:** Keep communication working when one path becomes unavailable or unreliable.
- **Cost and resource efficiency:** Avoid unnecessary cellular-data usage, battery consumption, and other resource costs.

These objectives can conflict.

For example, using Wi-Fi and cellular simultaneously may increase throughput, but it can also consume cellular data and battery power. Using a second path only as a backup may provide resilience while avoiding most of that extra usage.

The best policy depends on the application's requirements and the user's preferences.

**Example:** A large file download may benefit from using both paths, while a phone trying to conserve cellular data may use cellular only when Wi-Fi fails.

**Key takeaway:** Multipath design involves trade-offs; maximizing throughput is not always the same as maximizing overall user benefit.

---

## Q6. What costs and complications does multipath transport introduce?

**Answer:**

Multipath transport offers additional connectivity options, but it also introduces complexity.

Its major costs include:

1. **Reordering:** Different paths may have different delays, causing data sent later to arrive before earlier data.
2. **Buffering:** The receiver may need to retain out-of-order data until missing data arrives.
3. **Congestion-control complexity:** The protocol must control traffic across paths while considering shared bottlenecks and fairness.
4. **Path management:** It must discover, establish, monitor, and remove paths or subflows.
5. **Energy and data usage:** Sending or probing traffic over additional interfaces may consume more battery and cellular data.
6. **Compatibility:** NATs, firewalls, middleboxes, and network policies may restrict the protocol or its additional connections.
7. **Scheduling overhead:** The sender must decide which path should carry each piece of data.

The cost can be especially noticeable when one path is much slower than another or when the paths share the same bottleneck.

**Example:** Sending data over both low-latency Wi-Fi and high-latency cellular may create reordering and buffering costs even if both paths are available.

**Key takeaway:** More paths create more options, but they also create more state, coordination, and potential performance problems.

---

## Q7. Why could adding a second path decrease useful application throughput?

**Answer:**

Adding a second path can sometimes reduce useful application throughput because the paths may have significantly different delays or performance characteristics.

Consider a low-latency path and a high-latency path:

1. The sender transmits earlier data over the slower path.
2. It transmits later data over the faster path.
3. The later data arrives first, but the earlier data is still missing.
4. The receiver may have to buffer the later data while waiting for the missing earlier data.
5. The application may be unable to consume the complete ordered byte stream until the gap is filled.

This can increase buffering and delivery delay. If the receive buffer fills, or if the sender's scheduling and congestion-control decisions are poor, useful application throughput (goodput) may fall.

The second path can still be beneficial if the scheduler accounts for path delay, the application tolerates out-of-order delivery, or the protocol can manage the reordering efficiently. The outcome depends on the path conditions and implementation.

**Example:** Wi-Fi has an RTT of 20 ms, while cellular has an RTT of 150 ms. Data sent over Wi-Fi may arrive well before earlier data sent over cellular, delaying ordered delivery.

**Key takeaway:** Aggregate path capacity does not automatically translate into higher application goodput. Reordering, waiting, buffering, and scheduling decisions can reduce the benefit.

---

## Q8. In what situations might multipath provide little benefit or even hurt performance?

**Answer:**

Multipath may provide little benefit in several situations:

- **One path is much worse:** A slow or unstable path may introduce delay and reordering.
- **Shared bottleneck:** Both paths may ultimately use the same constrained network link, so using two paths does not double the available capacity.
- **Small transfers:** A short transfer may finish before the benefits of establishing and coordinating additional paths become worthwhile.
- **Application-limited traffic:** If the application produces data more slowly than one path can carry it, a second path may not increase throughput.
- **High path-management overhead:** Discovering, maintaining, or coordinating additional paths may cost more than the benefit they provide.
- **Resource constraints:** Extra transmission may consume battery or expensive cellular data without a meaningful performance improvement.

Multipath is not inherently worse in these cases, but its benefits may be limited or its costs may dominate.

**Example:** If a small webpage requires very little data and Wi-Fi already delivers it quickly, activating cellular for the same transfer may add overhead without noticeably reducing loading time.

**Key takeaway:** Multipath is most useful when the additional path contributes meaningful capacity, resilience, or continuity.

---

## Q9. What is a shared bottleneck, and why does it matter for multipath congestion control and fairness?

**Answer:**

A shared bottleneck occurs when two or more paths use the same capacity-limited network resource.

For example, Wi-Fi and cellular may initially appear to provide separate paths, but traffic could later converge on a common constrained link or network resource.

If both paths share a bottleneck, using them simultaneously may not provide the expected increase in total capacity. It may simply send more competing traffic toward the same constrained resource.

Fairness also matters. A multipath connection should not gain an unreasonable advantage over an ordinary single-path TCP connection merely because it uses multiple subflows through the same bottleneck.

Multipath congestion-control algorithms therefore need to consider the relationship between subflows and shared congestion. The exact behavior depends on the congestion-control algorithm and implementation.

**Example:** If two subflows share the same congested router output link, treating them as completely independent flows could allow the multipath connection to take more than a fair share of that link's capacity.

**Key takeaway:** The number of paths does not necessarily equal the number of independent capacity resources; congestion control must consider fairness and shared bottlenecks.

---

## Q10. Distinguish aggregation, failover, and handover.

**Answer:**

These describe three different ways multipath can help an application.

**1. Aggregation**

Multiple paths are used together to increase the resources available for transferring data.

**Example:** Wi-Fi and cellular both carry parts of a large file transfer.

**2. Failover**

Traffic moves to an alternative path when the primary path fails or becomes unusable.

**Example:** A download continues over cellular when Wi-Fi disconnects.

**3. Handover**

Communication transitions from one path or access network to another as connectivity changes, ideally with minimal disruption to the ongoing session.

**Example:** A user leaves Wi-Fi coverage while walking outside, and the connection continues using cellular connectivity.

The terms can overlap in practice. A system may aggregate paths while both are available and rely on failover or handover when one becomes unavailable.

**Key takeaway:** Aggregation seeks to use multiple paths together, failover provides an alternative after failure, and handover supports continuity during a change of network.

---

## Q11. Why might multipath be more useful for long transfers than for short transfers?

**Answer:**

Multipath may require extra work to establish or validate paths, coordinate subflows, schedule data, and manage reordering.

For a short transfer, this additional work may represent a significant fraction of the total transfer time. The transfer might finish before the extra path provides a measurable benefit.

For a long transfer, the setup and coordination costs can be spread across a larger amount of data. If the additional path provides useful independent capacity, aggregation may produce a more noticeable improvement.

However, transfer size alone does not determine whether multipath helps. Path quality, setup timing, congestion, and application requirements also matter.

**Example:** A small request to load a webpage may gain little from adding a second path, whereas transferring a multi-gigabyte file may benefit from sustained use of additional available capacity.

**Key takeaway:** Long transfers have more opportunity to benefit from aggregation, but the benefit depends on whether the additional path contributes useful capacity.

---

## Q12. How do battery consumption and data cost affect multipath decisions?

**Answer:**

Using multiple interfaces may improve connectivity and throughput, but it can also increase resource consumption.

Potential costs include:

- **Battery:** Keeping additional interfaces active and transmitting over them can consume extra energy.
- **Cellular data:** Using cellular alongside Wi-Fi may consume a limited or expensive data allowance.
- **Radio activity:** Additional transmissions and monitoring can increase device activity.
- **Unnecessary traffic:** Probing, duplicate transmission, or reinjection of data can consume resources without directly increasing useful application data.

A multipath policy should therefore consider more than throughput. It may prefer Wi-Fi when available and use cellular as a backup, or use both paths when the application needs higher performance and the user permits the additional cost.

**Example:** A user downloading a large file on a limited mobile-data plan may prefer Wi-Fi-only operation, while a user in an emergency video call may prioritize continuity over cellular-data savings.

**Key takeaway:** Multipath policies should balance performance and reliability against energy use and data cost.

---

## Q13. What is the difference between path management and packet scheduling?

**Answer:**

Path management and scheduling are related but distinct responsibilities.

**Path management** decides which paths are available and usable. It can involve discovering addresses, establishing additional subflows, checking connectivity, and responding to path failure.

**Scheduling** decides how to assign outgoing data to the available paths. Its decisions may consider path RTT, congestion, estimated delivery time, bandwidth, and the risk of reordering.

A protocol can have multiple usable paths but still perform poorly if its scheduler makes bad data-placement decisions.

**Example:**

- Path management establishes a Wi-Fi subflow and a cellular subflow.
- The scheduler decides whether the next data segment should be sent over Wi-Fi or cellular.

If cellular has a much higher RTT, a scheduler that ignores delivery timing may send data that arrives too late to help the application's ordered stream.

**Key takeaway:** Path management decides which paths to use; scheduling decides how to distribute data across those paths.

---

## Q14. How does multipath transport differ from link bonding, network-layer multipath, and application-layer multipath?

**Answer:**

Multipath can be implemented at different layers, and the layer affects what the system can coordinate and what the application must manage.

**1. Link bonding**

Link bonding combines multiple links at a lower network layer, depending on the technology. It may provide redundancy or distribute traffic across links, but its behavior depends on the bonding mechanism and network configuration.

**2. Network-layer multipath**

Network-layer techniques, such as ECMP, select or distribute traffic across network routes. They typically operate through routing and forwarding decisions rather than coordinating one application's transport-level byte stream across subflows.

**3. Transport-layer multipath**

Transport-layer multipath, such as MPTCP, coordinates multiple paths for a logical transport connection. It can manage subflows, transport-level reliability, congestion control, and data scheduling.

**4. Application-layer multipath**

An application can create and manage multiple connections itself. This gives the application control over how it distributes work, but requires application-level logic to coordinate transfers, handle failures, and combine results where needed.

These approaches are not interchangeable. Their suitability depends on the required transparency, deployment environment, failure handling, and performance goals.

**Example:** An application could split a file across several independent connections, while MPTCP can provide a single logical byte stream over multiple TCP subflows.

**Key takeaway:** The layer at which multipath is implemented determines which components coordinate paths and how much complexity is exposed to the application.

---

# Quick Recall - Questions 1-14

Before moving to Part 2, try answering these without looking at the notes.

1. What are the three main benefits of multipath transport?
2. Why are multiple independent TCP connections not equivalent to MPTCP?
3. What are the four fields in a TCP 4-tuple?
4. How do multihoming, ECMP, and multipath transport differ?
5. Why might maximizing throughput conflict with saving battery or cellular data?
6. Name four costs or complications introduced by multipath.
7. Explain the sequence of events through which a second path can reduce useful application throughput.
8. Name three situations in which multipath may provide little benefit.
9. Why can two paths fail to provide twice the capacity?
10. Distinguish aggregation, failover, and handover.
11. Why can a long transfer benefit more from aggregation than a short transfer?
12. What resource costs should a multipath policy consider?
13. Distinguish path management from scheduling.
14. Name four layers or approaches at which multipath-like behavior can be implemented.

## Core Concept to Remember

**Multipath is not simply “more paths = more throughput.”** Its success depends on the capacity and independence of the paths, congestion-control behavior, scheduling, reordering, resilience requirements, and resource costs.
```

After pasting, press **Ctrl + S** in Notepad and close it. Then run this PowerShell command to verify the file was saved\:

```powershell
Get-Content ".\01_Foundations_Q1-28\Q1-14_Why_Multipath.md" -TotalCount 12
```

Once that is saved, we can move to **Q15-28: TCP and Transport Fundamentals** in the same paste-ready format.

## Prompt:
10/27/2026, 12:05:30 AM

done now next

## Response:
10/27/2026, 12:04:38 AM · gpt-6

Next is **Part 2 - TCP and Transport Fundamentals (Q15-28)**\. Save these answers in\:

`01_Foundations_Q1-28\Q15-28_Transport_Fundamentals.md`

This section covers TCP reliability, head-of-line blocking, loss detection, congestion control, flow control, middleboxes, QUIC, and performance metrics. These fundamentals will help you explain why MPTCP and MP-QUIC behave differently.

````markdown

# Part 2 - TCP and Transport Fundamentals
## Questions 15-28 | Tier 1: Core Viva Preparation

## Q15. How does TCP deliver bytes reliably and in order? Explain sequence numbers, ACKs, the retransmission timer, and fast retransmit.

**Answer:**

TCP provides a reliable, ordered byte stream using sequence numbers, acknowledgements, and retransmission.

1. **Sequence numbers:** TCP assigns sequence numbers to bytes in the stream. These numbers allow the receiver to identify which bytes have arrived and which are missing.
2. **Acknowledgements (ACKs):** The receiver acknowledges received data. A cumulative ACK indicates the next byte expected, confirming that preceding bytes have been received in order.
3. **Retransmission timeout (RTO):** The sender maintains a retransmission timer. If the expected acknowledgement does not arrive before the timeout, the sender retransmits the relevant data.
4. **Fast retransmit:** When the sender receives enough duplicate ACKs indicating that a segment may be missing, it can retransmit the segment without waiting for the RTO to expire.

Together, these mechanisms allow TCP to recover from packet loss and present an ordered byte stream to the receiving application.

**Example:** If bytes 1000-1999 arrive but bytes 2000-2999 are missing, the receiver can acknowledge that it is still expecting byte 2000. The sender can retransmit the missing data.

**Key takeaway:** Sequence numbers identify data, ACKs report receipt, the RTO provides timeout-based recovery, and fast retransmit can recover from some losses sooner.

---

## Q16. What is head-of-line blocking in TCP? Which data is blocked, where does it wait, and why is it a consequence of the byte-stream abstraction?

**Answer:**

Head-of-line (HOL) blocking occurs when missing earlier data prevents later-arriving data from being delivered to the application in order.

TCP provides an ordered byte stream. Therefore, even if later bytes have arrived successfully, the receiving application cannot consume them as part of the normal stream until the missing earlier bytes have been recovered.

The later data may be held in the receiver's TCP buffer while TCP waits for the missing data to be retransmitted.

This behavior follows from TCP's ordered byte-stream abstraction: the application receives bytes in sequence rather than independently consumable messages.

**Example:** Suppose a file transfer sends bytes 1-1000, 1001-2000, and 2001-3000. If the middle segment is lost but the last segment arrives, TCP can retain the last segment, but the application cannot receive the complete stream past the missing byte range yet.

This is different from application protocols that can independently process separate messages or streams, although their exact behavior depends on their design.

**Key takeaway:** TCP's ordered byte stream means a missing earlier byte range can delay delivery of later bytes, even when those later bytes have already arrived.

---

## Q17. How does TCP detect loss using RTO, duplicate ACKs, SACK, and RACK? Why is fast retransmit faster than a timeout?

**Answer:**

TCP uses several mechanisms to identify and recover from missing data.

1. **Retransmission timeout (RTO):** If an acknowledgement does not arrive within the retransmission timeout, the sender retransmits data. This provides a fallback when other loss signals are insufficient.
2. **Three duplicate ACKs:** Traditionally, receiving three duplicate ACKs is used as a signal that a segment may have been lost. The sender can perform fast retransmit without waiting for the RTO.
3. **Selective Acknowledgement (SACK):** SACK allows the receiver to report blocks of data received beyond a gap. This gives the sender more detailed information about which data arrived and which may need retransmission.
4. **Recent ACK (RACK):** RACK is a time-based loss-detection mechanism that uses transmission timing and acknowledgements to infer loss. It can detect losses without relying solely on a fixed number of duplicate ACKs.

Fast retransmit can be faster than timeout-based recovery because the sender reacts to evidence of loss before the RTO expires.

However, duplicate ACKs can sometimes result from packet reordering rather than loss, so loss-detection mechanisms must account for network behavior.

**Example:** If a segment is lost but several later segments arrive, the receiver may send duplicate ACKs or SACK information. The sender can use these signals to recover before the retransmission timer expires.

**Key takeaway:** RTO provides timeout-based recovery; duplicate ACKs, SACK, and RACK can provide earlier or more informative loss signals.

---

## Q18. What is the retransmission ambiguity problem in RTT measurement? How do Karn's algorithm and timestamps address it, and why does this matter when comparing TCP with QUIC?

**Answer:**

TCP estimates the round-trip time (RTT) by measuring the time between transmitting data and receiving its acknowledgement.

Retransmission creates ambiguity. If a segment is retransmitted and an ACK subsequently arrives, the sender may not know whether that ACK corresponds to the original transmission or the retransmission. The measured time could therefore be misleading.

**Karn's algorithm** avoids taking RTT samples from retransmitted segments when the sender cannot determine which transmission the ACK acknowledges. This avoids using ambiguous measurements.

**TCP timestamps** add timestamp information to TCP segments and can help disambiguate acknowledgements under the relevant timestamp and PAWS mechanisms. They also support RTT measurement in implementations that use them.

QUIC has its own packet-number and acknowledgement mechanisms. QUIC packet numbers are not reused for retransmitted data in the same way TCP sequence ranges are reused; retransmitted information is sent in new QUIC packets. This makes acknowledgement interpretation and RTT sampling different from traditional TCP retransmission handling.

When comparing TCP and QUIC, it is important to compare their actual RTT-sampling and loss-detection algorithms rather than assuming that they measure or react to RTT identically.

**Example:** If a TCP segment is sent at time 0, retransmitted at time 100 ms, and acknowledged at time 130 ms, the sender cannot necessarily conclude that the RTT was 130 ms or 30 ms. The ACK's relationship to the two transmissions is ambiguous.

**Key takeaway:** Retransmissions complicate RTT measurement. Karn's algorithm avoids ambiguous samples, while timestamps and QUIC's packet-number design provide different mechanisms for interpreting acknowledgements.

---

## Q19. Distinguish the congestion window, receive window, and send window. On a high bandwidth-delay-product path, which can limit throughput?

**Answer:**

These windows serve different purposes.

**1. Congestion window (cwnd)**

The congestion window limits how much unacknowledged data the sender may have in flight based on congestion-control decisions. It helps prevent the sender from overwhelming the network.

**2. Receive window (rwnd)**

The receive window advertises how much additional data the receiver can accept. It supports flow control and protects the receiver from being overwhelmed by data it cannot buffer.

**3. Send window**

The effective sending allowance is constrained by both congestion control and receiver flow control. In a simplified model, the sender's usable in-flight allowance is approximately:

\[
\text{Usable window} = \min(\text{cwnd},\text{rwnd})
\]

Actual TCP sending behavior also depends on data already in flight and other protocol constraints.

**Bandwidth-delay product (BDP)** is the amount of data that can be in flight to fill a path at a given bandwidth and RTT:

\[
\text{BDP} = \text{Bandwidth} \times \text{RTT}
\]

On a high-BDP path, the sender may need a large enough congestion window and receive window to keep the path fully utilized. If either is too small, throughput can be limited.

**Example:** A high-bandwidth path with a large RTT may require several megabytes of in-flight data. A small receive window or congestion window can prevent the sender from filling the path.

**Key takeaway:** The congestion window controls network congestion, the receive window controls receiver flow, and the smaller effective window can limit throughput.

---

## Q20. How do slow start and congestion avoidance (AIMD) work, and why does TCP reduce its window after loss?

**Answer:**

TCP congestion control regulates the amount of unacknowledged data in flight.

**Slow start:** TCP begins with a relatively small congestion window and increases it rapidly as acknowledgements arrive. In the classic description, the congestion window grows approximately exponentially per RTT, until it reaches a threshold or congestion is detected.

**Congestion avoidance:** After the slow-start threshold, TCP typically increases its congestion window more cautiously. Under classic Additive Increase Multiplicative Decrease (AIMD), the window increases gradually and is reduced multiplicatively after a congestion signal.

**Why reduce the window after loss?**

Packet loss can indicate that a network queue or link is congested. Reducing the sending rate helps relieve congestion and allows the network to recover.

However, packet loss is not always caused by congestion, and different congestion-control algorithms interpret signals differently.

**Example:** A classic Reno-style TCP connection increases its congestion window as ACKs arrive. When it detects congestion, it reduces the window to lower the rate of traffic entering the network.

**Key takeaway:** Slow start probes available capacity quickly; congestion avoidance increases more cautiously; congestion signals cause a reduction to help control network load.

---

## Q21. Compare loss-based congestion control (Reno, CUBIC) with model-based congestion control (BBR). How can you check which algorithm your Linux kernel is using?

**Answer:**

Congestion-control algorithms differ in how they estimate network capacity and react to congestion.

**Loss-based approaches: Reno and CUBIC**

- Use packet loss as an important congestion signal.
- Adjust the congestion window in response to ACKs and loss.
- Reno follows the classic AIMD approach.
- CUBIC uses a cubic window-growth function designed to improve performance on high-bandwidth, high-RTT paths.

Loss-based algorithms can achieve high throughput, but when they rely heavily on loss signals, they may build large queues in some network conditions.

**Model-based approach: BBR**

- Estimates bottleneck bandwidth and minimum RTT.
- Uses these estimates to control sending rate and in-flight data.
- Attempts to operate near the path's estimated delivery capacity without relying on packet loss as its primary congestion signal.

BBR's behavior depends on its version and implementation. It is not accurate to say that BBR never responds to loss or that it always eliminates queueing.

### Check the algorithm on Linux

Run these commands in a Linux terminal or WSL Ubuntu shell:

```bash
sysctl net.ipv4.tcp_congestion_control
sysctl net.ipv4.tcp_available_congestion_control
```

The first command displays the default congestion-control algorithm. The second lists algorithms available in the running kernel.

For example, the default might be `cubic`, but the actual output on your machine may differ.

To inspect the algorithm for an individual TCP socket, where supported, use tools such as `ss -ti` and inspect the TCP information for the connection.

**Important:** The Linux default TCP algorithm does not automatically tell you which algorithm a particular MPTCP or QUIC experiment uses. Verify the transport implementation and configuration used in your experiment.

**Key takeaway:** Reno and CUBIC are loss-based approaches, while BBR estimates bandwidth and RTT. Always verify the algorithm in the actual experimental environment.

---

## Q22. How does bufferbloat affect throughput and latency? How can an emulated link's queue length distort results?

**Answer:**

Bufferbloat occurs when excessive buffering in network devices creates large queues and high delays, particularly under sustained congestion.

A buffer can absorb temporary bursts and help keep a link busy. However, an excessively large queue may allow packets to wait for a long time before transmission.

This can cause:

- **High latency:** Packets spend more time waiting in queues.
- **Increased jitter:** Queueing delay changes over time.
- **Potentially misleading throughput results:** A large queue can temporarily absorb bursts or sustain high utilization while producing poor interactive performance.
- **Slower congestion response:** Queued packets may delay feedback about changing network conditions.

A queue that is too small can also cause unnecessary packet drops and reduce throughput, so the goal is not simply to minimize buffer size.

In an emulated network, queue length is an experimental parameter. A large queue may hide some short-term effects, while a small queue may create more loss. Either choice can change how TCP, MPTCP, or QUIC behaves.

**Example:** An emulated link may report high throughput while a large queue adds hundreds of milliseconds of waiting time. A throughput-only comparison would miss this degradation.

**Key takeaway:** Queue length affects delay, loss, and congestion feedback. Control and report it when comparing transport protocols.

---

## Q23. How is flow control different from congestion control, and which TCP header field carries each?

**Answer:**

Flow control and congestion control protect different resources.

**Flow control**

Flow control prevents the sender from overwhelming the receiver. The receiver advertises its available buffer capacity through the TCP **Window** field, commonly called the receive window (`rwnd`).

**Congestion control**

Congestion control prevents the sender from injecting more traffic than the network can handle. It uses congestion-control state maintained by the sender, including the congestion window (`cwnd`).

The congestion window is not directly advertised in a TCP header field. Instead, it is an internal sender-side control variable.

**Example:** A receiver may have plenty of buffer space, but the network may be congested. In that case, the congestion window may limit sending. Conversely, the network may have spare capacity, but a receiver with a small advertised window may limit the data in flight.

**Key takeaway:** Flow control protects the receiver and uses the advertised TCP Window field; congestion control protects the network and uses sender-side congestion-control state.

---

## Q24. What changes when the path under a connection changes? Which transport state must be reset, and which can be kept?

**Answer:**

A path change can alter several network properties:

- **RTT:** The new path may have a different propagation and queueing delay.
- **Bandwidth:** Available capacity may be higher or lower.
- **Loss and reordering:** Packets may be lost or arrive in a different order.
- **MTU:** The maximum packet size supported by the path may change.
- **Middleboxes:** NATs, firewalls, and other devices may treat the new path differently.
- **Address and connectivity:** The device may use a different source address or network interface.

These changes can make existing transport estimates inaccurate.

For example, congestion control may need to adapt its sending rate and congestion window. RTT estimators, loss-detection state, and path-MTU information may also need to be updated or revalidated.

Not all connection state must be discarded. A multipath protocol may preserve the logical connection's identity, application data, and relevant connection-level reliability state while maintaining separate state for each subflow or path.

The exact state retained or reset depends on the protocol and implementation. A conventional TCP connection generally cannot simply change its IP address and continue as though nothing happened; MPTCP provides mechanisms to support additional subflows and address changes.

**Example:** If Wi-Fi fails and a device continues through cellular using a supported multipath connection, the protocol may preserve the logical data stream while adapting to cellular's different RTT and capacity.

**Key takeaway:** A path change requires adaptation of path-dependent state, but a multipath protocol may preserve higher-level connection continuity.

---

## Q25. What are middleboxes, and how can they break protocols? How did this influence MPTCP and QUIC?

**Answer:**

Middleboxes are network devices that perform functions beyond basic packet forwarding. Examples include:

- **NATs:** Translate network addresses and often transport-layer ports.
- **Firewalls:** Filter traffic according to security rules.
- **Proxies:** Intercept or relay connections.
- **Performance-enhancing proxies (PEPs):** Modify or split transport behavior to improve performance in certain environments.

Middleboxes may expect traffic to follow familiar protocol patterns. If they encounter unfamiliar TCP options, new protocol behavior, or unexpected address changes, they may drop, modify, or mishandle packets.

For example, a middlebox that does not correctly handle a new TCP option may prevent a connection from using the feature that depends on it. Devices that rewrite TCP sequence numbers or terminate connections can also complicate extensions that expect end-to-end transport behavior.

**MPTCP:** MPTCP extends TCP and uses TCP options for its connection-management and data-coordination mechanisms. Compatibility with middleboxes is therefore an important deployment concern. MPTCP includes mechanisms designed to work within the constraints of the TCP ecosystem, but support and behavior vary across networks.

**QUIC:** QUIC runs over UDP and encrypts much of its transport control information. This reduces dependence on exposing transport internals to middleboxes and helps avoid some forms of protocol ossification. However, UDP blocking, filtering, and other network policies can still affect QUIC.

**Key takeaway:** Middleboxes can interfere with protocol evolution. MPTCP extends TCP, while QUIC uses UDP and extensive encryption to reduce some compatibility and ossification problems.

---

## Q26. What is a TCP 4-tuple, how does NAT rewrite it, and why can a server usually not initiate a connection to a client behind NAT?

**Answer:**

A TCP 4-tuple consists of:

1. Source IP address
2. Source port
3. Destination IP address
4. Destination port

NAT (Network Address Translation) modifies address information as packets cross a network boundary. In common home-network setups, port address translation may also rewrite source ports.

For example, a private device may send traffic from `192.168.1.10:50000` to a public server. The NAT device may translate the source to a public address and a different port. It records mapping state so that returning traffic can be forwarded to the correct internal device.

A server usually cannot initiate a new connection directly to a client behind a typical NAT because the server does not have a usable mapping to that internal address and port, and unsolicited incoming traffic may be blocked by the NAT or firewall.

There are exceptions, including explicit port forwarding, suitable NAT mappings, and traversal techniques.

**Example:** A laptop behind a home router opens a TCP connection to a public website. The router creates a mapping for the outgoing connection, allowing the website's response to return through that mapping. The website generally cannot open an unrelated inbound connection directly to the laptop without additional configuration or traversal support.

**Key takeaway:** NAT changes address/port information and maintains mappings. Outgoing connections commonly work because they establish state that allows the replies to return.

---

## Q27. What is protocol ossification, and why does QUIC run over UDP and encrypt almost everything?

**Answer:**

**Protocol ossification** occurs when network infrastructure becomes dependent on the details of existing protocol behavior. As a result, protocol changes that should be valid may fail because middleboxes or other devices assume that the protocol will never change.

For example, a network device may drop packets containing an unfamiliar TCP option. This can make it difficult to deploy new transport features even when the endpoints support them.

QUIC addresses some of these problems by:

1. **Running over UDP:** UDP provides a widely deployed datagram substrate without requiring the transport to extend TCP itself.
2. **Encrypting most transport control information:** This limits the ability of on-path devices to inspect or depend on many internal transport details.
3. **Supporting transport evolution:** QUIC can introduce and evolve transport features without requiring every network device to understand those features.

QUIC still exposes some information needed for network operation, and its use of UDP does not guarantee compatibility with every network. UDP blocking and restrictive firewall policies can still prevent connections.

**Example:** A network device that expects familiar TCP behavior may mishandle an unfamiliar TCP extension. QUIC's use of UDP and encryption reduces some of these opportunities for interference.

**Key takeaway:** QUIC uses UDP and encryption to reduce dependence on middlebox assumptions and make transport evolution easier, but it cannot eliminate every deployment problem.

---

## Q28. How do throughput, goodput, latency, jitter, and packet loss differ? Which metrics matter most for video streaming, bulk transfer, and VoIP?

**Answer:**

These metrics describe different aspects of network performance.

**1. Throughput**

The rate at which data is transferred over a link or connection, often measured in bits per second. Depending on the measurement method, it may include protocol overhead or retransmitted data.

**2. Goodput**

The rate of useful application data delivered successfully, excluding retransmitted data and protocol overhead from the useful-data count.

**3. Latency**

The time required for data to travel from a sender to a receiver. RTT measures the time for a signal to travel to the other endpoint and for a response to return.

**4. Jitter**

Variation in packet delay. Even if average latency is acceptable, high jitter can make real-time applications harder to support.

**5. Packet loss**

The fraction or number of packets that fail to reach their intended destination. Loss may trigger retransmissions and can be especially harmful to real-time media.

### Which metrics matter for different applications?

| Application | Important metrics | Reason |
|---|---|---|
| Video streaming | Goodput, throughput, latency, and loss | Sufficient sustained goodput supports video quality; latency affects startup and live-stream delay, while loss can disrupt delivery. |
| Bulk file transfer | Goodput and completion time | The goal is to deliver the entire file correctly and efficiently. |
| VoIP and interactive calls | Latency, jitter, and loss | Delayed or irregular packets and lost audio can directly harm conversation quality. |

The relative importance depends on the application. Live interactive video, for example, places greater emphasis on latency than ordinary on-demand video streaming.

**Example:** A file download may finish correctly despite retransmissions, but a voice call cannot always wait for lost packets to be retransmitted because the audio may arrive too late to be useful.

**Key takeaway:** Throughput measures transfer rate, goodput measures useful delivery rate, latency measures delay, jitter measures delay variation, and packet loss measures delivery failures.

---

# Quick Recall - Questions 15-28

Try to answer these without looking at the notes.

1. What do TCP sequence numbers and ACKs do?
2. Why does TCP experience head-of-line blocking?
3. What is the difference between RTO and fast retransmit?
4. Why can a TCP retransmission make RTT measurement ambiguous?
5. What are `cwnd`, `rwnd`, and BDP?
6. How do slow start and congestion avoidance differ?
7. What is the main distinction between loss-based congestion control and BBR?
8. Why can a large network queue cause bufferbloat?
9. Which mechanism protects the receiver, and which protects the network?
10. Which path properties may change during a handover?
11. How can middleboxes interfere with transport protocols?
12. Why does NAT commonly allow replies to outgoing connections but block unsolicited inbound connections?
13. What is protocol ossification?
14. Which performance metrics matter most for bulk transfer and VoIP?

## Core Concepts to Remember

- TCP provides a reliable, ordered byte stream.
- Loss recovery and RTT measurement affect transport performance.
- Congestion control and flow control solve different problems.
- A path change can invalidate path-specific performance estimates.
- Middleboxes influence how transport protocols can evolve and be deployed.
- Performance comparisons require more than throughput alone: measure goodput, latency, jitter, and loss as appropriate.
````

## Save and verify

1\. Open the file in Notepad\:

```powershell
notepad ".\01_Foundations_Q1-28\Q15-28_Transport_Fundamentals.md"
```

2. Paste all the content above and press **Ctrl + S**\.
3. Close Notepad and run\:

```powershell
Get-Content ".\01_Foundations_Q1-28\Q15-28_Transport_Fundamentals.md" -TotalCount 12
```

Once saved, **Part 1 and Part 2 (Q1-28) will be complete in your notes**\. Next, we should move to the next shared section in your plan: **Part 10, Q177-190 - Applications and Recommendations**, which you lead, while keeping your assigned research and congestion-control sections in the overall project plan.

## Prompt:
10/28/2026, 10:59:40 AM

Done now let's move ahead

## Response:
10/28/2026, 10:59:44 AM · gpt-6

> **Remembering**
>
>
> ****
>
> 
>
> **Identified and sequenced your project responsibilities and team tasks**
>
> 
>
> Worked for 37s

We’ll continue with your **older full plan**\. One correction to my previous message: after the shared foundation (Q1-28), your next assigned block is **Part 9 - Existing Research and How to Read It (Q159-176)**\. Part 10 (Q177-190), which you lead, comes next in the study sequence.

For Part 9, the plan has an important rule: **never quote a research result without identifying the implementation, network setup, and workload behind it.** We’ll distinguish published findings from conclusions we infer ourselves.

Save this block in `05_Research_Q159-176\Research_Answers.md`\.

## Part 9 - Research answers (Q159-176)

Research sources checked include the CoNEXT 2017 MPQUIC paper, the 2019 MultipathTester study, RFC 8041, and the 2021 MPTCP adoption study. \[[Multipath QUIC: Design and Evaluation](https://inl.info.ucl.ac.be/publications/historical/2017-multipath-quic-design-and.html?utm_source=chatgpt.com); [rfc-editor.org](https://www.rfc-editor.org/rfc/rfc8041.html?utm_source=chatgpt.com); [MultipathTester: Comparing MPTCP and MPQUIC in Mobile Environments](https://research.dial.uclouvain.be/entities/publication/df3c61de-630b-4b8a-9a75-355470f97252?utm_source=chatgpt.com); [From Single Lane to Highways: Analyzing the Adoption of Multipath TCP in the Internet](https://arxiv.org/abs/2106.07351?utm_source=chatgpt.com)\]

```markdown

# Part 9 - Existing Research and How to Read It
## Questions 159-176 | Swamini's Assigned Section

> **Evidence rule:** Never quote a performance number without recording the implementation, version, topology, path conditions, workload, and metric. If a detail has not been verified from the original paper, mark it as "not verified."

## Q159. What research questions dominate MPTCP and MP-QUIC evaluations? Which question does each paper address?

**Answer:**

Research on multipath transport commonly investigates five questions:

1. **Aggregation:** Can multiple paths increase useful throughput compared with the best single path?
2. **Handover and resilience:** Can a connection continue when a path fails or changes?
3. **Scheduling:** How do different scheduling algorithms perform when paths have unequal RTTs, bandwidths, or loss rates?
4. **Fairness:** Can multipath traffic coexist fairly with ordinary single-path TCP traffic?
5. **Deployment:** Can the protocol work through real networks, middleboxes, NATs, and mobile interfaces?

Examples from the literature:

- **De Coninck and Bonaventure, CoNEXT 2017, "Multipath QUIC: Design and Evaluation":** Studies multipath QUIC design and compares its performance with TCP and MPTCP.
- **De Coninck and Bonaventure, MultipathTester, 2019:** Studies MPTCP and MPQUIC under mobile-network conditions, including stable traffic patterns and Wi-Fi-to-cellular handovers.
- **Aschenbrenner et al., "From Single Lane to Highways," 2021:** Studies Internet deployment and adoption of MPTCP, including false positives caused by middleboxes.

For every paper in the literature matrix, identify its main research question rather than treating every paper as a general protocol comparison.

**Key takeaway:** A study's conclusions are meaningful only in relation to the question it actually tested.

---

## Q160. For each study, record the implementation and version, emulator, path parameters, workload, metrics, congestion control, and scheduler. Why is every field needed?

**Answer:**

Every study should have a structured record containing:

| Field | Why it matters |
|---|---|
| Protocol and implementation | Different implementations can behave differently. |
| Version, commit, or draft | Protocol behavior and algorithms evolve over time. |
| Platform or emulator | A real phone, Linux host, and Mininet topology have different constraints. |
| Topology | Determines whether paths are independent or share bottlenecks. |
| Path bandwidth and RTT | Influence capacity, delay, and scheduling decisions. |
| Packet loss and queue size | Affect loss recovery, queueing, and goodput. |
| Workload | Bulk transfer, video, and interactive traffic have different requirements. |
| Metrics | Throughput, goodput, latency, jitter, and completion time measure different outcomes. |
| Congestion control | Changes the sending rate and response to congestion. |
| Scheduler | Changes which path carries data and how much reordering occurs. |
| Repetitions and duration | Help assess variability and reproducibility. |

Without these details, two results may look comparable but actually describe different experimental conditions.

**Example:** A throughput result from an old research version of MPQUIC cannot automatically be compared with a modern implementation running a different draft and scheduler.

**Key takeaway:** The experiment setup is part of the result, not optional background information.

---

## Q161. Which implementations did the CoNEXT 2017 MPQUIC paper use, and what does that imply for applying its results today?

**Answer:**

The paper *Multipath QUIC: Design and Evaluation* by Quentin De Coninck and Olivier Bonaventure introduced MPQUIC as an extension of the `quic-go` implementation. It evaluated that research prototype alongside TCP and MPTCP.

This was an early research implementation, based on the QUIC design of that period. It is not the same as a modern implementation of the evolving IETF multipath QUIC draft.

The distinction matters because protocol details, loss recovery, packet-number handling, scheduling, congestion control, and implementation maturity may have changed.

Before quoting a specific MPTCP version or kernel configuration from the paper, verify it in the paper's experimental-method section.

**Key takeaway:** The 2017 paper is valuable evidence about its prototype and experimental setup, but its numerical results should not be presented as measurements of today's MP-QUIC draft.

---

## Q162. What did the 2017 paper find with and without packet loss? Which QUIC features might explain the lossy-network result?

**Answer:**

The authors report that, without packet loss, single-path TCP and single-path QUIC had similar performance in their evaluated settings, while MPQUIC could outperform MPTCP.

For lossy scenarios, they report that QUIC and MPQUIC were better suited to the tested conditions than TCP and MPTCP.

The paper discusses the greater frequency of head-of-line blocking in MPTCP under heterogeneous path conditions. Its analysis also describes how slow-path scheduling and opportunistic retransmission can affect useful throughput.

A relevant design difference is that QUIC implements transport reliability and loss recovery above UDP, with packet-number and acknowledgement mechanisms distinct from TCP's. However, attributing the paper's result to one specific feature alone would require further evidence from the paper's experiments.

**Important limitation:** These are findings from the paper's tested prototype, workloads, and network conditions-not a guarantee that MPQUIC always outperforms MPTCP.

**Key takeaway:** The 2017 results suggest that loss recovery and cross-path blocking can substantially affect comparisons, so the tested conditions must accompany every claim.

---

## Q163. What did MultipathTester (MNM 2019) study, and why can phone measurements differ from Mininet measurements?

**Answer:**

MultipathTester, by Quentin De Coninck and Olivier Bonaventure, was presented at the 3rd Workshop on Mobile Network Measurement in 2019.

The authors developed an iOS application to compare iOS MPTCP with a research implementation of MPQUIC under different traffic patterns and network conditions.

The platform examined stable-network traffic and handovers, including transitions from Wi-Fi to cellular connectivity.

A real-phone measurement can differ from Mininet because the phone uses real wireless interfaces and carrier networks. It may experience changing radio conditions, handover delays, cellular scheduling, energy-management policies, and background system activity.

Mininet is useful for controlled experiments because the researcher can configure virtual topology and network parameters. However, a virtual emulation does not automatically reproduce all real-radio and mobile-network behavior.

**Key takeaway:** Use emulation to isolate causes and real devices to study deployment effects. Neither platform alone answers every question.

---

## Q164. What do MPTCP deployment scans show, and why can hosts that merely echo TCP options create false positives?

**Answer:**

The 2021 study *From Single Lane to Highways: Analyzing the Adoption of Multipath TCP in the Internet* examined MPTCP deployment through Internet-wide scans and traffic measurements.

The authors reported thousands of apparently MPTCP-capable IPv4 hosts, along with a much smaller number of IPv6 hosts. They also found that some apparent positives resulted from middleboxes mirroring TCP options rather than from genuine MPTCP support at the endpoint.

This creates a measurement problem: observing a response that contains an MPTCP-related option does not, by itself, prove that the endpoint implements the full protocol correctly.

A stronger verification approach checks whether the endpoint completes the relevant MPTCP handshake and demonstrates the expected protocol behavior.

The paper also reported that MPTCP traffic remained a small share of observed traffic despite growth in its use.

**Key takeaway:** Protocol capability must be verified through behavior, not inferred solely from a matching packet field.

---

## Q165. What does RFC 8041 report about MPTCP use cases and operational experience?

**Answer:**

RFC 8041, *Use Cases and Operational Experience with Multipath TCP*, is an Informational IETF document published in January 2017.

It describes MPTCP use cases and practical deployment lessons, drawing on experience with implementations and real networks.

The document discusses use cases including:

- Datacenters, where multiple network paths can improve capacity utilization.
- Cellular/Wi-Fi offload, where multiple interfaces can support continuity or make use of available connectivity.
- MPTCP proxies and other operational deployment arrangements.

It also discusses middlebox interference, congestion control, subflow management, packet scheduling, segment-size selection, and operational issues such as captive portals.

The document is not a guarantee that every use case benefits equally. Outcomes depend on the network, implementation, and policy.

**Key takeaway:** RFC 8041 is useful for understanding practical deployment challenges and operational experience, not just the protocol's theoretical capabilities.

---

## Q166. Which research introduced opportunistic retransmission with penalisation, BLEST, and ECF? What problem did each address?

**Answer:**

These mechanisms address scheduling and recovery problems that arise when MPTCP uses paths with different performance characteristics.

- **Opportunistic Retransmission and Penalisation (ORP):** Allows data to be retransmitted over an alternative subflow under certain conditions, while penalising a subflow when its behavior suggests that continued scheduling could be harmful.
- **BLEST:** A scheduler designed to reduce receiver-side head-of-line blocking by estimating whether sending data over a slower path is likely to delay delivery of data arriving over a faster path.
- **ECF:** A scheduler proposed to improve data-placement decisions by accounting for path characteristics and the impact of scheduling on delivery performance.

The important distinction is that schedulers do not change the physical properties of the paths. They attempt to make better use of the available paths by changing where data is sent.

For your literature matrix, verify the original paper, author list, year, algorithm name, and evaluation conditions before attributing a specific numerical improvement to any of these mechanisms.

**Key takeaway:** Scheduling research tries to manage the trade-off between path utilization and the delay caused by out-of-order delivery.

---

## Q167. State three published findings about when multipath aggregates well or badly, and the conditions each depends on.

**Answer:**

**Finding 1 - Multiple paths can improve capacity utilization.**

RFC 8041 discusses datacenter research in which multiple MPTCP subflows can improve utilization of available paths. The benefit depends on whether the paths offer additional usable capacity and how traffic is distributed across them.

**Finding 2 - Heterogeneous paths can reduce the benefit of aggregation.**

The CoNEXT 2017 MPQUIC study describes cases where MPTCP experiences more head-of-line blocking than MPQUIC under heterogeneous path conditions. The result depends on the evaluated implementation, path characteristics, and scheduler behavior.

**Finding 3 - Packet loss can change the relative performance of transports.**

The same CoNEXT study reports that QUIC-based transports were better suited than TCP-based transports in its lossy scenarios. This is a result of the tested setup, not a universal ranking of all QUIC and TCP implementations.

For each finding, your matrix should record the exact paper, implementation, workload, topology, metric, and limitations.

**Key takeaway:** Multipath benefits are conditional; independent capacity, path heterogeneity, and loss can change the result.

---

## Q168. What do studies report about handover and failover, and what is a common cause of a stall?

**Answer:**

Multipath transport can help maintain a logical connection when connectivity changes, but seamless recovery is not automatic.

A handover can introduce a stall if the old path stops delivering data before the alternative path is usable or before the sender successfully schedules data over it.

Other possible causes include:

- Delayed detection of the failed path.
- Time needed to establish or validate an alternative path.
- Retransmission and loss-recovery delays.
- Data arriving out of order across paths.
- A scheduler continuing to send data over a path that is no longer useful.

The exact cause must be established from the particular study's packet traces, logs, or time-series measurements. Do not claim that one cause is universally the most common unless the cited evidence establishes that.

**Example:** During a Wi-Fi-to-cellular transition, the connection may remain logically alive while delivery pauses because data in the old path has not yet been recovered or the new path has not started carrying useful data.

**Key takeaway:** To evaluate failover, measure interruption duration and recovery behavior-not merely whether the connection eventually survives.

---

## Q169. How do schedulers change results in published studies? Give one number together with its setup.

**Answer:**

Schedulers influence which path carries each piece of data. This affects throughput, reordering, buffering, and completion time.

A round-robin scheduler distributes data across paths in turn. A lowest-RTT scheduler prefers the path with the smallest measured RTT. More specialized schedulers try to avoid sending data over a slower path when doing so could delay ordered delivery.

The CoNEXT 2017 paper reports that, in its considered scenarios, QUIC outperformed TCP in 89% of the scenarios. The paper also discusses how MPTCP's head-of-line blocking and scheduling behavior contributed to performance differences.

**Do not interpret the 89% figure as a general scheduler improvement.** It describes the paper's comparison across its particular scenarios, not a universal result for modern implementations.

Before using the number in a presentation, extract the exact scenario set, baseline implementations, metrics, and relevant figure or table from the original paper.

**Key takeaway:** A scheduler result is meaningful only when the workload, paths, baseline, and metric are specified.

---

## Q170. How do studies treat short versus long flows, and what does this imply for video, file transfer, and VoIP?

**Answer:**

Short and long flows respond differently to multipath overhead.

**Short flows:** Path setup, initial congestion-control behavior, and scheduling overhead may account for a large fraction of the transfer. The transfer may finish before aggregation provides a substantial benefit.

**Long flows:** They provide more time to exploit additional capacity, provided the paths offer useful independent resources and the scheduler controls reordering effectively.

Application implications:

- **Video streaming:** Sustained goodput matters, but startup delay, rebuffering, and segment deadlines also matter.
- **File transfer:** Goodput and completion time are often the primary objectives.
- **VoIP:** Latency, jitter, and packet loss usually matter more than maximum throughput.

These are transport and application-level expectations. For a claim about a particular paper's findings, check which flow sizes and workloads the authors actually tested.

**Key takeaway:** The right multipath strategy depends on the traffic pattern and application objective, not just available bandwidth.

---

## Q171. Which limitations do research papers report, and which matter most for this project?

**Answer:**

Common limitations to look for include:

- **Emulation-only testing:** Controlled conditions may not reproduce real wireless behavior.
- **One implementation:** Results may depend on a particular codebase or version.
- **Older protocol versions:** Early QUIC or MPQUIC prototypes may not reflect later designs.
- **Limited path diversity:** Two paths may not represent networks with more interfaces or complex bottlenecks.
- **Limited workloads:** Bulk transfer results may not predict video or voice performance.
- **Few repetitions:** Results may be sensitive to random variation or transient congestion.
- **Restricted metrics:** Throughput alone cannot establish application quality or handover smoothness.

For this project, the most important limitation is likely **implementation and protocol-version comparability**, especially when contrasting an older MPQUIC research prototype with a newer implementation. Emulation versus real-network differences are also important if the project makes claims about mobile deployment.

The final choice should reflect your actual experiment and the limitations stated by the papers you include.

**Key takeaway:** A good literature review identifies where a result is trustworthy and where its generalization is limited.

---

## Q172. Does QUIC need multipath if QUIC connection migration already exists? Explain both sides.

**Answer:**

Connection migration and multipath address related but different problems.

**Argument that migration may be enough:**

- A connection can move to a new network path when the old path becomes unavailable.
- Only one path may be needed for many applications.
- Using one active path may avoid cross-path reordering and the added complexity of coordinating several paths.

**Argument for multipath:**

- Migration does not, by itself, aggregate the capacity of several paths simultaneously.
- Multiple paths can provide resilience while the original path is still usable.
- Simultaneous path use may increase throughput or improve continuity when path conditions change.

**Trade-offs:**

Multipath introduces scheduling, path-management, congestion-control, and reordering challenges. Migration alone offers a simpler model but does not provide simultaneous path aggregation.

The right choice depends on the application and network conditions. A bulk transfer may benefit from aggregation, while a low-rate application may need only reliable migration or backup connectivity.

**Key takeaway:** Migration supports moving a connection; multipath can support using several paths together. The added capability is valuable only when its benefits justify its costs.

---

## Q173. Classify published results as directly comparable, qualitatively relevant, or not comparable with our experiment.

**Answer:**

Use three categories.

**Directly comparable**

A study uses a sufficiently similar protocol implementation and version, path configuration, workload, metric definition, and baseline. Differences must be small enough that the results answer the same question.

**Qualitatively relevant**

A study investigates the same general mechanism or failure mode but uses a different implementation, workload, or environment. It can explain expected behavior but should not be treated as a numerical benchmark for our experiment.

**Not comparable**

The study's protocol, metric, setup, or workload differs so substantially that numerical comparison would be misleading.

For each paper, record:

- Protocol and version.
- Topology and path conditions.
- Workload.
- Metric definition.
- Congestion control and scheduler.
- Main limitation.

Then assign the category and explain why.

**Key takeaway:** Comparability must be justified field by field; it should not be inferred merely because two papers study multipath transport.

---

## Q174. Why can we not compare a throughput result from a 2017 quic-go fork with a picoquic or quiche run today?

**Answer:**

The implementations may differ in several ways:

1. Protocol draft or version.
2. Loss-detection and recovery algorithms.
3. Packet-number and acknowledgement handling.
4. Congestion-control algorithm and configuration.
5. Multipath scheduling behavior.
6. Path-management and connection-migration behavior.
7. Runtime, compiler, and platform.
8. Socket buffers, offloads, and other system settings.
9. Workload, topology, and measurement method.

A difference in throughput could therefore arise from the protocol design, the implementation, or the experiment setup.

A fair comparison should align the conditions as closely as possible and report unavoidable differences.

**Key takeaway:** Protocol names alone do not establish experimental equivalence. Version and configuration are essential.

---

## Q175. Why are throughput and goodput sometimes confused between papers, and how can that mislead?

**Answer:**

Throughput and goodput are related but not identical.

- **Throughput** measures the rate of data transferred according to the study's definition. It may include retransmissions or protocol overhead, depending on how it is measured.
- **Goodput** measures useful application data successfully delivered, excluding retransmitted data and protocol overhead from the useful-data count.

This distinction is particularly important for multipath protocols.

For example, a redundant scheduler may send duplicate copies of data over different paths. The amount of transmitted traffic can increase even if the amount of unique application data delivered does not increase proportionally.

Similarly, retransmissions can increase network traffic without increasing the quantity of unique data received by the application.

Before comparing results, verify how the authors calculate the metric and whether they measure bytes at the transport, network, or application layer.

**Key takeaway:** A higher transmission rate does not necessarily mean a higher useful-data delivery rate.

---

## Q176. How would you reproduce one published result on a smaller scale? What counts as reproduced, partly reproduced, or not reproducible?

**Answer:**

Choose one specific finding from a published paper and reproduce its essential conditions.

**Step 1 - Select the claim**

For example, investigate whether unequal path RTTs can cause reordering and reduce useful application throughput.

**Step 2 - Record the original setup**

Extract the protocol implementation and version, topology, path bandwidth, RTT, loss, queue settings, workload, scheduler, congestion control, and measurement method.

**Step 3 - Implement the smallest meaningful experiment**

Create the closest feasible topology and run the selected protocols under the specified conditions. Keep the workload and metric definition consistent.

**Step 4 - Collect evidence**

Save configuration files, commands, software versions, raw measurements, logs, and packet captures where appropriate. Repeat runs to assess variability.

**Step 5 - Compare the result**

- **Reproduced:** The central finding appears under sufficiently similar conditions, within a reasonable tolerance.
- **Partly reproduced:** The main trend appears, but some conditions differ or only part of the result is confirmed.
- **Not reproduced:** The expected finding does not appear under the attempted conditions.
- **Not reproducible with this setup:** Required software, data, hardware, or experimental conditions cannot be recreated.

A result that differs from the paper is not automatically a failure. It may reveal a setup difference, implementation difference, or limitation in the original result's generality.

**Key takeaway:** Reproducibility requires documented conditions and evidence, not merely obtaining a similar-looking graph.
```

## What to do now

1\. Open your file\:

```powershell
$base = Join-Path $env:USERPROFILE "Documents\MPTCP_MPQUIC_Swamini"
Set-Location $base
notepad ".\05_Research_Q159-176\Research_Answers.md"
```

2. Paste the full block and press **Ctrl + S**\.
3. Keep the source references and verification warnings intact. In particular, do not present the CoNEXT 2017 results as a modern MP-QUIC benchmark.

The next step after Part 9 is your **Part 16 - Congestion Control, Fairness and Scheduling Theory (Q265-279)**, which is a Tier 1 section for you.

## Prompt:
10/29/2026, 4:46:02 PM

this is what claude gave for the research part, analyze it and then give correct content to paste in our files made , final ready to put in files proper all deliverables correct, then will move forward ahead as discudssed by finishing the parts given here - its long so ill share in two parts, first now im attaching first part, then ill upload the second part after that you work - here is the first part # Research block: Part 9 (Q159–176) and Part 18 (Q291–297)

**Owner:** Swamini · **Project:** MPTCP vs MP-QUIC understanding plan · **Prepared:** Thu 29 Oct 2026 · **Status:** Draft v1, ready for your verification pass

---

## 0. Read this first

**What this file is.** Written answers to Q159–176 and Q291–297, the literature matrix (Q160 columns), a timeline (Q291), cross-training cards, a one-page guide, a gap list, and a teach-back script. Every answer follows the plan's four beats: **What / Why / Cost or caveat / Check**.

**How the evidence was gathered.** I opened the sources in this session. Each source carries a tag so you know how far to trust it:

| Tag | Meaning |

| --- | --- |

| **[F]** | Full text opened and read in this session |

| **[A]** | Abstract or landing page only. Numbers come from the abstract; the body is not checked |

| **[S]** | Second-hand: described in a document I did read (for example RFC 8041 describing another paper) |

| **[M]** | From memory, not re-checked. Treat as "not verified" until you confirm it |

**The rule for numbers (plan Part 9).** No number appears without its implementation, topology and workload. Each number carries a setup tag (S1, S2…) that points to the setup cards in §2, plus a short inline reminder.

**Please do not hand this in as-is.** The viva rewards reasons and honest "not verified". Open the sources marked **[A]**, **[S]** and **[M]** (listed in §7), check the page or figure numbers I could not give, and rewrite each answer in your own words. Part 9 is Tier 2, so you may need a minute to think. Part 18 is Tier 3, so a one-line answer plus "where to look" is enough.

**If you are short on time (plan §10 cut order).** Do these in order, and stop when time runs out:

1. §3 cross-training cards (Q167, Q168, Q172) — these are Tier 1 for everyone.

2. Q161, Q162, Q164, Q166 (the named papers Sir may ask about).

3. Q169, Q171, Q173–176.

4. Part 18 last (Tier 3): Q291, Q293, Q297 first.

**Scope note.** BALIA (Peng et al.), Chiu and Jain (1989), DASH and the ITU E-model belong to Parts 16–17, not to Parts 9 and 18. BALIA appears here only as RFC 8041 describes it.

### Deliverables checklist

| Deliverable | Where |

| --- | --- |

| Written answers Q159–176 | §4 |

| Written answers Q291–297, including the timeline | §5 |

| Literature matrix (Q160 columns) | §2 |

| Cross-training cards Q167, Q168, Q172 | §3 |

| One-page technical guide for this block | §6 |

| Gap list (what I could not verify) | §7 |

| 10-minute teach-back script and cold questions | §8 |

| Source list | §9 |

---

## 1. Facts re-checked from plan §3 (checked 29 Oct 2026)

| Plan statement | Result | Evidence |

| --- | --- | --- |

| MP-QUIC is not an RFC; draft-21 of 17 Mar 2026 | **Confirmed, with a caution.** The datatracker page I opened shows draft-21 as the latest version, an "Active Internet-Draft", intended status Proposed Standard, no RFC number. The page lists an expiry of 18 Sep 2026, which has already passed, so check for a -22 or an RFC Editor entry before you write a status in a report. I could not confirm RFC-Editor-queue state. The title is now "Managing multiple paths for a QUIC connection" | draft-ietf-quic-multipath-21 **[F]** |

| "RFC 9443" is MP-QUIC | **False.** RFC 9443 is "Multiplexing Scheme Updates for QUIC" (July 2023). It updates the RTP/DTLS/STUN demultiplexing rules (RFC 7983, RFC 5764) and has nothing to do with multipath | rfc-editor.org info/rfc9443 **[F]** |

| Drafts drift (`enable_multipath` → `initial_max_path_id`) | **Confirmed.** Draft-21's registry text shows `enable_multipath` provisionally registered for drafts 05 and 06, and `initial_max_path_id` registered for draft 15. Draft-21 uses `PATH_ACK`, `PATH_ABANDON`, `PATH_STATUS_AVAILABLE/BACKUP`, `MAX_PATH_ID`, one packet number space per path | draft-21 §1, §2.1, §4, §6.1 **[F]** |

| Linux MPTCP upstream since v5.6, MPTCP v1 only | **Confirmed** (upstreamed Feb 2020, available from Linux 5.6). Older papers used the out-of-tree fork | Aschenbrenner et al. §I **[F]** |

| 2017 MPQUIC = research fork of quic-go on pre-IETF QUIC | **Confirmed** (quic-go extension; QUIC crypto handshake; WINDOW_UPDATE frames). **Not verified:** whether *mainline* quic-go has multipath today (I only saw the research fork) | CoNEXT'17 paper **[F]** |

| quiche multipath only in a blog; picoquic lists support | **Needs updating.** picoquic's README lists the evolving multipath draft. IETF-118 slides list xquic, picoquic, Rask and quiche in interop on draft-06. A 2026 paper cites a quiche pull request for multipath with non-zero-length CIDs. **Not verified:** whether that PR is merged or released | picoquic README, IETF 118 slides, ACM 3822163.3827925 reference list **[A]** |

| MPTCP adoption: middleboxes, false positives, Apple small share | **Confirmed**, with numbers in Q164 and Q293. The scan studied MPTCP **v0** only | Aschenbrenner et al. **[F]** |

---

## 2. Literature matrix (Q160 columns)

### 2.1 Empirical studies (setup cards)

Fields: implementation and version · emulator or testbed · path parameters · workload · metrics · congestion control · scheduler. "n/o" means not opened (abstract only).

| ID | Study | Read | Q159 focus |

| --- | --- | --- | --- |

| **S1** | De Coninck and Bonaventure, *Multipath QUIC: Design and Evaluation*, CoNEXT 2017 | **[F]** | aggregation, loss, handover (first MPQUIC vs MPTCP) |

| **S2** | Paasch, Ferlin, Alay, Bonaventure, *Experimental Evaluation of MPTCP Schedulers*, SIGCOMM CSWS 2014, Mininet part | **[F]** | scheduling |

| **S3** | Same paper, NorNet Edge real-network part | **[F]** | scheduling, receive-buffer limits |

| **S4** | De Coninck and Bonaventure, *MultipathTester*, MNM 2019 | **[F]** | handover on real phones; MPTCP vs MPQUIC |

| **S5** | Aschenbrenner et al., *From Single Lane to Highways*, IFIP Networking 2021: active scans | **[F]** | deployment |

| **S6** | Same paper: HTTP(S) GET timing, MPTCP vs TCP | **[F]** | deployment, middlebox impact |

| **S7** | Same paper: CAIDA and MAWI traffic traces | **[F]** | deployment (traffic share) |

| **S8** | Zheng et al., *XLINK*, SIGCOMM 2021 | **[A]** + blog + IETF-111 slides | QoE, scheduling at scale |

| **S9** | Lim, Nahum, Towsley, Gibbens, *ECF*, CoNEXT 2017 | **[A]** | scheduling, video |

| **S10** | Ferlin, Alay, Mehani, Boreli, *BLEST*, IFIP Networking 2016 | **[A]** | scheduling (HOL blocking) |

**S1: Multipath QUIC, CoNEXT 2017** **[F]**

- **Implementation:** MPQUIC = extension of quic-go (Google-QUIC era, QUIC-crypto handshake). MPTCP = Linux kernel 4.1.39 patched with MPTCP v0.91 (out-of-tree, protocol v0), default settings.

- **Emulator:** Mininet, two multihomed hosts, two disjoint paths; Intel Xeon E3-1245 V2, VM with 2 dedicated cores and 2 GB RAM.

- **Path parameters (WSP experimental design):** capacity 0.1–100 Mbps; RTT 0–50 ms (low-BDP) or 0–400 ms (high-BDP); queuing delay 0–100 ms (low-BDP) or 0–2000 ms (high-BDP); random loss 0–2.5%. 253 scenarios per class × 2 starting paths = 506 runs per class; 3 repeats; median reported.

- **Workload:** HTTPS GET of 20 MB on one stream (TLS 1.2 over (MP)TCP; QUIC crypto over (MP)QUIC); 256 KB GET (low-BDP, no loss only); handover test with 750 B requests every 400 ms; maximum receive window 16 MB for both.

- **Metrics:** download-time ratio (TCP/QUIC, MPTCP/MPQUIC); experimental aggregation benefit EBen; request delay.

- **Congestion control:** CUBIC for single-path TCP and QUIC; OLIA for MPTCP and MPQUIC.

- **Scheduler:** MPTCP default lowest-RTT; MPQUIC lowest-RTT plus duplication of traffic on a path while its RTT is unknown.

**S2: Paasch 2014, Mininet** **[F]**

- **Implementation:** Linux MPTCP release 0.88 (scheduler framework published from v0.89).

- **Emulator:** Mininet with the experimental-design method, two hosts, two subflows.

- **Path parameters:** capacity 0.1–100 Mbps; propagation delay 0–50 ms (low-BDP) or 0–400 ms (high-BDP); queuing 0–100 ms or 0–2000 ms; up to 200 experiments per class.

- **Workload:** iperf bulk, 60 s; application-limited stream of 8 KB blocks at a fixed rate.

- **Metrics:** aggregation benefit; goodput; worst-case relative delay increase over the minimum one-way delay.

- **Congestion control:** OLIA (similar results reported with LIA).

- **Schedulers:** round-robin (RR); lowest-RTT (LowRTT); LowRTT + retransmission and penalisation (RP); LowRTT + bufferbloat mitigation (BM).

**S3: Paasch 2014, NorNet Edge** **[F]**

- **Implementation:** standard Linux 3.11.7 with MPTCP.

- **Testbed:** real public WLAN (average RTT about 15 ms, about 10 Mbps) plus 3G/UMTS (RTT from 20 ms to seconds under bufferbloat, about 5 Mbps down).

- **Workload:** 16 MB downlink bulk with receive buffers of 2 MB (bounded) or 16 MB (unbounded); application-limited at 500 kbps and 1875 kbps; about 30 repeats over 3 weeks.

- **Metrics:** goodput; delay variation. **Congestion control:** OLIA. **Schedulers:** as S2.

**S4: MultipathTester, MNM 2019** **[F]**

- **Implementation:** iOS (Darwin) MPTCP in *interactive* mode vs the authors' mp-quic (old Google-QUIC format, via gomobile). Servers: Linux 4.14 MPTCP (lowest-RTT, fullmesh, OLIA) in France, Canada, Japan.

- **Testbed:** real iPhones on real Wi-Fi and cellular networks (1098 runs from 264 devices, 72 carriers, 288 SSIDs, Mar 2018–Apr 2019).

- **Workload:** ping (5 × 10 B GET); bulk 10 MB GET; iperf-like upload; *interactive* (2 KB request and 750 B reply every 100 ms in each direction). Mobile mode: interactive traffic while the user walks away from a Wi-Fi access point. MPTCP interactive mode uses two connections; QUIC uses one connection with two streams.

- **Metrics:** median delay; completion time; maximum application delay; Wi-Fi-to-cellular handover duration.

- **Scheduler:** iOS interactive: Wi-Fi first, cellular as backup, switch when Wi-Fi smoothed RTT > 600 ms, or Wi-Fi RTO fired, or Wi-Fi RTO > 1500 ms. MPQUIC configured to imitate this. **Congestion control:** servers OLIA; phone side not exposed.

**S5–S7: Aschenbrenner et al. 2021** **[F]**

- **Implementation:** MPTCP **v0** (RFC 6824) only; v1 results are on mptcp.io, not in the paper.

- **S5 scans:** ZMap + Tracebox; whole IPv4 space and an IPv6 hitlist; ports 80 and 443; Jul–Dec 2020.

- **S6 GET timing:** MPTCP vs TCP GETs from AWS Germany to hosts found in S5; 10+ runs per set, about two weeks; metrics: connect time, TLS handshake, time to first byte, completion time.

- **S7 traces:** CAIDA (Tier-1 backbone, 2015–2019, one-hour traces) and MAWI samplepoint-F (2014–2020, 15-minute captures on the third Thursday); flows with fewer than 5 packets removed.

- Congestion control and scheduler: not applicable.

**S8: XLINK** **[A]**: production A/B test in Taobao short-video service; user-space multipath QUIC; QoE-driven scheduling and re-injection; metrics: p99 chunk completion time, first-frame latency, rebuffering rate, redundant traffic. Congestion control, exact topology and path parameters: n/o.

**S9: ECF** **[A]**: Linux MPTCP; testbed plus in-the-wild; video streaming and web browsing; compares ECF with default and other schedulers. Version, parameters, congestion control: n/o.

**S10: BLEST** **[A]**: Linux-kernel implementations of several MPTCP schedulers; heterogeneous paths such as 3G + WLAN; bulk and web traffic. Version, parameters, congestion control: n/o.

### 2.2 Design, theory and standards documents

| Document | Read | What problem it addresses | Key claim (paraphrased) | Q159 focus | | --- | --- | --- | --- | --- |

| Wischik et al., NSDI 2011 | **[A]** | Congestion control when one connection uses several paths | Running ordinary TCP on every subflow can be harmful; their coupled algorithm improves throughput and fairness vs single-path TCP | fairness |

| RFC 6356 (Oct 2011) | **[S]** (cited in RFC 8041, draft-21) | Standardises that coupled increase (LIA) | Linux default congestion control for MPTCP | fairness |

| Khalili et al., *MPTCP is not Pareto-optimal* (OLIA), CoNEXT 2012 / ToN 2013 | **[A]** | Two flaws of LIA: (P1) upgrading some TCP users to MPTCP can hurt others with no gain to the upgraded users; (P2) MPTCP can be too aggressive | OLIA is Pareto-optimal and as responsive as LIA | fairness |

| BALIA (Peng et al., ToN 2016) | **[S]** (RFC 8041 §3.2) | Balance of TCP-friendliness, responsiveness, window oscillation | — | fairness |

| Raiciu et al., *How Hard Can It Be?*, NSDI 2012 | **[A]** + RFC 8041 summary | Making MPTCP deployable despite middleboxes; buffer and reordering heuristics | Introduced reinjection and penalisation for slow paths | deployment, scheduling |

| Honda et al., *Is it still possible to extend TCP?*, IMC 2011 | **[S]** (RFC 8041 §3.1) | Measures what middleboxes do to TCP extensions | Main motivation for MPTCP's middlebox-defence mechanisms | deployment |

| RFC 8041 (Jan 2017) | **[F]** | Use cases and operational experience with MPTCP v0 | See Q165 | deployment |

| RFC 8684 (Mar 2020) | **[A]** | MPTCP v1, obsoletes RFC 6824 | Changes driven by deployment experience | spec |

| draft-ietf-quic-multipath-21 (17 Mar 2026) | **[F]** | Multipath for QUIC v1 | Path IDs, per-path packet number spaces; scheduling and address management left out | spec |

| draft-deconinck-multipath-quic-00 (Oct 2017) | **[A]** | First MP-QUIC draft | Companion to S1 | spec |

---

## 3. Cross-training cards (Tier 1 for all four of you)

These are Q167, Q168 and Q172. Everyone must be able to say them cold. Full versions are in §4.

**Q167 — When does multipath aggregate well or badly?**

- **What:** It aggregates well when the paths are not too different and the receiver has enough buffer; it aggregates badly when RTTs differ a lot, buffers are small, flows are short, or the paths share a bottleneck.

- **Why:** A multipath receiver must deliver bytes in order. Data sent on the slow path holds up data from the fast path, and the stalled data fills the receive buffer.

- **Cost / caveat:** Three published conditions: receive buffer (S3: 16 MB buffer, all schedulers aggregate WLAN + 3G; 2 MB buffer, goodput suffers), BDP and starting path (S1: multipath beneficial in 58% of high-BDP scenarios for MPQUIC but 20% for MPTCP), flow length (S1: no point using multipath for 256 KB over unequal paths).

- **Check:** Compute EBen against the best single path on each path, and repeat with a larger and a smaller receive buffer. If EBen stays about the same when you enlarge the buffer, the buffer was not the limit.

**Q168 — Handover and failover: what do studies find, and what is the usual cause of a stall?**

- **What:** Multipath gives smooth handover only if the transport notices the failing path quickly. Handover on real phones is gradual, not abrupt.

- **Why:** A degrading Wi-Fi link rarely dies cleanly. The transport usually waits for a retransmission timeout (RTO) before moving data to the other path.

- **Cost / caveat:** S4 (real iPhones, MPTCP interactive mode, 231 mobile runs): about two-thirds of switches to cellular were triggered by a Wi-Fi RTO, and more than 60% of runs had a maximum application delay above 1 s. S1 (Mininet, MPQUIC only) also recovers after an RTO. The most common cause of a stall is therefore **failure-detection delay**; a second cause is a signalling gap (S4: iOS ignores ADD_ADDR, so a connection that started on IPv6 Wi-Fi could stay stuck when cellular is IPv4-only).

- **Check:** In a trace, mark the time the path stopped delivering, the time of the first RTO, and the first packet on the other path. The stall is the gap between the first and the last mark.

**Q172 — Does QUIC need multipath if it already has migration?**

- **What:** Migration moves the connection to a new path and releases the old one. Multipath keeps several paths open at the same time.

- **Why for:** Aggregation is impossible with migration; draft-21 §5.1 says creating a new path and later abandoning the old one gives smoother handover than migration; XLINK reports production gains.

- **Why against / cost:** Simultaneous use brings scheduling and head-of-line risks; draft-21 §1 says simultaneous use needs more care than the draft gives and that no IETF scheduling spec exists. Extra paths cost battery, data and complexity.

- **Check:** Compare, for the same handover event, migration versus an open second path: time to first packet delivered on the new path and number of delayed packets.

---

## 4. Part 9 answers (Q159–176)

### Reading the literature

#### Q159 — What research questions dominate, and which does each paper address?

**What.** Six questions recur: (1) **aggregation** (does a second path add throughput?); (2) **handover and failover**; (3) **scheduling** (which path carries the next data); (4) **fairness and congestion control** (do not hurt single-path flows at a shared bottleneck); (5) **deployment** (middleboxes, adoption); (6) **application QoE** (video, interactive traffic).

**Why.** These are the original reasons for multipath (Q1–Q14) turned into measurable claims.

**Cost / caveat.** Most papers cover one question and report conditions for it only; do not generalise from a paper's question to a different one. For example, S1 measures aggregation and loss but its handover test (§4.3) is MPQUIC alone.

**Check.** The matrix in §2 gives one focus per paper: S1 aggregation, loss, handover; S2 and S3 scheduling; S4 handover on phones; S5–S7 deployment; S8 QoE; S9 and S10 scheduling; Wischik, OLIA and RFC 6356 fairness; Raiciu 2012 deployment and scheduling.

#### Q160 — Why is every field needed before two studies can be compared?

**What.** Implementation and version, emulator, path parameters, workload, metrics, congestion control and scheduler.

**Why.** Each field can change the result by itself. Examples from the studies: S1 compares CUBIC (single-path) against OLIA (multipath), so "multipath benefit" includes a congestion-control change; S1 used MPTCP v0.91 on kernel 4.1.39, while S2 used release 0.88 and S3 Linux 3.11.7; S1's queuing delay goes to 2000 ms in high-BDP runs, which changes how much bufferbloat the scheduler sees; S1 measures EBen against single-path runs, S4 measures maximum application delay. Numbers measured with different versions or metrics cannot be set side by side.

**Cost / caveat.** Even with all fields equal, hardware and run counts differ (S1 uses a 2-core VM and 3 repeats; S3 uses about 30 repeats).

**Check.** Fill the matrix row before you quote a number; if a cell is "n/o" say so.

#### Q161 — Which implementations did the 2017 paper use, and what does that imply today?

**What.** MPQUIC was an extension of quic-go on pre-IETF Google QUIC (QUIC-crypto handshake, public header, WINDOW_UPDATE frames). MPTCP was Linux kernel 4.1.39 with the out-of-tree MPTCP v0.91, default settings, which speaks MPTCP v0 (RFC 6824). Both ran on a 2-core Mininet VM; both used HTTPS (TLS 1.2 over TCP, QUIC crypto over QUIC) [S1].

**Why it matters.** Today's draft is a different design: the paper put a Path ID in the unencrypted public header and added PATHS and ADD_ADDRESS frames; draft-21 derives the path ID from the connection ID, uses `PATH_ACK` and path-status frames, includes the path ID in the AEAD nonce, requires path validation before sending on a new path (anti-amplification applies), and lets only the client open paths. The paper's scheduler duplicates data while a path's RTT is unknown; draft-21 §5.5 says scheduling is a local decision and the draft specifies none. On the TCP side, upstream Linux speaks MPTCP v1 only.

**Cost / caveat.** The paper's absolute numbers and percentages describe that old stack. The directions (what hurts MPTCP; why QUIC's ACKs help) are hypotheses to test, not facts about draft-21 stacks.

**Check.** Compare S1 §3 with draft-21 §1, §2.4, §3, §5.5. Verified in the paper's text (not a guess).

#### Q162 — What did the paper find without loss and with loss, and which QUIC features explain the lossy result?

**What.** [S1: quic-go MPQUIC fork vs Linux 4.1.39 + MPTCP v0.91; Mininet, two disjoint paths; 20 MB HTTPS GET; 253 scenarios × 2 starting paths; median of 3 runs.]

- *Low-BDP, no random loss:* single-path TCP and QUIC performed alike (both used CUBIC). With multipath, QUIC was faster than TCP in 89% of scenarios. MPQUIC reached a higher experimental aggregation benefit in 77% of scenarios against 45% for MPTCP (the text does not define the threshold exactly; read Fig. 4 before quoting).

- *High-BDP, no loss:* multipath beneficial in 58% of scenarios with QUIC against 20% with TCP.

- *With loss (up to 2.5%):* (MP)QUIC nearly always beat (MP)TCP in low-BDP runs (Fig. 5) and still did in high-BDP runs (Fig. 8); multipath still helped QUIC in lossy low-BDP runs, though goodput varied more.

**Why.** The paper credits: an ACK frame that can report up to 256 ranges versus 2–3 SACK blocks, which makes early retransmission more effective and reduces head-of-line blocking; unique, increasing packet numbers (no retransmission ambiguity), giving cleaner RTT estimates; frames can be retransmitted on a different path, unlike MPTCP, which must retransmit in order on each subflow.

**Cost / caveat.** The measured loss is random and up to 2.5% only. Today's QUIC loss recovery (RFC 9002: PTO and related mechanisms) differs from the 2017 implementation, so the lossy-network result is not a claim about modern stacks.

**Check.** Reproduce in small form (Q176) with one lossy path and look at retransmission counts per path.

#### Q163 — What did MultipathTester study, and why does a phone measurement differ from Mininet?

**What.** An iOS app that compares iOS MPTCP (interactive mode) with the authors' MPQUIC on real phones, in a stable mode and a mobile mode. Setup details are in S4. Headline results: MPTCP often used cellular only after a Wi-Fi RTO (67.0% of switches; RTT threshold 2.2%, RTO threshold 11.0%, other 19.8%); only 10% of runs switched abruptly, while 58% had at least 10 s with both networks in use; more than 60% of runs had a maximum application delay above 1 s (median 2.6 s, 70th percentile 6 s); with the same scheduling policy, MPTCP and MPQUIC behaved similarly; MPTCP achieved higher throughput than MPQUIC at upload rates above 50 Mbps, probably implementation overhead.

**Why it differs from Mininet.** On a phone the paths are real (cross traffic, carrier NAT and middleboxes, radio fade, NAT64), the OS policy is part of the system (Apple's thresholds, opaque Wi-Fi Assist, aggregate mode restricted to developer phones), the transports are different implementations (kernel versus a Go library called through gomobile), and the runs cannot be repeated. Mininet gives control and repeatability but only the paths you built.

**Cost / caveat.** Self-selected volunteers; old Google-QUIC format; interactive traffic only while moving; the two protocols ran at the same time in the mobile test (the authors argue the load of 55 KB/s each way is negligible).

**Check.** Read S4 §II–IV; compare Fig. 6 and Fig. 7.

#### Q164 — What do the MPTCP deployment scans show, and why are echoing hosts a false-positive trap?

**What.** [S5: ZMap + Tracebox; MPTCP v0; entire IPv4 space and an IPv6 hitlist; ports 80 and 443; Jul–Dec 2020.] About 200 000 IPv4 addresses answered with MP_CAPABLE (about 3.3% of responsive hosts on port 80, about 4.6% on port 443). Most of them echoed the probe's own key: 96% of potential hosts on port 80 and 81% on port 443 sent back a mirrored key. After Tracebox filtering the paper counts 7.5k (port 80) and 6.9k (port 443) truly MPTCP-capable IPv4 addresses over six months, about 5.5k and 4.5k active in December 2020; IPv6: 31 and 27. Many hosts are transient. Apple (AS 6185 and AS 714, over 2000 IPv4 addresses) and ISPs such as Telstra and Korea Telecom account for much of it. [S7: CAIDA 2015–2019 and MAWI 2014–2020.] MPTCP traffic share stayed low, peaking near 0.4% of bytes at MAWI in June 2020, and over 99% of MPTCP traffic was HTTPS.

**Why echoing is a trap.** The scanner sends a SYN carrying MP_CAPABLE and a fixed key. A device that reflects unknown option bytes returns a SYN-ACK with MP_CAPABLE and *the same key*, so a non-MPTCP host looks MPTCP-capable. A real server generates a random 64-bit key; the probe's key had Hamming weight 16, and that weight was heavily over-represented in the replies. The paper attributes the echo to middleboxes; a SYN-ACK alone cannot tell you whether it is a box or the end host, which is why Tracebox (which hop modified the option) is used. An earlier 2015 scan of the Alexa top 1M made this mistake and was corrected.

**Cost / caveat.** Only v0, only servers on ports 80/443, no client-side or proxy deployments; passive traces show support, not necessarily use.

**Check.** Compare the returned key with the key you sent; run Tracebox from a vantage point; confirm a real MPTCP data transfer.

#### Q165 — What does RFC 8041 report, and which use cases worked?

**What.** RFC 8041 (Informational, Jan 2017; Bonaventure, Paasch, Detal) collects use cases and operational experience with MPTCP v0. Use cases: **datacenters** (multiple equal-cost paths; subflows from the same IP pair using different source ports; benefits measured in a public datacenter); **cellular/Wi-Fi offload** (simultaneous use, backup mode with the cellular subflow idle, and single-path mode with break-before-make); **proxies** (SOCKS proxy at Korea Telecom, reaching up to 850 Mbps; hybrid access networks combining DSL and LTE). Operational lessons: MPTCP falls back to TCP when middleboxes strip options; on one server only 125 of 184 000 connections fell back; the DSS checksum catches FTP application-layer gateways; only clients create subflows; lowest-RTT is the best compromise scheduler; segment size, DNS and CDN, captive portals, SYN cookies and layer-4 load balancers each bring problems.

**Why they worked.** Datacenters: many similar paths and short RTTs, with the operator controlling both ends. Phones: the main value was seamless handover (Siri on iOS since Sept 2013). Proxies: the operator controls both MPTCP ends and the client's access links.

**Cost / caveat.** RFC 8041 says no paper analysed Apple's deployment; short connections on smartphones mostly use only the first subflow; it covers v0, not today's v1.

**Check.** §2.1–2.3 and §3 of the RFC. #### Q166 — Which papers introduced opportunistic retransmission with penalisation, BLEST and ECF, and what gap did each close?
**What / Why.**
- **ORP (Raiciu et al., NSDI 2012).** *Gap:* when the receive buffer is small, a slow subflow blocks the fast one, and MPTCP over two paths can end up slower than TCP on the best path alone (as RFC 8041 summarises the paper). *Fix:* re-inject the blocking segment on the path with room (opportunistic retransmission) and shrink the slow subflow's window (penalisation).
- **BLEST (Ferlin, Alay, Mehani, Boreli, IFIP Networking 2016).** *Gap:* the default scheduler plus ORP reacts after blocking has begun; this costs spurious retransmissions and leaves resources underused. *Fix:* proactively estimate whether sending on the slow subflow would block the send window and skip it. Abstract numbers [S10: Linux kernel schedulers; heterogeneous paths; bulk traffic; setup details n/o]: +12% application goodput and 80% fewer unnecessary retransmissions than default MPTCP and other schedulers.
- **ECF (Lim, Nahum, Towsley, Gibbens, CoNEXT 2017).** *Gap:* the default lowest-RTT scheduler under-utilises the fast path under heterogeneity, which lowers video quality below what the aggregate bandwidth allows. *Fix:* use more than RTT (RTT, window and send-queue size) to decide whether to wait for the fast path. Abstract claim: more efficient path use, especially for video, and never worse in web browsing.
**Cost / caveat.** BLEST and ECF numbers come from abstracts; read the bodies for topologies, versions and congestion control before you quote them.
**Check.** Paasch 2014 (S2/S3) is the neutral comparison of RR, LowRTT, RP and BM.
### What the studies found
 
#### Q167 — Three published findings on when multipath aggregates well or badly
**What.** (1) **Receive buffer.** [S3: Linux 3.11.7; WLAN ≈10 Mbps + 3G ≈5 Mbps; 16 MB downlink bulk, about 30 runs.] With a 16 MB buffer all schedulers aggregate both paths; with a 2 MB buffer, goodput falls, and LowRTT+BM or LowRTT+RP do better. (2) **BDP and starting path.** [S1, 20 MB GET.] Low-BDP, no loss: MPQUIC reached higher aggregation in 77% of scenarios against 45% for MPTCP; high-BDP: multipath was beneficial in 58% of QUIC scenarios against 20% of TCP scenarios. MPTCP depends more on which path starts the connection. (3) **Short flows.** [S1: 256 KB GET, low-BDP, no loss.] Multipath is not useful; QUIC should stay single-path over unequal paths. Also: [S2: Mininet, low-BDP] no significant difference between schedulers, close to perfect aggregation; high-BDP becomes receive-window limited.
**Why.** In-order delivery plus RTT mismatch turns the slow path into a brake (Q7).
**Cost / caveat.** Each finding depends on its stated condition; none is a rule for every network.
**Check.** Change one condition at a time (buffer size, RTT ratio, flow length) and watch EBen.
 
#### Q168 — Handover and failover findings, and the most common cause of a stall
**What.** [S1: Mininet; MPQUIC only; 750 B requests every 400 ms; initial path 15 ms RTT, second 25 ms; initial path turns fully lossy at 3 s.] The client waits for an RTO, then retransmits on the other path; a PATHS frame tells the server so it does not wait for its own RTO. [S4: real iPhones, 231 mobile runs.] About two-thirds of switches followed a Wi-Fi RTO; handover is gradual (only 10% abrupt); more than 60% of runs had a maximum delay above 1 s; the tail reaching hundreds of seconds came from the iOS client ignoring ADD_ADDR (a connection started on IPv6 Wi-Fi stayed there when cellular was IPv4-only). [RFC 8041 [S]: INFOCOM'14 scenario.] A subflow that turned lossy keeps retransmitting data that was already delivered on the other subflow, which wastes window and can block.
**Why.** The sender cannot distinguish a short outage from a dead path until its loss-detection timer fires.
**Cost / caveat.** Faster detection (smaller thresholds) risks switching on a transient glitch and spending cellular data; the S1 handover test has no MPTCP counterpart in the same figure.
**Check.** In a capture, time the first RTO against the first packet on the new path.
 
#### Q169 — How schedulers change results (one number with its setup)
**What.** [S2: Linux MPTCP release 0.88; OLIA; Mininet high-BDP class (capacity 0.1–100 Mbps, propagation delay 0–400 ms, queuing 0–2000 ms), 200 experiments; application-limited stream of 8 KB blocks; metric: worst-case delay increase over the minimum one-way delay.] With LowRTT, 70% of experiments had a worst-case delay increase between 10% and 100%; with round-robin, roughly 40% of experiments had an increase between 100% and 1500%. [S3: NorNet; 500 kbps stream.] The round-robin delay variance was up to 10 times worse than LowRTT's.
**Why.** Round-robin ignores RTT, so it sends comparable amounts on the slow path and creates head-of-line blocking.
**Cost / caveat.** In bulk transfers, the ack clock decides, so RR and LowRTT behaved alike (S2 skipped RR for that reason). In low-BDP bulk runs, schedulers made little difference. BLEST's +12% goodput is abstract-only (Q166).
**Check.** Repeat with RR and LowRTT on a 20 ms / 150 ms path pair at a fixed application rate and compare delay.
 
#### Q170 — Short versus long flows, and what it implies for video, file transfer, VoIP
**What.** [S1: 256 KB GET, low-BDP, no loss.] QUIC beats TCP mainly because the handshake takes 1 RTT against 3 (TCP + TLS 1.2); multipath adds little. [RFC 8041 [S]: PAM'16 and IMC'13 studies.] Short connections matter on smartphones and the second subflow is nearly unused; no significant difference between congestion controls below 4 MB. [Paasch 2014 intro.] MPTCP works best with long-lasting flows. [S7: CAIDA.] The growth in MPTCP flows without a matching growth in bytes suggests mostly short transfers.
**Implication (reasoning, not a measured result).** *File transfer:* long, so aggregation can help if paths are not too different. *Video:* long session of medium-sized chunks; aggregation helps only when one path cannot carry the bitrate; otherwise backup or handover is the value (see S8). *VoIP:* low-rate and long-lived; the value is failover or redundancy, not throughput.
**Cost / caveat.** The implications are my inference from the above; label them as such.
**Check.** Sweep file size from 100 KB to 100 MB and find where EBen turns positive.
 
#### Q171 — Limitations the authors state, and which matters most
**What.** S1: Mininet only (real-world tests are future work); one implementation; two paths; short-file results only for one class "due to space"; the handover test is MPQUIC only. S4: old Google-QUIC implementation; aggregate mode cannot be tested on iOS; interactive traffic only while moving. S5–S7: v0 only; no client-side or proxy deployment; passive data shows support, not use. S2/S3: two subflows; scheduler design out of scope; cross traffic left for future work.
**Which matters most for this project.** The **version and implementation mismatch** (a 2017 quic-go fork and MPTCP v0.91 versus draft-21 stacks and upstream MPTCP v1), combined with **emulation-only** evidence: it limits how much any absolute number transfers.
**Cost / caveat.** Authors state limitations they know about; unstated threats are in Q294.
**Check.** Read each paper's discussion section for the list.
 
#### Q172 — Both sides of "does QUIC need multipath given migration?"
**For.** Migration (RFC 9000 §9) switches the connection to one new preferred path and releases the old one, so it cannot aggregate; the 2017 paper calls it a form of hard handover; draft-21 §5.1 states that opening a new path and then abandoning the old one is generally preferable to migration, for smoother handover and server-side control; XLINK reports a production gain (abstract [S8: Taobao A/B test vs single-path QUIC]: 19–50% lower p99 chunk completion time, 32% lower p99 first-frame latency, 23–67% lower rebuffering, at 2.1% redundant traffic).
**Against / caution.** Draft-21 §1 warns that simultaneous use needs more than it specifies to avoid negative effects, and says no IETF scheduling spec exists; the IETF-111 slides report that vanilla multipath scheduling did not do well in A/B tests (so extra mechanisms are needed). Extra paths cost battery and cellular data (RFC 8041 backup and single-path modes). Applications could also use two connections at the application layer for some needs (this last point is my reasoning, not from a source). The WG draft *What to do with QUIC multipath* (Dawkins, Jan 2021) exists to frame this question; I read only its introduction.
**Check.** For one handover event, compare time to first packet on the new path under migration versus an already-open second path.

## Response:
10/29/2026, 4:45:10 PM · gpt-6

Received **Part 1** of Claude’s research block, covering Part 9 (Q159–176), the literature matrix, experimental setup cards, cross-training cards, and the start of the detailed answers.

I’ll wait for **Part 2** before making changes or producing the final files. Once you send it, I’ll review both parts together against your original full project plan, check technical claims and source references, identify inconsistencies or unsupported numbers, and consolidate everything into **final, properly formatted, ready-to-paste deliverables** in the folder structure we created.

I’ll preserve the assigned question coverage and shared/team responsibilities, and clearly flag anything that still needs source verification rather than presenting it as established fact.

**Please send Part 2.**

## Prompt:
10/29/2026, 4:46:54 PM

here is the part 2 - ### Comparability
\
&#x20;
\
\#### Q173 — Sort published results into directly comparable, qualitatively relevant, not comparable
\
\*\*Criteria.\*\* A result is \*\*directly comparable\*\* only if all five hold: same protocol version and implementation lineage; same metric definition; overlapping topology and parameter region; same workload; same congestion control and scheduler. It is \*\*qualitatively relevant\*\* if the mechanism and direction transfer even though the implementation differs. Otherwise it is \*\*not comparable\*\*. This table assumes a Mininet/netem setup with a current Linux MPTCP (v1) and a current multipath-QUIC stack; adjust to your actual setup.
\
&#x20;
\
\| Class | Results | Reason |
\
\| --- | --- | --- |
\
\| Directly comparable | \*\*None by default.\*\* Exception: if you rerun the published 2017 artifacts (multipath-quic.org: Mininet images, quic-go fork, scripts) with the same MPTCP v0.91 image, the S1 numbers become comparable to \*that\* rerun | no current stack matches S1's versions |
\
\| Qualitatively relevant | S1 directions (RTT mismatch hurts MPTCP; QUIC's richer ACKs help under loss); S2/S3 scheduler lessons (receive-window limit; RP and BM help in high-BDP); BLEST and ECF mechanisms; S4 handover mechanism (RTO-triggered switch); RFC 8041 lessons; LIA and OLIA fairness findings | mechanisms hold; magnitudes do not |
\
\| Not comparable | S5–S7 (Internet scans and traces, MPTCP v0); S8 production numbers (user population, video workload, A/B design); S4 absolute delays (carriers, phones); absolute times and percentages from S1; BLEST and ECF percentages | different regime, population, version or metric |
\
&#x20;
\
\*\*Check.\*\* Before comparing, fill the S-row of §2 for your own run and compare field by field.
\
&#x20;
\
\#### Q174 — Why a 2017 quic-go fork throughput cannot be compared with picoquic or quiche today
\
\*\*What differs.\*\*
\
\- QUIC version: pre-IETF Google QUIC versus QUIC v1 (RFC 9000); handshake (QUIC crypto versus TLS 1.3); packet formats.
\
\- Multipath design: explicit Path ID in a public header and PATHS frame versus path ID derived from connection IDs, \`PATH_ACK\` and path-status frames; duplication while RTT unknown versus no specified scheduler; path validation and anti-amplification rules.
\
\- Loss recovery and congestion control: 2017 implementation (CUBIC single-path, OLIA multipath) versus RFC 9002-style recovery and whatever each library implements; pacing and ACK policy.
\
\- Implementation: Go (garbage collection) versus C/Rust libraries; crypto libraries and CPU offload; UDP I/O path (batching, GSO/GRO); user-space process versus kernel stack.
\
\- The TCP side: out-of-tree v0.91 on kernel 4.1.39 versus upstream MPTCP v1 on Linux 5.6 or newer, with different path managers and schedulers.
\
\- Environment: kernel, hardware (a 2-core VM), receive-window settings, emulation parameters, number of repeats, which draft version the stack implements.
\
\*\*Cost / caveat.\*\* Even two current stacks are not comparable unless they implement the same draft version; name the draft every time.
\
\*\*Check.\*\* Record every item above for each stack before comparing.
\
\#### Q175 — Why throughput and goodput are mislabelled, and how that misleads
\
\*\*What.\*\* \*\*Throughput\*\* counts bytes moved at some layer in some interval (including headers, retransmissions and duplicates). \*\*Goodput\*\* counts unique application bytes delivered, measured at the receiver. S1's aggregation benefit uses goodput; S2 and BLEST also talk about goodput.
\
\*\*Why it misleads.\*\* (a) Redundant scheduling inflates bytes sent: S1's MPQUIC duplicates traffic while RTT is unknown and XLINK adds 2.1% redundant traffic; (b) spurious retransmissions: BLEST reports 80% fewer unnecessary retransmissions [S10, abstract]; (c) header and option overhead differs (MPTCP DSS/options versus QUIC headers and AEAD tags); (d) sender-side counters versus receiver-side counters.
\
\*\*Cost / caveat.\*\* If a paper says "throughput" without saying where it was measured, treat the number as unreliable.
\
\*\*Check.\*\* Measure unique bytes delivered at the receiving application per unit time and report wire bytes separately.
\
&#x20;
\
\#### Q176 — Reproducing one published result in a small way
\
\*\*Pick.\*\* S1's large-file result: 20 MB GET over two disjoint paths, comparing MPTCP with TCP and MPQUIC with QUIC through EBen. (Running is parked in the plan, so this is a design, not a result.)
\
\*\*Small version.\*\* Three or four path configurations: symmetric (10 Mbps, 20 ms each); RTT asymmetry (20 ms / 150 ms); rate asymmetry; one path with 2% random loss. Measure single-path runs on each path first (EBen needs them), then multipath. Use at least the paper's 3 repeats; more is better. Record every field of the §2 card.
\
\*\*Scoring.\*\*
\
&#x20;
\
\| Verdict | Meaning |
\
\| --- | --- |
\
\| \*\*Reproduced\*\* | You used the same artifacts (multipath-quic.org images and scripts), and the direction and approximate size of the claim match, within the spread of your repeats |
\
\| \*\*Partly reproduced\*\* | The direction matches but the size differs, or only some classes reproduce; you used current stacks instead of the 2017 ones |
\
\| \*\*Not reproducible with this setup\*\* | Needs production traffic (XLINK), real carriers and iPhones (S4), or Internet-wide scanning (S5) |
\
&#x20;
\
\*\*Cost / caveat.\*\* With current stacks the best honest verdict is "partly reproduced" or "tests the same hypothesis on a different stack". For the scan study, use the authors' published dataset rather than scanning; scanning raises ethics issues.
\
\*\*Check.\*\* Compare your EBen distribution with the paper's CDFs (Fig. 4–8).
\
&#x20;
\
\---
\
&#x20;
\
\## 5. Part 18 answers (Q291–297) — Tier 3: one-line answer, know where to look
\
&#x20;
\
\#### Q291 — Timeline of multipath ideas
\
Tags: \*\*[F]\*\* or \*\*[A]\*\* = confirmed in a source I opened; \*\*[M]\*\* = from memory, confirm before use.
\
&#x20;
\
\| When | Event | Problem it answered | Tag |
\
\| --- | --- | --- | --- |
\
\| 2000 / Sept 2007 | \*\*SCTP\*\* (RFC 2960, then RFC 4960) with \*\*multihoming\*\* | One association can have several addresses for fault tolerance; it was \*not\* load sharing | RFC 4960 date \*\*[F]\*\* (cited in S1); RFC 2960 year \*\*[M]\*\*; "failover not sharing" from a 2003 post by the CMT author \*\*[A]\*\* |
\
\| Nov 2002 | \*\*pTCP\*\* (Hsieh and Sivakumar, ICNP) | Striping one connection over several paths to aggregate bandwidth (multihomed mobile hosts); evaluated in simulation | \*\*[A]\*\* |
\
\| c. 2004 | \*\*mTCP\*\* | Multipath TCP-like scheme with shared-path detection | \*\*[S]\*\* feature; year \*\*[M]\*\* |
\
\| 2006 | \*\*CMT-SCTP\*\* (Iyengar, Amer, Stewart, IEEE/ACM ToN) | Concurrent use of SCTP's paths; fixes receive-buffer blocking and spurious retransmissions | \*\*[A]\*\* |
\
\| 2008 | \*The resource pooling principle\* (Wischik et al.) | The idea that a network should pool path capacity | \*\*[S]\*\* (cited in S1) |
\
\| 2009 | \*\*MPTCP working group\*\* formed; Linux research kernel begins | Standardise one TCP connection over several paths | WG date \*\*[M]\*\*; Linux "2009–2017" \*\*[S]\*\* |
\
\| Oct 2010, Aug 2011 | MPTCP in \*\*datacenters\*\* (HotNets; SIGCOMM) | Use many equal-cost paths between single-homed servers | \*\*[S]\*\* (RFC 8041) |
\
\| Mar 2011 | Wischik et al., NSDI: \*\*coupled congestion control\*\*; \*\*RFC 6182\*\* architecture | Do no harm at shared bottlenecks | \*\*[A]\*\* |
\
\| Oct 2011 | \*\*RFC 6356\*\* (coupled CC, LIA) | Standardises it | \*\*[S]\*\* |
\
\| Nov 2011 | Honda et al., IMC: \*Is it still possible to extend TCP?\* | What do middleboxes do to TCP options? | \*\*[S]\*\* |
\
\| Apr 2012 | Raiciu et al., NSDI: \*How Hard Can It Be?\* | Deployable design and implementation; buffer tuning and reordering | \*\*[A]\*\* |
\
\| \*\*Jan 2013\*\* | \*\*RFC 6824\*\* (MPTCP v0, Experimental) | First specification | \*\*[F]\*\* (cited in 8041, ECF reference lists) |
\
\| \*\*Sept 2013\*\* | \*\*Apple\*\* ships MPTCP in iOS 7 for Siri | Seamless handover for a voice assistant | \*\*[F]\*\* (RFC 8041) |
\
\| June 2015 | Korea Telecom commercial service via SOCKS proxy | Aggregation for Wi-Fi + LTE phones | \*\*[F]\*\* (RFC 8041) |
\
\| \*\*Jan 2017\*\* | \*\*RFC 8041\*\* | Collects use cases and operational experience | \*\*[F]\*\* |
\
\| Sept 2017 | iOS 11 lets \*any\* app request MPTCP | Opens it to third-party apps | \*\*[F]\*\* (S4) |
\
\| 2013 and after | \*\*Google QUIC\*\*, then the IETF QUIC WG (formed 2016) | Faster, encrypted, evolvable transport over UDP | \*\*[S]\*\* |
\
\| Oct–Dec 2017 | \*\*2017 MPQUIC\*\*: draft-deconinck-multipath-quic-00 (Oct 2017); CoNEXT paper (Dec 2017) | Bring MPTCP-style benefits to QUIC | \*\*[F]\*\* |
\
\| Mar 2018 | draft-deconinck-quic-multipath-00 | Updated individual draft | \*\*[A]\*\* |
\
\| Feb–Mar 2020 | \*\*MPTCP upstream in Linux 5.6\*\*; \*\*RFC 8684\*\* (MPTCP v1, obsoletes 6824) | Deployment experience folded into v1; mainline support | \*\*[F]\*\* |
\
\| May 2021 | \*\*RFC 9000\*\* (QUIC v1) | QUIC standardised | \*\*[F]\*\* (draft-21 refs) |
\
\| Dec 2020 – Jan 2021 | Dawkins drafts on multipath questions for the QUIC WG | Frame the WG's multipath decision | \*\*[A]\*\* |
\
\| Jun–Aug 2021 | XLINK (Alibaba); Aschenbrenner scans | MP-QUIC at production scale; MPTCP adoption measured | \*\*[A]\*\* / \*\*[F]\*\* |
\
\| 2021 → | draft-lmbdhk-quic-multipath → \*\*draft-ietf-quic-multipath\*\* | Merge of three proposals into one WG draft | WG adoption date \*\*[M]\*\*; "three proposals" \*\*[F]\*\* (draft-21 §8) |
\
\| Oct 2022, Mar 2023, Oct 2023, Jul 2024, Apr 2025, \*\*Mar 2026\*\* | Drafts -03, -04, -06, -11, -14, \*\*-21\*\* | Iterating toward a standard; interop tests (xquic, picoquic, Rask, quiche on draft-06 at IETF 118) | \*\*[A]\*\* / \*\*[F]\*\* |
\
&#x20;
\
\#### Q292 — Why were earlier multipath transports not deployed, and what did MPTCP do differently?
\
\*\*What.\*\* pTCP, mTCP and CMT-SCTP were research designs evaluated mostly in simulation, and SCTP needed new transport support. The 2017 paper notes SCTP "generated interest" but is still not widely deployed.
\
\*\*Why MPTCP differed.\*\* Its subflows look like ordinary TCP connections with options, so they cross NATs and firewalls; it falls back to plain TCP when options are stripped; applications keep the TCP socket API and get a single reliable byte stream; it ships coupled congestion control for fairness; and it had an open-source Linux implementation, then Apple's adoption. The NSDI 2012 goals say the same: work wherever TCP works, benefit unmodified applications, perform at least as well as TCP without starving it.
\
\*\*Cost / caveat.\*\* The price is dependence on TCP options (middleboxes, 40-byte option space) and TCP's byte-stream reordering problems.
\
\*\*Check.\*\* S1 §1; NSDI'12 introduction; RFC 8684 §1. (That SCTP failed because of NAT and firewall support is my reasoning; confirm before stating it as fact.)
\
&#x20;
\
\#### Q293 — Evidence that middleboxes are less hostile than feared, and as hostile as feared; why labs and scans disagree
\
\*\*Less hostile.\*\* RFC 8041 §3.1: the Linux implementation falls back correctly when a middlebox strips MP_CAPABLE or DSS, and handles NAT, sequence-number rewriting, segment splitting and coalescing; on the multipath-tcp.org server only 125 of 184 000 connections fell back (28 client IPs; FTP gateways and some HTTP proxies). [S6: GET timing from AWS Germany; MPTCP v0.] For genuinely MPTCP-capable servers, no discernible difference from TCP; echoing middleboxes had no discernible effect either (traffic simply used TCP).
\
\*\*As hostile as feared.\*\* [S5/S6.] Middlebox-affected targets (402 hosts on port 80, 1.27k on port 443) were slower over MPTCP than TCP in about 30% of timing values and faster in about 10%, with delays of several seconds; MPTCP's silent fallback keeps connections working but loses the multipath benefit. RFC 8041 reports one box that accepted MP_CAPABLE in the SYN and later replaced the MPTCP options with EOL (fallback, no application impact). The need for an elaborate defence set (address, port, sequence, split, coalesce, option removal, payload change) is itself the evidence that such boxes exist (Honda IMC'11 [S]).
\
\*\*Why a lab and a scan disagree.\*\* A lab test (MBtest) injects known behaviours; a scan samples whatever is on the path to a particular set of servers, from one vantage point. They also measure different things: "does the connection still work" (lab: yes) versus "does MPTCP stay on" (scan: often no). Population effects matter (the scan hosts are mostly Apple, ISPs, hobbyists; most boxes in the study are geolocated in China).
\
\*\*Cost / caveat.\*\* The scan is MPTCP v0 and server-side only; the lab results are from 2013–2016.
\
\*\*Check.\*\* RFC 8041 §3.1; S5/S6 §III–D.
\
&#x20;
\
\#### Q294 — Threats to validity for two papers (S1 and S4)
\
\*\*S1 (MPQUIC, CoNEXT 2017).\*\*
\
\- \*Internal.\* The single-path baselines use CUBIC while the multipath runs use OLIA, so "benefit of multipath" includes a change of congestion control. MPTCP ran with default settings on an out-of-tree v0.91 kernel; TLS 1.2 against QUIC crypto gives different handshake costs (the authors note TLS 1.3 and TCP Fast Open would reduce this). Three repeats and the median hide variance (CDFs are over scenarios, not repeats). The VM has 2 cores, so crypto and CPU can limit the user-space QUIC. MPQUIC's duplication phase is part of the design being tested. Loss is random, not bursty; only two disjoint paths; one stream; no cross traffic.
\
\- \*External.\* Pre-IETF QUIC versus QUIC v1; MPTCP v0.91 versus upstream v1; Mininet versus real networks; Go implementation versus today's libraries.
\
\*\*S4 (MultipathTester, MNM 2019).\*\*
\
\- \*Internal.\* Volunteer, self-selected runs; MPTCP uses two connections for the interactive pattern while QUIC uses one connection with two streams (different head-of-line behaviour); iOS thresholds and Wi-Fi Assist are opaque; MPTCP (Darwin kernel) and MPQUIC (Go via gomobile) differ in efficiency; both protocols run at once in mobile tests; uncontrolled fade pattern.
\
\- \*External.\* 2018–2019 iOS and carriers; old Google-QUIC format; interactive traffic only.
\
\*\*Check.\*\* For each threat ask: would changing it change the conclusion?
\
\#### Q295 — What did XLINK target, and how does it differ from the IETF draft?
\
\*\*What.\*\* [S8: Alibaba, Taobao short-video service, production A/B test; user-space multipath QUIC; compared with single-path QUIC.] The problem: tail latency and rebuffering for short videos over mobile networks, and the finding that obvious multipath scheduling is not good enough (IETF-111 slides). The approach: the client sends video-player QoE information (for example play time left in the buffer) back to the server, which uses it to control scheduling, re-injection and path management. Abstract results: 19–50% lower p99 chunk completion time, 32% lower p99 first-frame latency, 23–67% lower rebuffering rate, at 2.1% redundant traffic.
\
\*\*Difference from the draft.\*\* Draft-21 specifies only mechanics (path IDs, frames, path management) and explicitly leaves out address management and scheduling. It has no QoE signal. XLINK's QoE feedback is application-specific and sits in the scheduler. The IETF-111 slides list "does multipath QUIC need extra signalling?" as an open question.
\
\*\*Cost / caveat.\*\* Abstract, blog and slides only; I did not read the paper body. [verify] Which XLINK frames match the draft is not checked.
\
\*\*Check.\*\* SIGCOMM 2021 paper §3–§5.
\
&#x20;
\
\#### Q296 — How did the design evolve from the 2017 research design to the IETF draft?
\
&#x20;
\
\| Aspect | 2017 design (S1) | Draft-21 (Mar 2026) | Why / evidence |
\
\| --- | --- | --- | --- |
\
\| Base protocol | Google QUIC | QUIC v1 (RFC 9000 etc.) | QUIC was standardised |
\
\| Path identity | Explicit Path ID in the unencrypted public header | Path ID bound to the connection ID; ID 0 is the initial path; IDs only increase and are never reused | The WG draft aims to use the same header format as QUIC v1 to minimise what multipath exposes on the wire (draft-07); S1 itself notes the header design exposes paths to middleboxes |
\
\| ACKs | ACK frame with Path ID | \`PATH_ACK\` | Per-path packet number spaces kept |
\
\| Nonce | Two options: a number used once across all paths, or Path ID in the nonce | Path ID mixed into the AEAD nonce; 32-bit limit | draft §2.4 |
\
\| Negotiation | Described in the Oct 2017 draft (not read) | Transport parameter \`initial_max_path_id\`; earlier \`enable_multipath\` (drafts 05–06) | draft §2.1, §6.1 |
\
\| Addresses | \`ADD_ADDRESS\` and \`PATHS\` frames | Address discovery out of scope; path-status frames | draft §1, §3.3 |
\
\| Opening a path | Either host (odd/even IDs), but only client implemented; data in the first packet | Client only; both sides need connection IDs for the same path ID; path validation unless the 4-tuple was validated | draft §3 |
\
\| Path status | Statistics in \`PATHS\` | \`PATH_STATUS_AVAILABLE\` / \`PATH_STATUS_BACKUP\` (split from one \`PATH_STATUS\` frame in draft-06) | IETF-118 slides; draft §4.3 |
\
\| Closing a path | Not in the text I read | \`PATH_ABANDON\` with error codes; state kept 3 PTOs | draft §3.4 |
\
\| Limits | None | \`MAX_PATH_ID\`, \`PATHS_BLOCKED\`, \`PATH_CIDS_BLOCKED\` | draft §4.6–4.7 |
\
\| Scheduler | Lowest-RTT plus duplication while RTT unknown | Not specified; "local decision" | draft §5.5 |
\
\| Congestion control | OLIA | Per path; LIA adaptable; BCP 133 advice | draft §5.3 |
\
\| Security | Encrypted frames avoid MPTCP-style option attacks | Memory, amplification and DoS considerations | draft §7 |
\
&#x20;
\
\*\*Caveat [verify].\*\* I read the 2017 paper and draft-21 in full and saw snippets of drafts 04–14, but I did not diff the intermediate drafts. The history between -00 and -14 (and when each rename happened) must be checked in the datatracker changelogs before you state it.
\
&#x20;
\
\#### Q297 — A claim you cannot back with a primary source, and how to check it
\
\*\*Example 1: "RFC 9443" is multipath QUIC.\*\* The plan found a blog giving this number. Checked today: RFC 9443 is "Multiplexing Scheme Updates for QUIC" (July 2023, B. Aboba, G. Salgueiro, C. Perkins), which updates RTP/DTLS/STUN demultiplexing; draft-21 of the multipath draft still has no RFC number. \*\*Method:\*\* open rfc-editor.org/info/rfcNNNN and read the title and abstract; open the datatracker page for the draft; check the "Replaces / Updates" lines; look in the IANA registry for the codepoints. \*\*If you cannot verify:\*\* write the claim, the source and the date, mark it "unverified, not used as evidence", and leave the number out of the report.
\
\*\*Example 2: a blog saying XLINK is "the only" multipath QUIC draft "tested in large-scale practice".\*\* The SIGCOMM abstract supports "first large-scale experimental study in production"; the word "only" is not backed by anything I read.
\
\*\*Example 3: a blog giving "15.03%" as XLINK's average fragment-download gain.\*\* I could not match it to the abstract's metrics (p99 request completion time, 19–50%). Do not quote it without the paper.
\
\*\*What to write when you cannot back a claim.\*\* "Claimed by [source, date]; not verified against a primary source; not used."
\
&#x20;
\
\--- ## 6. One-page guide for this block: reading a multipath paper critically\
&#x20;\
\*\*Five questions to ask before you trust a number\*\*\
1\. \*\*Which implementation and version?\*\* (MPTCP v0.88, v0.91, v0.96 or upstream v1; a 2017 quic-go fork or a draft-21 stack.)\
2\. \*\*Which setup?\*\* Emulator or real network, path parameters, number of runs, hardware.\
3\. \*\*Which workload?\*\* Bulk, short GET, request/response, video.\
4\. \*\*Which metric, measured where?\*\* Goodput at the receiver, completion time, delay; EBen needs single-path runs.\
5\. \*\*Which congestion control and scheduler?\*\* A different congestion control between baseline and multipath changes the answer.\
\*\*Evidence ladder (strongest first):\*\* RFC or draft section → paper's own setup and figures → paper's abstract → second-hand description → blog or video → memory. Write the rung next to each claim.\
&#x20;\
\*\*Five traps seen in this block\*\*\
\- Quoting a percentage without the scenario count and class (S1's 89% / 77% / 58% belong to specific classes).\
\- Treating abstract numbers (BLEST, ECF, XLINK) as if you had read the setup.\
\- Comparing a 2017 fork with a 2026 stack as if they were the same protocol.\
\- Throughput versus goodput (Q175).\
\- A scan that counts echoed options as MPTCP support (Q164).\
\*\*Core results to remember (each with its setup)\*\*\
\- S1 [fork vs v0.91; Mininet; 20 MB]: QUIC beat TCP in 89% of low-BDP no-loss multipath scenarios; (MP)QUIC better under loss; multipath not useful for 256 KB.\
\- S2/S3 [MPTCP 0.88 / 3.11.7; Mininet / NorNet]: bounded receive buffers and high BDP are where schedulers matter; RR is worst for delay.\
\- S4 [iPhones; 231 mobile runs]: switch to cellular mostly follows a Wi-Fi RTO; handover is gradual.\
\- S5–S7 [v0; 2020 scans; 2014–2020 traces]: most "MPTCP hosts" in naive scans echo the probe; true use is a tiny share, mostly HTTPS.\
\- S8 [production A/B; abstract]: QoE-aware scheduling cut tail latency and rebuffering for 2.1% extra traffic.\
\---\
&#x20;\
\## 7. Gap list: what I could not verify (close these before the mock vivas)\
&#x20;\
\| # | Gap | Why it matters | Where to look | Q |\
\| --- | --- | --- | --- | --- |\
\| 1 | BLEST, ECF, XLINK, Wischik, OLIA, Raiciu 2012 read at abstract level only | Setups and numbers are not checked | Full PDFs (links in §9) | Q166, Q169, Q295 |\
\| 2 | S1 figure details (Fig. 4: how the 77% / 45% were defined) | I quote them with a caveat | S1 §4.1, Fig. 3–8 | Q162, Q167 |\
\| 3 | BALIA, Honda IMC 2011 known only through RFC 8041 | Second-hand | RFC 8041 §3.1–3.2, originals | Q293 |\
\| 4 | mTCP year; MPTCP WG formation date; RFC 2960 year; WG adoption date of the multipath draft | From memory | datatracker WG pages, RFC pages | Q291 |\
\| 5 | Draft history between -00 and -14; PATH_STANDBY → PATH_BACKUP naming | Q296 needs it | datatracker changelogs; github.com/quicwg/multipath | Q296 |\
\| 6 | Draft-21 shows an expired Internet-Draft (18 Sep 2026); is there a -22 or an RFC Editor entry? | Status line in the report | datatracker, rfc-editor queue | §1 |\
\| 7 | Whether mainline quic-go has multipath; whether the quiche PR is merged; picoquic version support | Implementation landscape | the repositories' READMEs and releases | Q174 |\
\| 8 | Dawkins draft read only at the introduction | Q172 background | draft-dawkins-quic-what-to-do-with-multipath | Q172 |\
\| 9 | RFC 8684 §1 constraints (the two WG constraints) not opened | Q292 wording | RFC 8684 §1 | Q292 |\
\| 10 | Whether SCTP's non-deployment was due to NAT and firewall support | Reasoning, not sourced | Budzisz et al., SCTP survey (cited in S1) | Q292 |\
&#x20;\
\---\
&#x20;\
\## 8. Teach-back script (10 minutes, one drawing: the literature matrix)\
&#x20;\
\*\*Minutes 0–2: the map.\*\* Six questions (aggregation, handover, scheduling, fairness, deployment, QoE); name one paper for each. Draw the matrix with the Q160 columns, filled for S1.\
&#x20;\
\*\*Minutes 2–5: three findings and their conditions\*\* (Q167). Receive buffer (S3), BDP and starting path (S1), short flows (S1). Say the setup out loud each time.\
&#x20;\
\*\*Minutes 5–7: the two pairs that cause confusion.\*\* The 2017 MPQUIC versus draft-21 (Q161, Q296); the scan versus the lab (Q164, Q293).\
&#x20;\
\*\*Minutes 7–9: handover and the stall\*\* (Q168), and both sides of "does QUIC need multipath?" (Q172).\
&#x20;\
\*\*Minutes 9–10: honest limits.\*\* Name two gaps from §7.\
&#x20;\
\*\*Five cold questions the others may ask\*\*\
1\. Why is MPQUIC faster than MPTCP in S1 when both use OLIA? \*(ACK ranges, packet numbers without ambiguity, path usable from the first packet, retransmission on any path; and the caveat that it is an old fork.)\*\
2\. Why can a scan report an MPTCP host that is not one? \*(Echoed key; Hamming weight; Tracebox.)\*\
3\. What stalls a handover? \*(Waiting for RTO; no ADD_ADDR.)\*\
4\. Can I quote "89%"? \*(Only with: fork vs MPTCP v0.91, Mininet, 20 MB, low-BDP no loss, 253 scenarios.)\*\
5\. Is MP-QUIC an RFC? \*(No. Draft-21, 17 Mar 2026; RFC 9443 is unrelated.)\*\
\---\
&#x20;\
\## 9. Sources opened in this session\
&#x20;\
\*\*Full text [F]\*\*\
\- De Coninck and Bonaventure, \*Multipath QUIC: Design and Evaluation\* (CoNEXT 2017): https\://inl.info.ucl.ac.be/system/files/conext17-deconinck.pdf\
\- De Coninck and Bonaventure, \*MultipathTester\* (MNM 2019): https\://inl.info.ucl.ac.be/system/files/multipathtester.pdf\
\- Aschenbrenner et al., \*From Single Lane to Highways\* (IFIP Networking 2021): https\://arxiv.org/pdf/2106.07351\
\- Paasch et al., \*Experimental Evaluation of Multipath TCP Schedulers\* (CSWS 2014): https\://inl.info.ucl.ac.be/publications/experimental-evaluation-multipath-tcp-schedulers.html (full text read from a mirror copy)\
\- RFC 8041: https\://datatracker.ietf.org/doc/html/rfc8041\
\- draft-ietf-quic-multipath-21: https\://datatracker.ietf.org/doc/html/draft-ietf-quic-multipath\
\*\*Abstract or landing page only [A]\*\*\
\- Raiciu et al., NSDI 2012: https\://usenix.org/conference/nsdi12/technical-sessions/presentation/raiciu\
\- Wischik et al., NSDI 2011: https\://usenix.org/conference/nsdi11/design-implementation-and-evaluation-congestion-control-multipath-tcp\
\- Khalili et al. (OLIA): https\://infoscience.epfl.ch/entities/publication/51204650-75eb-4416-9ac2-4cfa87708c10\
\- BLEST: https\://dl.ifip.org/db/conf/networking/networking2016/1570234725.pdf\
\- ECF: https\://dblp.dagstuhl.de/rec/conf/conext/LimNTG17.html and https\://core.ac.uk/works/52648723\
\- XLINK: https\://conferences.sigcomm.org/sigcomm/2021/files/papers/3452296.3472893.pdf, abstract at https\://unpaywall.org/10.1145%2F3452296.3472893, blog https\://blog.apnic.net/2021/12/08/efficient-multipath-transport-with-quic-video-services/, slides https\://datatracker.ietf.org/meeting/111/materials/slides-111-quic-multipath-experiments-00.pdf\
\- IETF 118 interop slides: https\://datatracker.ietf.org/meeting/118/materials/slides-118-quic-multipath-quic-00\
\- RFC 8684: https\://www\.rfc-editor.org/info/rfc8684 · RFC 9443: https\://www\.rfc-editor.org/info/rfc9443\
\- CMT-SCTP (Iyengar, Amer): https\://www\.eecis.udel.edu/\~amer/PEL/poc/pdf/ToN2006-CMT-over-Independent-Paths-Iyengar.pdf\
\- multipath-quic.org artifacts page: https\://multipath-quic.org/conext17.html\
\- picoquic README: https\://github.com/Quicr/picoquic\
\---\
&#x20;\
*End of file. Remaining actions for you: work through §7, add page or figure numbers to each answer, and rewrite each in your own words before the mock viva.*

## Response:
10/29/2026, 4:46:01 PM · gpt-6

Got it. This is **Part 2 of your MPTCP-MPQUIC project plan**, covering Q173-176, Q291-297, the critical-paper-reading guide, verification gaps, and your 10-minute teach-back.

Since your goal is to complete the **full older plan**, we should file this material in the appropriate folders rather than mix it into Q1-28.

## 1\. Run these PowerShell commands

```powershell
$base = Join-Path $env:USERPROFILE "Documents\MPTCP_MPQUIC_Swamini"
Set-Location $base

notepad ".\05_Research_Q159-176\Research_Answers.md"
```

Paste the **Q173-176** section under the existing research answers. Save with `Ctrl+S` and close Notepad.

Next, open the literature/history file\:

```powershell
notepad ".\09_Literature_History_Q291-297\Literature_History.md"
```

Paste **Q291-297** into this file, then save and close it.

## 2\. Put the remaining material in its own files

Run these commands one at a time\:

```powershell
notepad ".\13_Literature_Matrix\Literature_Matrix.csv"
```

This file is a CSV, so **don't paste the prose guide into it**\. Keep it for the structured comparison of papers and experiments.

Create a separate critical-reading guide\:

```powershell
notepad ".\13_Literature_Matrix\Reading_a_Multipath_Paper.md"
```

Paste the section titled **“One-page guide for this block: reading a multipath paper critically”** into it.

Create a file for unresolved verification gaps\:

```powershell
notepad ".\00_Project_Admin\Verification_Gaps.md"
```

Paste the **“Gap list: what I could not verify”** section into it.

Save and close each file after pasting.

## 3\. Save the teach-back script

```powershell
notepad ".\14_Team_Guides_and_Reviews\Swamini_Teach_Back.md"
```

Paste the **10-minute teach-back script** and its five cold questions. Save the file.

## 4\. Verify the files

Run\:

```powershell
Test-Path ".\05_Research_Q159-176\Research_Answers.md"
Test-Path ".\09_Literature_History_Q291-297\Literature_History.md"
Test-Path ".\13_Literature_Matrix\Reading_a_Multipath_Paper.md"
Test-Path ".\00_Project_Admin\Verification_Gaps.md"
Test-Path ".\14_Team_Guides_and_Reviews\Swamini_Teach_Back.md"
```

Each command should return `True`\.

**Important\:** These commands only open or create the files. You still need to copy the corresponding sections from your message into them. Also, preserve the `[F]`, `[A]`, `[S]`, `[M]`, and `[verify]` labels; they distinguish evidence levels and unresolved claims.

Once this is saved, we can continue with the next unfinished section of your original plan, without treating these literature answers as a substitute for the remaining questions.

## Prompt:
10/29/2026, 4:50:09 PM

now before moving ahead give me exactly what all we have covered till now and what all is remaining to complete this project from my side in short tell then will move to the next part

## Response:
10/29/2026, 4:49:15 PM · gpt-6

## Project status — what we have covered so far

Based on the material shared so far, here is the current status. I’m distinguishing **content we have prepared** from work that is still pending; I can’t confirm that everything has been saved into the correct project files yet.

### 1\. Completed content so far

| Area | What we have covered |
|--------|--------|
| Research questions Q173–Q176 | Four questions on study/research-related topics, with detailed answers and examples. |
| Literature/history questions Q291–Q297 | Seven questions covering historical and literature-related topics, including explanations and examples. |
| One-page reading guide | A guide for critically reading research papers. |
| Research gap list | Identified gaps and remaining improvements in the research material. |
| Teach-back notes | A structured explanation intended to help communicate the research clearly. |
| Source tracking | A list of sources already opened or consulted. |

### 2\. What remains to complete from your side

- [ ] **Organize and save** each completed section in its appropriate project folder and file.
- [ ] **Verify references\:** add page numbers, figure numbers, or other precise source locations where required.
- [ ] **Address the research gaps** identified in the notes.
- [ ] **Review and validate answers** against the original papers and sources.
- [ ] **Complete the remaining question blocks** in the project's original plan.
- [ ] **Consolidate the final deliverables\:** research answers, literature notes, source register, reading guide, and teach-back notes.
- [ ] **Perform a final completeness check** against the original project requirements.

### 3\. Where we stand

**Content prepared**

The sections listed above have been shared in the conversation.

---

**Project completion not yet verified**

Folder placement, source validation, remaining questions, and final deliverables still need checking.

**Important\:** I can confirm only the material shared here. I don't yet have enough evidence to say exactly how many questions remain in the *entire project*, because the complete master question list and project requirements have not been established in this exchange.

We can now move to the next part, continuing with the original project structure rather than duplicating work already covered.

## Prompt:
10/29/2026, 4:51:27 PM

im asking for the overall project were are we currently and what all we still need to complete to finish this projects my part

## Response:
10/29/2026, 4:50:34 PM · gpt-6

> **Remembering**
>
>
> ****
>
> 
>
> **Reviewed project progress and identified remaining deliverables**
>
> 
>
> Worked for 13s

You're asking about your **entire Computer Networks project on MPTCP vs MP-QUIC**, including your assigned research, shared work, experiments, and final submission — not just the questions in the latest section. You're right; I misunderstood that earlier.

## Overall project status

**1\. Foundations and initial research**

Q1–Q28 were prepared in the project workspace, including the initial Q1–Q14 material and the transport-fundamentals section.

---

**2\. Research-question material**

The workspace includes research answers for Q159–Q176. You have also shared material for the literature/history questions Q291–Q297 and supporting research notes.

---

**3\. Your remaining assigned research**

The other assigned question blocks still need to be completed, checked against sources, and consolidated into the appropriate folders.

---

**4\. Technical and shared project work**

Your MPTCP/MP-QUIC comparison, experiment evidence, diagrams, analysis, and final project materials must be checked against the full team plan. I cannot confirm from the available progress record that these are finished.

## Your remaining work

Your recorded assignment is\:

| Responsibility | Question blocks |
|--------|--------|
| Individual research | Q159–176, Q265–279, Q280–290, Q291–297 |
| Lead responsibility | Q177–190 |
| Shared responsibility | Q1–28, Q177–205, Q281, Q298–300, Q133 |

The exact completion status of every block needs to be verified against the actual saved files.

You also need to ensure the following overall deliverables are complete\:

- [ ] Finish all outstanding assigned questions and validate citations.
- [ ] Complete the literature matrix, source register, research-gap notes, and diagrams.
- [ ] Coordinate and integrate the other members' protocol and methodology material.
- [ ] Verify the technical comparison and experiment results, including the relevant logs, measurements, and analysis required by your team's plan.
- [ ] Prepare the final comparison, conclusions, presentation/report, and viva or revision guide.
- [ ] Check the final submission against the original project requirements.

**Deadline recorded\:** November 4, 2026.

**Where we stand\:** We have established the project structure and prepared a meaningful amount of the written research. However, I cannot honestly label the whole project nearly finished or give a reliable completion percentage until we verify the saved files and the technical work.

The next step should be to **continue with the next outstanding question block in your original plan**, while tracking each completed block and deliverable so nothing is missed.

## Prompt:
10/30/2026, 3:43:09 PM

done, now lets move to the next part

## Response:
10/30/2026, 3:42:17 PM · gpt-6

> **Remembering**
>
>
> ****
>
> 
>
> **Reviewed MPTCP and MP-QUIC progress and identified next tasks**
>
> 
>
> Worked for 9s

Great. Let's move to the next section of your **MPTCP vs MP-QUIC project**\.

### Next part: Q265–Q279 — Theory

This is the next outstanding research block in your original plan.

We'll follow the same workflow\:

1. Go through each question individually.
2. Prepare technically accurate, detailed answers.
3. Include examples, diagrams, and relevant protocol explanations wherever useful.
4. Track references and source material.
5. Identify anything that needs further verification.
6. Organize the completed answers into the correct project folder.

After this, we'll cover\:

- **Q280–Q290\:** Applications and QoE.
- **Q177–Q190\:** Your lead-assigned applications section.
- Remaining shared questions and project deliverables.

**Send me the Q265–Q279 section (questions or source material), and we'll start with Q265.**

## Prompt:
10/30/2026, 3:48:13 PM

ive shared the complete plan here again where all the plan and questions are here

[Attachment: mptcp-mpquic-understanding-plan(1).md]

## Response:
10/30/2026, 3:47:20 PM · gpt-6

> **Confirming next steps**
>
> I’m reviewing the complete plan and current progress so I can continue from the correct section rather than repeat earlier work. I’m checking the sequence and the latest completed block before proceeding.
>
> **Confirmed next steps**
>
> 
>
> **Resumed original plan with questions 265–279**
>
> 
>
> **Finding exact text for questions 265–279**
>
>
> **Found exact text for questions 265–279**
>
> 
>
> Worked for 28s

Got it. I've received the complete **MPTCP vs MP-QUIC Understanding Plan (21 October–2 November 2026)**, including the full question bank, ownership assignments, reading list, study schedule, and parked hands-on tasks.

I'll use this original plan as our reference from now on. You do **not** need to resend individual questions or explain the project structure again.

According to Section 6, your individual responsibility is\:

- Part 9: Q159–176 — Existing research
- Part 16: Q265–279 — Congestion control, fairness and scheduling theory
- Part 17: Q280–290 — Applications and QoE
- Part 18: Q291–297 — Literature and history
- Lead Part 10: Q177–190 — Applications and recommendations

You also have shared responsibilities and cross-training questions.

## Next section: Part 16 — Q265–Q279

(Your individual responsibility · Tier 1)

**Topic\:** Congestion control, fairness and scheduling theory.

This section builds on\:

- Q52–Q55: MPTCP congestion control.
- Q117–Q119: Scheduling and blocking.
- Q126: Congestion-control comparison.

We'll proceed question by question, using the plan's four-beat structure: **what it is → why it exists → what it costs → how to verify it.**

### Q265. Define max-min fairness, proportional fairness and Jain's fairness index. Which one does TCP's AIMD approximate, and what does "TCP-friendly" mean?

**1\. Max-min fairness**

An allocation is max-min fair if no flow can receive more bandwidth without reducing the allocation of another flow that already receives an equal or smaller share.

In simple terms, bandwidth is distributed so that the least-served flows receive priority before already better-served flows receive additional bandwidth.

Example: Suppose three flows share a 12 Mbps bottleneck with equal demands.

- Flow A: 4 Mbps
- Flow B: 4 Mbps
- Flow C: 4 Mbps

This is max-min fair because all three receive an equal share.

**2\. Proportional fairness**

An allocation is proportionally fair if no alternative allocation can produce a positive aggregate proportional improvement across flows.

Mathematically, for current rates $x_i$ and a feasible alternative $y_i$\:

$$
\sum_i \frac{y_i-x_i}{x_i}\leq 0
$$

It balances overall network efficiency against fairness rather than requiring equal bandwidth for everyone.

**3\. Jain's fairness index**

This is a numerical measure of how fairly resources are distributed.

$$
J(x_1,\ldots,x_n)=
\frac{(\sum_{i=1}^{n}x_i)^2}
{n\sum_{i=1}^{n}x_i^2}
$$

- $J=1$\: perfectly equal allocation.
- Values closer to 0: increasingly unequal allocation.
- It is useful for comparing fairness between different congestion-control algorithms.

**4\. Which one does TCP's AIMD approximate?**

TCP's Additive Increase Multiplicative Decrease (AIMD) tends towards fair sharing among competing flows under suitable assumptions, particularly when flows experience the same bottleneck and have comparable RTTs and congestion-control parameters.

It is associated with max-min-style fairness, but it does not guarantee perfectly equal bandwidth in every real network. RTT differences, different algorithms and multiple bottlenecks can change the outcome.

**5\. What does TCP-friendly mean?**

A congestion-controlled flow is TCP-friendly if it does not consume significantly more bandwidth than a comparable TCP flow competing under similar network conditions.

For example, a UDP-based transport should not aggressively increase its sending rate and starve ordinary TCP flows sharing the same bottleneck.

**Why this matters for MPTCP vs MP-QUIC**

A multipath connection can behave like several competing flows. If it opens two subflows and each independently takes a TCP-like share, it may obtain an unfair advantage over a single-path TCP connection.

This is one reason coupled congestion control is important.

**Evidence to study\:** Chiu and Jain (1989), *Analysis of the Increase and Decrease Algorithms for Congestion Avoidance in Computer Networks*; RFC 5681 for TCP congestion control; RFC 6356 for coupled congestion control in MPTCP.

---

**Checkpoint\:** Make sure you can distinguish these three concepts without notes. Next, we'll tackle **Q266: Why does AIMD converge towards fairness, and what happens when flows use different increase parameters?**

## Prompt:
10/30/2026, 3:53:56 PM

give complete part 16 answers everything to putint he file we made, igive in proper way to paste in that md file this complete section

## Response:
10/30/2026, 3:53:06 PM · gpt-6

> **Remembering**
>
>
> ****
>
> 
>
> **Reconstructed prior answers, topics, notes structure, and response style**
>
> 
>
> Worked for 17s

Below is the **complete, paste-ready Part 16 section (Q265-Q279)** for\:

`07_Congestion_Fairness_Q265-279/Congestion_Fairness_Scheduling.md`

I’ve kept the original question order and used the four-beat structure for each answer: **what it means → why it matters → limitations/trade-offs → how to verify or explain it**\. The answers are written for your project notes and should also prepare you for viva questions. Where behaviour depends on the implementation or network conditions, I’ve stated that rather than presenting it as a universal rule.

**document: **

# Part 16 - Congestion Control, Fairness and Scheduling Theory (Q265-Q279)

**Owner:** Swamini  
**Scope:** Congestion-control fairness, coupled congestion control, resource pooling, shared-bottleneck detection, BBR, multipath scheduling, blocking, performance diagnosis, FEC and network coding.

---

## Q265. Define max-min fairness, proportional fairness and Jain's fairness index. Which one does TCP's AIMD approximate, and what does "TCP-friendly" mean?

### 1. Max-min fairness

An allocation is **max-min fair** if no user's allocation can be increased without decreasing the allocation of another user that already has an equal or smaller allocation.

In simple terms, it tries to improve the allocation of the least-served user first.

**Example:** Suppose three flows share a 12 Mbps bottleneck and have equal access requirements. A max-min fair allocation is:

- Flow 1: 4 Mbps
- Flow 2: 4 Mbps
- Flow 3: 4 Mbps

Now suppose Flow 3 can use only 2 Mbps because its receiver or another path limits it. The remaining capacity can be redistributed:

- Flow 1: 5 Mbps
- Flow 2: 5 Mbps
- Flow 3: 2 Mbps

The allocation is max-min fair because increasing either of the first two flows would require reducing another flow that already has an allocation no greater than the proposed increase.

### 2. Proportional fairness

An allocation is **proportionally fair** if any feasible change in the allocation produces a non-positive sum of proportional changes:

$$
\sum_i \frac{x_i-x_i^*}{x_i^*} \leq 0
$$

Here:

- $x_i^*$ is the current allocation to flow $i$.
- $x_i$ is a proposed alternative feasible allocation.

It balances total efficiency against fairness. A large proportional improvement for one flow must be balanced by proportional losses elsewhere.

Proportional fairness does not necessarily mean equal bandwidth for every flow.

### 3. Jain's fairness index

Jain's index is a numerical measure of how equally a resource is distributed:

$$
J(x_1,\ldots,x_n)=
\frac{(\sum_{i=1}^{n}x_i)^2}
{n\sum_{i=1}^{n}x_i^2}
$$

Its value lies between $1/n$ and 1 for non-negative allocations with a non-zero total.

- $J=1$: perfectly equal allocation.
- A value closer to 1: more equal allocation.
- A lower value: greater inequality.

**Example:**

For allocations of 5 Mbps, 5 Mbps and 5 Mbps:

$$
J=\frac{15^2}{3(25+25+25)}=1
$$

For allocations of 10 Mbps, 2 Mbps and 2 Mbps:

$$
J=\frac{14^2}{3(100+4+4)}
\approx 0.647
$$

Jain's index measures equality, not whether the network is fully utilized or whether the allocation is optimal.

### 4. What fairness does TCP AIMD approximate?

TCP's Additive Increase Multiplicative Decrease (AIMD) is associated with convergence towards fair sharing when competing flows use comparable congestion-control parameters and share a bottleneck.

- **Additive increase:** increase the congestion window gradually when acknowledgements arrive.
- **Multiplicative decrease:** reduce the congestion window by a multiplicative factor after congestion is detected.

Under the simplified assumptions studied by Chiu and Jain, AIMD converges towards an efficient and fair operating point.

However, TCP AIMD does not guarantee max-min fairness in every real network. Different RTTs, different congestion-control algorithms, multiple bottlenecks and implementation differences can change the resulting allocation. TCP throughput is also RTT-sensitive.

### 5. What does TCP-friendly mean?

A transport is **TCP-friendly** if it does not consume substantially more bandwidth than a comparable TCP flow under similar network conditions.

The purpose is to allow a new transport protocol to coexist fairly with conventional TCP traffic.

For MPTCP, this is particularly important: if every subflow independently behaved like a separate TCP connection, one multipath connection could obtain multiple shares of a shared bottleneck. Coupled congestion control is designed to prevent this unfair advantage.

**Key takeaway:** Max-min fairness and proportional fairness describe allocation policies; Jain's index measures equality; TCP-friendly describes coexistence with TCP traffic.

**Sources:** Chiu and Jain, *Analysis of the Increase/Decrease Algorithms for Congestion Avoidance in Computer Networks* (1989); RFC 5681; RFC 6356.

---

## Q266. Why does AIMD converge towards fairness? Give the intuition (the Chiu-Jain phase plot) and say what happens if two flows use different increase parameters.

### 1. The two-flow phase plot

Consider two competing flows sharing a bottleneck.

- Horizontal axis: rate or congestion window of Flow 1, $x_1$.
- Vertical axis: rate or congestion window of Flow 2, $x_2$.

Two important lines are:

**Efficiency line:**

$$
x_1+x_2=C
$$

Here, $C$ is the bottleneck capacity. Points on this line represent full utilization in the simplified model.

**Fairness line:**

$$
x_1=x_2
$$

Points on this line represent equal sharing.

The intersection of these lines is the ideal point:

$$
x_1=x_2=\frac{C}{2}
$$

### 2. What additive increase does

With additive increase, both flows increase their rates by approximately the same absolute amount.

$$
x_1' = x_1+a
$$

$$
x_2' = x_2+a
$$

In the phase plot, this moves the operating point diagonally, parallel to the fairness line.

Both flows increase their rates, improving utilization while maintaining the difference between their rates in the simplified model.

### 3. What multiplicative decrease does

When congestion is detected, both flows reduce their rates by a multiplicative factor:

$$
x_1'=\beta x_1
$$

$$
x_2'=\beta x_2
$$

where $0<\beta<1$.

Geometrically, the operating point moves towards the origin along a line connecting the current point to the origin.

This reduces the total offered load while preserving the ratio between the two flows.

### 4. Why does AIMD converge towards fairness?

The combination of additive increase and multiplicative decrease creates a control process that moves the system towards efficient and fair sharing under the assumptions of the model.

- Additive increase gradually raises utilization.
- Multiplicative decrease responds to congestion.
- Repeated congestion cycles move the operating point towards the intersection of the efficiency and fairness boundaries.

Chiu and Jain mathematically analyse the conditions under which increase/decrease algorithms converge towards efficiency and fairness.

This is a simplified model. Real TCP behaviour also depends on RTT, loss detection, delayed acknowledgements, competing traffic and bottleneck structure.

### 5. What if two flows use different increase parameters?

Suppose:

$$
x_1'=x_1+a_1
$$

$$
x_2'=x_2+a_2
$$

If $a_1>a_2$, Flow 1 increases its rate faster during congestion avoidance.

Consequently, it can obtain a larger share over repeated congestion cycles.

If their multiplicative decrease factors also differ, their relative aggressiveness changes further.

Thus, equal sharing is not guaranteed when flows use different AIMD parameters.

A second important factor is RTT: even if two TCP flows use the same increase rule per RTT, the flow with a shorter RTT may complete more congestion-avoidance cycles per second.

**Key takeaway:** AIMD combines gradual probing with multiplicative backoff. Its fairness result depends on comparable control parameters and the assumptions of the model; it is not a universal guarantee of equal bandwidth.

**Source:** Chiu and Jain (1989), *Analysis of the Increase/Decrease Algorithms for Congestion Avoidance in Computer Networks*.

---

## Q267. What is RTT unfairness, and why do short-RTT flows get more bandwidth? What does it mean when the subflows of one connection have very different RTTs?

### 1. What is RTT unfairness?

RTT unfairness occurs when flows competing for the same bottleneck receive different bandwidth shares partly because they have different round-trip times.

In traditional TCP congestion avoidance, the congestion window increases approximately by one MSS per RTT.

A flow with a shorter RTT completes more feedback cycles per second. It can therefore increase its congestion window more frequently.

### 2. Why do short-RTT flows often get more bandwidth?

Consider two flows sharing a bottleneck:

- Flow A: RTT = 20 ms.
- Flow B: RTT = 100 ms.

If both increase their congestion windows by approximately one MSS per RTT, Flow A gets five increase opportunities for every one increase opportunity of Flow B.

This can allow Flow A to become more aggressive and obtain a larger bandwidth share.

This is a simplified explanation. Actual throughput depends on congestion control, loss rate, bottleneck conditions and the relationship between congestion window and RTT.

### 3. What happens when subflows of one MPTCP connection have very different RTTs?

An MPTCP connection can have multiple subflows with different RTTs.

For example:

- Wi-Fi subflow: RTT = 20 ms.
- Cellular subflow: RTT = 100 ms.

If congestion control is not appropriately coupled, the short-RTT subflow may grow faster and carry a disproportionately large share of the traffic.

This can cause:

- Unequal distribution across subflows.
- Increased reordering at the receiver.
- Delayed delivery of data that is waiting for a slower subflow.
- Reduced benefit from using the slower path.
- More complicated scheduling decisions.

Coupled congestion control and multipath scheduling address different parts of this problem: congestion control determines how aggressively each path may send, while scheduling determines which data should be sent on which path.

**Key takeaway:** RTT differences can create unfairness even when flows use the same TCP congestion-control algorithm. In multipath transport, different subflow RTTs also affect scheduling and reordering.

**Source:** RFC 5681; RFC 6356.

---

## Q268. What is resource pooling in the multipath context? How does coupled congestion control try to realise it?

### 1. Definition

**Resource pooling** is the idea that multiple network paths should behave, as far as possible, like a shared pool of resources rather than completely independent links.

The goal is to use available capacity efficiently and shift traffic away from congested paths towards less congested paths.

For example, suppose an MPTCP connection has:

- Path A: 10 Mbps available capacity, currently congested.
- Path B: 20 Mbps available capacity, relatively uncongested.

A resource-pooling approach should encourage the connection to make greater use of Path B rather than continuing to overload Path A.

### 2. Why is it useful?

Without resource pooling, a multipath connection might:

- Overuse one path while another has spare capacity.
- React independently to congestion on each path.
- Compete unfairly with other TCP flows.
- Fail to benefit from the combined resources of multiple paths.

Resource pooling aims to improve robustness and aggregate performance.

### 3. How does coupled congestion control help?

In uncoupled congestion control, each subflow runs its own congestion-control algorithm independently.

Coupled congestion control coordinates the congestion windows of the subflows.

For MPTCP, Linked Increases (LIA) is a well-known example. It adjusts the increase of each subflow based on the congestion window of the entire multipath connection.

The controller therefore considers both:

- The state of the individual subflow.
- The aggregate state of the MPTCP connection.

This prevents every subflow from behaving as if it were an unrelated TCP connection.

### 4. Important distinction

Resource pooling does not mean that all paths become physically identical or that their bandwidth is always perfectly combined.

Different paths may have:

- Different RTTs.
- Different bottlenecks.
- Different loss rates.
- Different capacities.
- Different access-network characteristics.

Coupled congestion control attempts to coordinate their use while respecting fairness and congestion.

**Key takeaway:** Resource pooling is the objective of using multiple paths as a coordinated resource pool. Coupled congestion control is one mechanism for moving towards that objective.

**Source:** RFC 6356, Sections 1 and 5.

---

## Q269. State the three design goals of coupled congestion control in RFC 6356: no worse than the best single path, no harm to single-path flows, balance congestion. Show with an example how two of them conflict.

RFC 6356 identifies three goals for multipath congestion control.

### Goal 1: Improve throughput

A multipath connection should perform at least as well as a single-path connection using the best available path.

In other words, using multiple paths should not make the connection perform worse than using its best individual path.

### Goal 2: Do no harm

A multipath connection should not take more capacity from a shared network resource than a single TCP flow would take if it used only one of the paths.

This prevents one MPTCP connection from unfairly taking multiple shares of a shared bottleneck.

### Goal 3: Balance congestion

The connection should move as much traffic as possible away from its most congested paths, subject to satisfying the first two goals.

This supports resource pooling.

### Example of conflict

Suppose an MPTCP connection has two subflows:

- Subflow A uses a shared bottleneck with an ordinary TCP flow.
- Subflow B uses a separate path with spare capacity.

If the MPTCP connection independently increases both subflows, it may obtain more bandwidth than a single TCP flow at the shared bottleneck.

This helps improve aggregate throughput (Goal 1), but violates the do-no-harm requirement (Goal 2).

Now suppose the controller reduces Subflow A's aggressiveness to protect the competing TCP flow.

This protects fairness, but it may prevent the MPTCP connection from using all available capacity on A, even when B is congested or has insufficient capacity.

The controller must therefore balance throughput, fairness and congestion distribution.

### How does LIA address these goals?

LIA couples the additive increase of subflows.

Its increase rule uses a parameter $\alpha$, which depends on the congestion windows and RTTs of all subflows.

For subflow $i$, RFC 6356 specifies an increase of the form:

$$
\Delta cwnd_i =
\min\left(
\frac{\alpha \cdot bytes\_acked \cdot MSS_i}{cwnd_{total}},
\frac{bytes\_acked \cdot MSS_i}{cwnd_i}
\right)
$$

where:

$$
cwnd_{total}=\sum_i cwnd_i
$$

The first term couples the increase across the multipath connection. The second term prevents a subflow from being more aggressive than a comparable TCP flow.

The exact implementation must follow the RFC's byte/packet and acknowledgement accounting rules.

**Key takeaway:** RFC 6356 defines throughput improvement, do-no-harm and congestion balancing. These goals can conflict, so a practical controller must make trade-offs rather than maximise aggregate throughput without considering fairness.

**Source:** RFC 6356, *Coupled Congestion Control for Multipath Transport Protocols*.

---

## Q270. What is flappiness, and why do fully coupled controllers show it? What did LIA give up to avoid it?

### 1. What is flappiness?

Flappiness is undesirable oscillation in the traffic distribution across paths.

A controller may repeatedly shift traffic between subflows:

1. It sends more traffic on Path A.
2. Path A becomes congested.
3. It shifts traffic towards Path B.
4. Path B becomes congested or appears preferable.
5. It shifts traffic back towards Path A.

This repeated switching can cause unstable path utilisation and fluctuating performance.

### 2. Why can fully coupled controllers exhibit it?

A fully coupled controller strongly coordinates the congestion windows of all subflows.

The increase or decrease of one subflow can influence the behaviour of the others.

This can create strong interactions between paths, especially when their RTTs and congestion conditions differ.

If the controller reacts aggressively to changing path conditions, traffic may repeatedly move between paths rather than settling into a stable distribution.

The result can be oscillatory behaviour.

### 3. What did LIA give up?

LIA uses a compromise between independent TCP behaviour and fully coupled control.

It couples the additive increase but retains the normal TCP-style congestion response on a subflow when congestion is detected.

This avoids some of the instability associated with more aggressive coupling.

The trade-off is that LIA does not achieve every theoretically desirable property of a fully coupled controller. In particular, it is not Pareto-optimal in the sense discussed by later multipath congestion-control research.

### 4. Why does this matter?

A controller should not only achieve high throughput in a static experiment. It should also behave stably when:

- RTTs change.
- One path becomes congested.
- A path temporarily loses capacity.
- A mobile device changes networks.
- Multiple subflows experience different loss conditions.

**Key takeaway:** Flappiness refers to unstable switching or oscillation in path usage. LIA is a practical compromise that avoids some instability by coupling increases without fully coupling every congestion response.

**Source:** RFC 6356; Khalili et al., *MPTCP Is Not Pareto-Optimal: Performance Issues and a Possible Solution* (NSDI 2012).

---

## Q271. What does it mean that LIA is not Pareto-optimal, and what did OLIA do about it?

### 1. What is Pareto optimality?

An allocation is Pareto-optimal if there is no alternative feasible allocation that improves at least one participant's performance without making another participant worse off.

In the multipath congestion-control context, the objective is to find a suitable distribution of traffic across subflows while respecting network congestion and fairness constraints.

### 2. Why was LIA criticised?

LIA was designed as a practical coupled congestion-control algorithm. However, its allocation decisions do not always achieve a Pareto-optimal operating point.

This means that in some network conditions, another feasible allocation could improve the performance of a multipath connection without harming other flows.

The problem is not that LIA always performs poorly. Rather, its design can leave performance improvements unrealised in certain topologies and path conditions.

### 3. What did OLIA change?

**Opportunistic Linked-Increases Algorithm (OLIA)** was proposed to address limitations of LIA.

OLIA uses information about the congestion windows and RTTs of the subflows, along with information about which subflows are currently more useful or less congested.

Its increase rule is designed to:

- Preserve the coupled nature of congestion control.
- Maintain TCP-friendliness.
- Improve responsiveness to changing network conditions.
- Achieve Pareto improvements in cases where LIA's allocation is suboptimal.

OLIA adds an opportunistic component to the increase decisions rather than relying only on LIA's original linked-increase rule.

### 4. Important distinction

OLIA is not simply a scheduler.

- A **scheduler** decides which data should be transmitted over which subflow.
- A **congestion controller** decides how much a subflow is allowed to send.

OLIA changes congestion-control behaviour, not the basic role of the multipath scheduler.

**Key takeaway:** LIA is a practical coupled controller but is not always Pareto-optimal. OLIA was designed to improve the allocation by making opportunistic, coupled increase decisions while retaining fairness objectives.

**Source:** Khalili et al., *MPTCP Is Not Pareto-Optimal: Performance Issues and a Possible Solution*, USENIX NSDI 2012. The precise Pareto-optimality argument should be understood in the paper's defined network model and assumptions.

---

## Q272. Why is detecting a shared bottleneck hard? Which signals do detection schemes use (delay and loss correlation, RFC 8382), and what would you do differently if you knew the paths were disjoint?

### 1. What is a shared bottleneck?

Two paths have a shared bottleneck when their traffic competes for capacity at the same constrained network resource.

For example:

- Path A: device → Wi-Fi router → ISP link → server.
- Path B: device → cellular network → mobile core → ISP link → server.

These paths may be physically different near the sender but could still share a congested router or upstream link.

### 2. Why is detection difficult?

The sender usually does not know the complete internal route taken by packets.

It cannot directly see:

- Every router along the path.
- The capacity of every link.
- The queue occupancy of intermediate routers.
- Whether two paths share an upstream bottleneck.

Even two paths with different RTTs may share a bottleneck. Conversely, two paths with similar RTTs may be completely disjoint.

Therefore, shared-bottleneck detection must infer the relationship from end-to-end measurements.

### 3. Signals used for detection

**A. Delay correlation**

If two flows share a congested queue, increases in queueing delay may affect both flows.

If their delay variations are correlated over time, that can indicate a shared bottleneck.

However, end-to-end delay contains noise from all devices along each path. Different base delays also make direct comparison difficult.

**B. Packet-loss correlation**

If congestion at a shared bottleneck causes packet drops, losses may occur around similar periods on both paths.

Correlated loss can be useful evidence, but loss events may be rare or caused by unrelated links.

**C. Delay distribution and path lag**

RFC 8382 describes a measurement-based shared-bottleneck detection mechanism for RTP media.

It considers statistics such as:

- Delay measurements.
- Delay skewness.
- Delay variability.
- Delay oscillation.
- Packet loss.
- Differences in path delay characteristics.

The mechanism groups flows with similar statistical behaviour.

An important detail: RFC 8382 is an Experimental RFC for shared-bottleneck detection in RTP media. It is useful as a reference for measurement-based detection, but it is not itself the MPTCP congestion-control specification.

**D. ECN**

Explicit Congestion Notification can provide additional congestion information when supported by the network and transport.

Correlated ECN marking can be useful evidence that flows are experiencing congestion at a common resource.

### 4. What if the paths are known to be disjoint?

If the paths are genuinely disjoint, they do not compete at a common bottleneck along those paths.

A controller can therefore make greater use of their independent capacities, subject to the congestion-control algorithm's overall fairness policy and any other shared resources elsewhere in the network.

However, knowing that the paths are disjoint does not mean that each subflow should be allowed to send without congestion control.

The controller still needs to:

- Respond to congestion on each individual path.
- Avoid overwhelming other traffic.
- Adapt to changes in path capacity.
- Account for the possibility that paths later converge at a shared resource.

### 5. Practical experiment

To investigate shared-bottleneck behaviour, compare two controlled scenarios:

1. Two subflows sharing one configured bottleneck.
2. Two subflows using separate bottlenecks.

Measure throughput, RTT, loss, congestion-window behaviour and fairness against a competing single-path TCP flow.

**Key takeaway:** Shared-bottleneck detection is difficult because endpoints cannot directly observe network topology. Delay, loss and ECN patterns provide indirect evidence. If paths are known to be disjoint, there is more opportunity to exploit their independent capacity, but congestion control remains necessary.

**Source:** RFC 8382, *Shared Bottleneck Detection for Coupled Congestion Control for RTP Media* (2018); RFC 6356.

---

## Q273. What does BBR assume about the network, and what happens when two BBR subflows share a bottleneck? Why is coupling a model-based controller harder than coupling a loss-based one?

### 1. What is BBR?

BBR stands for **Bottleneck Bandwidth and Round-trip propagation time**.

It is a model-based congestion-control algorithm.

Rather than treating packet loss as the primary indication of congestion, BBR estimates two important properties:

- **Bottleneck bandwidth (BtlBw):** the delivery rate supported by the bottleneck.
- **Round-trip propagation time (RTprop):** the minimum or baseline RTT, used to estimate the path's propagation delay without persistent queueing.

BBR uses these estimates to control its sending rate and the amount of data in flight.

### 2. What does BBR assume or estimate?

BBR attempts to model the path using delivery-rate and RTT measurements.

Its basic model assumes that the path has a bottleneck link with a measurable delivery rate and a propagation delay.

It periodically probes the path to update these estimates.

This is different from traditional loss-based congestion control, which typically increases its sending rate until congestion is indicated by loss or ECN and then reduces its congestion window.

### 3. What happens when two BBR subflows share a bottleneck?

Suppose two BBR subflows belonging to one multipath connection use the same bottleneck.

Each subflow may independently estimate:

- The bottleneck delivery rate.
- The propagation RTT.
- The amount of data in flight.

If both controllers behave independently, they may each attempt to use the bottleneck capacity.

This can result in:

- Competition between the subflows.
- Excessive aggregate sending.
- Unnecessary queueing.
- Unfairness towards other flows.
- Complicated interactions between their probing cycles.

The exact outcome depends on the BBR version, implementation, network conditions and whether any multipath coupling mechanism is present.

It is therefore incorrect to claim that all BBR subflows always obtain twice the bandwidth or that they always produce a particular queueing pattern.

### 4. Why is coupling model-based congestion control harder?

For a loss-based algorithm such as Reno, coupling can be designed around relatively direct congestion-window increase and decrease rules.

The controller can coordinate how much each subflow increases its window and how it reacts to congestion.

A model-based controller such as BBR maintains estimates of network properties.

Coupling it requires decisions about:

- Whether subflows should share a bottleneck-bandwidth estimate.
- Whether their propagation RTT estimates should remain independent.
- How probing should be coordinated.
- How to distinguish shared congestion from independent path limitations.
- How to avoid one subflow's measurements corrupting another's model.

The controller must coordinate both the sending behaviour and the underlying path models.

### 5. Relevance to MPTCP versus MP-QUIC

Do not assume that MPTCP and MP-QUIC necessarily use the same congestion-control algorithm.

The congestion-control algorithm is an implementation choice and must be identified for the specific implementation and experiment.

For a fair comparison, record:

- The congestion-control algorithm used.
- Whether it is loss-based or model-based.
- Whether it is coupled across subflows or paths.
- Its implementation and version.
- Whether the two paths share a bottleneck.

**Key takeaway:** BBR estimates bottleneck bandwidth and propagation RTT. Coupling multiple BBR paths is challenging because the controller must coordinate both path measurements and sending behaviour, not merely combine congestion-window updates.

**Sources:** BBR technical papers and implementation documentation; RFC 6356 for the contrasting LIA approach.

---

## Q274. Why is multipath scheduling hard? Think about heterogeneous paths and delayed feedback. For two paths with rates $r_1$ and $r_2$ and delays $d_1$ and $d_2$, what would an ideal schedule look like for a bulk transfer, and what for a message with a deadline?

### 1. What is multipath scheduling?

A multipath scheduler decides which data should be sent over which available subflow or path.

In MPTCP, the scheduler operates at the sender and chooses a subflow for transmitting data.

In a multipath QUIC design, scheduling decisions are similarly needed to distribute application data across paths, although the precise mechanism depends on the implementation and draft design.

### 2. Why is it difficult?

Paths are heterogeneous: they can have different rates, RTTs, loss rates, congestion levels and available buffers.

For example:

| Property | Path 1 | Path 2 |
|---|---:|---:|
| Rate | 20 Mbps | 5 Mbps |
| RTT | 20 ms | 100 ms |
| Loss | Low | Higher |
| Queueing | Low | Variable |

A scheduler must decide whether to:

- Use the fastest path.
- Use the lowest-RTT path.
- Distribute traffic across both.
- Avoid sending data on a congested path.
- Send urgent data on a path likely to deliver it before a deadline.

It also receives delayed feedback. By the time a new RTT or delivery-rate measurement is available, network conditions may already have changed.

### 3. Ideal schedule for a bulk transfer

For a large bulk transfer, the objective is usually to maximise aggregate goodput and minimise completion time.

If the paths are independent, stable and have sufficient capacity, an ideal long-term allocation is approximately proportional to their usable rates:

$$
\frac{D_1}{D_2}\approx\frac{r_1}{r_2}
$$

where:

- $D_1,D_2$ are the amounts of data assigned to the paths.
- $r_1,r_2$ are their usable delivery rates.

For example, if:

$$
r_1=20\text{ Mbps},\quad r_2=5\text{ Mbps}
$$

then a simple rate-proportional allocation is:

$$
D_1:D_2=4:1
$$

This is a long-term approximation, not a complete scheduling algorithm. The scheduler must also consider RTT, loss, congestion, reordering, buffers and the receiver's ability to process arriving data.

### 4. Ideal schedule for a deadline-sensitive message

For a message with a deadline, the objective changes.

The scheduler should favour the path that is most likely to deliver the message before the deadline.

A simplified expected completion-time estimate is:

$$
T_i \approx d_i+\frac{S}{r_i}
$$

where:

- $d_i$ represents the relevant path delay.
- $S$ is the message size.
- $r_i$ is the usable delivery rate.

For a small message, the path with the lower RTT may be preferable even if its bandwidth is lower.

For a larger message, a higher-rate path may be preferable despite a longer RTT.

If reliability is critical and the application permits duplication, the sender could send redundant copies on multiple paths, but this consumes additional bandwidth.

### 5. Main scheduling trade-off

A throughput-oriented scheduler may spread data across paths to maximise aggregate capacity.

A latency-oriented scheduler may concentrate urgent data on the path with the best expected delivery time.

These goals can conflict.

**Key takeaway:** Bulk transfers generally benefit from rate-aware distribution, while deadline-sensitive traffic should be scheduled according to expected delivery time and deadline risk.

---

## Q275. Distinguish send-buffer blocking from receive-buffer blocking. Which one does each protocol's scheduler worry about, and why?

### 1. Send-buffer blocking

Send-buffer blocking occurs when the sender cannot place more data into the transport's sending buffer because the buffer is full or the application has not supplied data.

For a multipath sender, this can prevent a subflow from transmitting even when the network path itself has available capacity.

Possible causes include:

- Insufficient send-buffer space.
- Application not writing data quickly enough.
- Data waiting for acknowledgement or retransmission.
- Limits imposed by the transport implementation.

### 2. Receive-buffer blocking

Receive-buffer blocking occurs when the receiver cannot accept more data because its receive buffer is full or its advertised receive window has become restrictive.

In TCP, the receiver communicates its available receive-window capacity through the advertised window.

In MPTCP, the connection-level data-level receive-window mechanism also matters because data arriving on different subflows must be assembled into the connection's ordered byte stream.

### 3. Why does multipath make this complicated?

Suppose an MPTCP connection has two subflows:

- Subflow A delivers data quickly.
- Subflow B delivers earlier sequence data slowly.

Data from A may arrive before missing data from B.

The receiver may need to retain out-of-order data while waiting for the missing earlier data.

This can consume receive-buffer space and contribute to receive-window pressure.

The sender must therefore consider not only individual path capacity but also the state of the connection-level receive buffer and the amount of data already in flight.

### 4. Which blocking should a scheduler worry about?

A multipath scheduler must consider both.

**Send-side considerations:**

- Is there data available to send?
- Is the send buffer full?
- Can the selected subflow accept more data?
- Is the congestion window or receiver window limiting transmission?

**Receive-side considerations:**

- Is the receiver able to accept more data?
- Is the connection-level receive window limiting transmission?
- Is out-of-order data consuming buffer capacity?
- Is one path causing data to arrive too late for in-order delivery?

The exact buffer and blocking mechanisms differ between MPTCP and QUIC implementations.

### 5. Important distinction

Congestion-window blocking, receiver-window blocking and application-limited sending are not the same thing.

A path may have spare network capacity but still fail to send because a transport-level or application-level limit is preventing it.

**Key takeaway:** Send-buffer blocking is a sender-side resource limitation; receive-buffer blocking is a receiver-side capacity limitation. A multipath scheduler must account for both because data is distributed across paths but ultimately belongs to one connection.

---

## Q276. A measured RTT includes queueing delay. Why does that make lowest-RTT-first a poor heuristic when buffers are large, and how stale can the estimate be when the scheduler acts on it?

### 1. What does measured RTT contain?

A measured round-trip time can be represented approximately as:

$$
RTT = RTT_{propagation}+RTT_{queueing}+RTT_{processing}
$$

where:

- Propagation delay is caused by signal travel.
- Queueing delay is time spent waiting in network buffers.
- Processing delay is time spent handling packets at intermediate devices and endpoints.

Therefore, measured RTT is not a pure measurement of the physical distance or baseline latency of a path.

### 2. Why can lowest-RTT-first be misleading?

Suppose:

- Path A has a baseline RTT of 20 ms.
- Path B has a baseline RTT of 50 ms.

Initially, Path A appears better.

However, if Path A develops a large queue, its measured RTT may increase to 120 ms.

Path B may still have a measured RTT of 55 ms.

A scheduler using recent RTT measurements should now prefer B for latency-sensitive data.

The problem becomes more serious when buffers are large. A large buffer can hold substantial queued data, causing measured RTT to increase significantly without immediately producing packet loss.

A path that previously had the lowest RTT may therefore become the slowest path for newly scheduled data.

### 3. What is bufferbloat?

Bufferbloat refers to excessive queueing delay caused by large network buffers.

The network may continue delivering packets without dropping them, but packets spend a long time waiting in queues.

This increases latency and can damage interactive application performance.

### 4. How stale can an RTT estimate be?

There is no universal fixed staleness period.

The estimate can become outdated between the measurement and the scheduler's next decision.

For example:

1. A packet is sent using an RTT estimate of 20 ms.
2. The path becomes congested.
3. Queueing delay increases.
4. The scheduler continues making decisions using the old measurement.
5. It may keep selecting the path even though its current delay is much higher.

The practical staleness depends on:

- RTT measurement frequency.
- Feedback delay.
- Scheduler invocation frequency.
- Queue dynamics.
- Smoothing or filtering of measurements.
- Whether the scheduler uses a recent minimum RTT, smoothed RTT or another metric.

### 5. Better approach

A robust scheduler should not rely only on the smallest measured RTT.

It can combine:

- Smoothed RTT.
- Minimum or baseline RTT.
- Delivery-rate estimates.
- Queueing-delay estimates.
- Loss information.
- In-flight data.
- Retransmission state.
- Application deadlines.

**Key takeaway:** Measured RTT includes queueing delay. With large buffers, a path that looks attractive based on old RTT measurements can become heavily delayed. RTT should be combined with other path measurements.

---

## Q277. How do you tell what limits a connection: congestion window, receive window, send buffer, or the application itself? Which counters or trace fields show each?

A connection may fail to achieve its expected throughput even when the network has available capacity. The cause may be a transport-level or application-level limitation.

### 1. Congestion-window limitation

The congestion window, $cwnd$, limits the amount of unacknowledged data that a sender may have in flight because of network congestion control.

If the congestion window is full, the sender must wait for acknowledgements or a congestion-control update before sending more data.

**What to inspect:**

- Congestion-window size.
- Bytes or packets in flight.
- RTT.
- Loss and retransmission events.
- Congestion-control state.
- Delivery rate.

For Linux MPTCP/TCP, relevant information may be available through TCP diagnostic interfaces, `ss -ti`, kernel tracing and implementation-specific instrumentation.

### 2. Receive-window limitation

The receiver advertises how much additional data it can accept.

If the sender has exhausted the advertised receive window, it cannot send more data even if the congestion window has spare capacity.

**What to inspect:**

- Advertised receive window.
- Scaled receive-window value.
- Zero-window events.
- Window-update packets.
- Sender's usable send window.

A zero-window condition is strong evidence that the receiver is limiting transmission.

### 3. Send-buffer limitation

The sender may be unable to queue more application data because its send buffer is full or constrained.

**What to inspect:**

- Send-buffer capacity and occupancy.
- Socket memory usage.
- Write-queue state.
- Application write blocking.
- Socket send-queue information.

For Linux, `ss -m` can provide socket memory information. The exact fields depend on the kernel and socket implementation.

### 4. Application limitation

The application itself may not provide data quickly enough.

For example:

- A file-reading process may be slow.
- An application may generate data intermittently.
- CPU processing may limit data production.
- The application may intentionally pace writes.

**What to inspect:**

- Application write rate.
- Time spent blocked in socket writes.
- CPU utilisation.
- Application-side production rate.
- Whether the socket is writable but no data is being supplied.

### 5. How to distinguish them

| Limiting factor | Typical indication |
|---|---|
| Congestion window | Data in flight approaches the congestion window |
| Receive window | Advertised receive window is exhausted or becomes zero |
| Send buffer | Sender cannot queue more data; socket memory/queue is constrained |
| Application | Transport could send, but the application does not provide enough data |

### 6. MPTCP and QUIC differences

MPTCP inherits TCP's per-subflow congestion-control and receive-window mechanisms, together with MPTCP-level data handling.

QUIC has its own flow-control mechanisms:

- Connection-level flow control.
- Stream-level flow control.
- Congestion control.
- Application data availability.

For QUIC, inspect connection-level and stream-level flow-control limits, congestion-controller statistics, bytes in flight and qlog events where available.

**Key takeaway:** Never assume low throughput automatically means congestion. Identify whether the connection is congestion-window-limited, receive-window-limited, send-buffer-limited or application-limited before drawing conclusions.

---

## Q278. Latency-oriented and throughput-oriented scheduling pull in different directions. Can one scheduler serve both? What signal from the application would it need?

### 1. Throughput-oriented scheduling

The goal is to maximise the total amount of useful data delivered per unit time.

A throughput-oriented scheduler may:

- Use several paths simultaneously.
- Allocate data according to available delivery rates.
- Keep paths utilised.
- Accept some reordering if aggregate throughput improves.

This is useful for large file transfers and bulk downloads.

### 2. Latency-oriented scheduling

The goal is to deliver data as quickly as possible, particularly when the data is time-sensitive.

A latency-oriented scheduler may:

- Prefer the path with the lowest expected completion time.
- Avoid paths with large queueing delays.
- Prioritise urgent data.
- Use redundant transmission if the application permits it.

This is useful for interactive applications, voice and real-time communication.

### 3. Can one scheduler serve both?

Yes, but it needs to adapt its decisions according to the application's requirements.

A single fixed policy is unlikely to be optimal for both bulk transfers and deadline-sensitive traffic.

For example:

- A file transfer can tolerate some reordering if it improves aggregate throughput.
- A real-time voice packet may become useless if it arrives after its playback deadline.

### 4. What application signal is needed?

The scheduler needs information about the application's delivery requirements.

Useful signals include:

- Traffic priority.
- Deadline or expiry time.
- Whether data is reliable or unreliable.
- Whether retransmission is useful.
- Whether redundant transmission is permitted.
- Whether the application values low latency or maximum throughput.

For example, an application could identify a packet as high-priority and deadline-sensitive, allowing the transport to favour a low-latency path.

### 5. Why is this difficult?

Traditional transport APIs often do not provide enough application-level information to make fine-grained scheduling decisions.

The transport may know the available path rates and RTTs but not whether a particular piece of data is:

- A voice frame.
- A video segment.
- A file block.
- An interactive control message.

This limits how effectively it can adapt its scheduling policy.

**Key takeaway:** A single adaptive scheduler can support both objectives, but it needs application-level information such as priority, deadline and reliability requirements.

---

## Q279. What are FEC and network coding, and how can they replace retransmission across paths? Why are they rarely deployed?

### 1. Forward Error Correction (FEC)

**Forward Error Correction** adds redundant information to transmitted data so that the receiver can recover from some packet losses without requesting retransmission.

For example, a sender may transmit:

- 4 original data packets.
- 1 parity packet.

If one original packet is lost, the receiver may reconstruct it using the remaining original packets and the parity packet.

This depends on the FEC code and the number and pattern of losses.

### 2. Network coding

Network coding combines multiple data packets mathematically before transmission.

Instead of simply sending duplicate copies, the sender or intermediate node may transmit coded combinations of packets.

The receiver collects enough independent coded packets to reconstruct the original data.

For example, if packets $A$ and $B$ are encoded, the sender could transmit:

$$
A,\quad B,\quad A\oplus B
$$

If one of the original packets is lost, the receiver may recover it using the other packet and the coded packet.

More advanced network-coding schemes use finite-field arithmetic and combinations of multiple packets.

### 3. How can they help multipath transport?

Suppose a connection uses two paths:

- Path A has low latency but occasional losses.
- Path B has higher latency but is more reliable.

With ordinary retransmission, if a packet is lost on Path A, the sender must detect the loss and retransmit the missing data. The retransmission may arrive significantly later.

With FEC or network coding:

1. The sender transmits original data and redundancy.
2. Redundant information may be sent over another path.
3. The receiver may reconstruct missing data without waiting for a retransmission.
4. This can reduce recovery delay.

This is particularly useful when a lost packet would otherwise have to be retransmitted over a high-RTT path.

### 4. Why are FEC and network coding not universally deployed?

**A. Bandwidth overhead**

Redundancy consumes additional bandwidth even when no packet is lost.

**B. Computational overhead**

Encoding and decoding require processing resources.

**C. Choosing the right redundancy level**

Too little redundancy fails to recover losses. Too much wastes bandwidth.

**D. Variable network conditions**

Loss rates can change rapidly, making it difficult to choose an appropriate FEC rate.

**E. Retransmission may be sufficient**

For reliable bulk transfers, retransmission is often simpler and more bandwidth-efficient when latency is not critical.

**F. Application requirements differ**

Real-time media may benefit more from FEC because late retransmissions can be useless. File transfers usually require complete reliable delivery and can tolerate retransmission.

**G. Implementation complexity**

FEC and network coding add complexity to transport protocols, receiver logic, buffering and recovery mechanisms.

### 5. Important distinction

FEC does not necessarily eliminate retransmission. It can reduce the number of retransmissions needed or recover selected losses without retransmission.

For reliable transport, retransmission may still be necessary when the available redundancy is insufficient.

**Key takeaway:** FEC adds redundancy to recover losses; network coding sends coded combinations that allow reconstruction. Both can reduce recovery delay across heterogeneous paths, but they introduce bandwidth, computational and implementation overhead.

---

# Part 16 - Consolidated comparison and viva revision

## 1. Important concepts to distinguish

| Concept | What it controls or measures | Main purpose |
|---|---|---|
| Congestion control | Sending rate / congestion window | Prevent congestion and respond to it |
| Coupled congestion control | Relationship between subflows' congestion-control behaviour | Coordinate multipath resource usage |
| Scheduling | Which path carries which data | Decide where data should be sent |
| Max-min fairness | Resource allocation | Protect the least-served flows |
| Proportional fairness | Resource allocation | Balance efficiency and proportional gains |
| Jain's fairness index | Equality of allocations | Quantify fairness |
| Resource pooling | Use of multiple paths | Exploit available capacity across paths |
| Shared-bottleneck detection | Whether paths compete at a common bottleneck | Inform coupling decisions |
| FEC | Redundant error-correction information | Recover losses without waiting for retransmission |
| Network coding | Coded combinations of packets | Recover original data from coded transmissions |

## 2. MPTCP versus MP-QUIC: points to remember

| Topic | MPTCP | MP-QUIC |
|---|---|---|
| Basic transport | TCP extended to use multiple subflows | QUIC extended to use multiple paths, depending on the implementation/draft |
| Congestion control | Per-subflow congestion state; coupled algorithms such as LIA are relevant | Depends on the MP-QUIC implementation and its congestion-control design |
| Scheduling | Selects an MPTCP subflow for data transmission | Selects a path for QUIC data transmission |
| Flow control | TCP receive-window and MPTCP data-level mechanisms | QUIC stream-level and connection-level flow control |
| Reliability | TCP retransmission and MPTCP data-level reliability mechanisms | QUIC reliability for stream data; DATAGRAM frames are not retransmitted by QUIC |
| Reordering | Can arise when data arrives across subflows at different speeds | Can arise when data is distributed across paths, depending on the design and delivery mechanism |

**Important:** Do not claim that every MP-QUIC implementation uses one specific scheduler or congestion-control algorithm. State the exact implementation, version and configuration used in the project.

## 3. How to connect this theory to our experiments

Our project compares MPTCP and MP-QUIC under controlled multipath conditions. The following principles should guide interpretation of experimental results:

1. **Keep congestion control identifiable.** Record which algorithm each implementation uses and whether it is coupled across paths.
2. **Separate congestion control from scheduling.** A throughput difference may result from the congestion controller, scheduler or their interaction.
3. **Use both shared and disjoint bottleneck scenarios.** This helps distinguish resource pooling from competition at a common bottleneck.
4. **Use asymmetric paths.** Vary RTT, bandwidth and loss to observe how scheduling and congestion control respond.
5. **Measure more than throughput.** Record completion time, RTT, loss, retransmissions, fairness and reordering where the implementation exposes them.
6. **Test competing traffic.** Include a single-path TCP flow sharing a bottleneck to investigate whether a multipath connection takes an unfair share.
7. **Repeat experiments.** Use multiple repetitions and report variability instead of relying on one run.
8. **Control the workload.** Compare bulk transfers separately from small or latency-sensitive transfers.
9. **Record implementation details.** Freeze the implementation version/commit and document all relevant settings.

## 4. Primary references and further reading

1. **Chiu, D. and Jain, R. (1989).** *Analysis of the Increase/Decrease Algorithms for Congestion Avoidance in Computer Networks.*  
   https://www.cs.wustl.edu/~jain/papers/cong_av.htm

2. **RFC 5681 - TCP Congestion Control.**  
   https://www.rfc-editor.org/rfc/rfc5681

3. **RFC 6356 - Coupled Congestion Control for Multipath Transport Protocols.**  
   https://www.rfc-editor.org/rfc/rfc6356

4. **Khalili et al. (2012).** *MPTCP Is Not Pareto-Optimal: Performance Issues and a Possible Solution.* USENIX NSDI.  
   https://www.usenix.org/conference/nsdi12/technical-sessions/presentation/khalili

5. **RFC 8382 - Shared Bottleneck Detection for Coupled Congestion Control for RTP Media.**  
   https://www.rfc-editor.org/rfc/rfc8382

6. **RFC 8684 - TCP Extensions for Multipath Operation with Multiple Addresses.**  
   https://www.rfc-editor.org/rfc/rfc8684

7. **BBR congestion control - Google Research.**  
   https://research.google/pubs/bbr-congestion-based-congestion-control/

---

## 5. Final viva checklist

Before marking Part 16 complete, make sure you can explain these without reading the notes:

- [ ] Explain the difference between max-min fairness, proportional fairness and Jain's index.
- [ ] Draw the Chiu-Jain phase plot and explain additive increase and multiplicative decrease.
- [ ] Explain RTT unfairness and why different subflow RTTs matter.
- [ ] Explain resource pooling and why independent subflows can be unfair.
- [ ] State all three RFC 6356 design goals and explain their trade-off.
- [ ] Explain LIA, flappiness and OLIA.
- [ ] Explain why shared-bottleneck detection is difficult and what RFC 8382 measures.
- [ ] Explain BBR's bottleneck-bandwidth and propagation-RTT model.
- [ ] Compare throughput-oriented and latency-oriented scheduling.
- [ ] Distinguish send-buffer blocking from receive-buffer blocking.
- [ ] Explain why lowest-RTT-first can fail when queueing delay is high.
- [ ] Identify congestion-window, receive-window, send-buffer and application limitations.
- [ ] Explain what application information an adaptive scheduler needs.
- [ ] Explain how FEC and network coding can reduce retransmission delay.

**Completion criterion:** Part 16 is ready for team review when all 15 answers are in the notes, the primary references have been checked, and you can explain the phase plot, RFC 6356's three goals, LIA/OLIA and the scheduling trade-offs on a whiteboard.

A few technical cautions to retain when you discuss this with the team\:

- **Q270\:** “Flappiness” is a useful description of unstable path allocation; avoid claiming every fully coupled controller necessarily flaps under every topology.
- **Q272\:** RFC 8382 is specifically an Experimental RFC for RTP-media shared-bottleneck detection. Use it as a reference for the detection signals, not as an MPTCP standard.
- **Q273\:** Do not claim a universal outcome for two BBR subflows sharing a bottleneck. It depends on BBR version, implementation and coupling.
- **Q275-Q277\:** The exact counters and trace fields depend on the Linux MPTCP kernel and TQUIC/MP-QUIC implementation. Record the fields actually available in your test setup rather than claiming every implementation exposes the same counters.

**Next\:** Save this section, then we can verify the technical claims and map the relevant counters to the exact MPTCP and TQUIC versions used in your experiments.

## Prompt:
10/31/2026, 3:16:53 PM

now lets move ahead

## Response:
10/31/2026, 3:16:02 PM · gpt-6

> **Preparing Part 17**
>
> I’m moving ahead with the next assigned section, covering Questions 280–290. I’ll keep the answers paste-ready, technically precise, and consistent with the structure used in Part 16.
>
> **Prepared Part 17**
>
> 
>
> Worked for 4s

According to the original plan, the next section is **Part 17 - Applications and Quality of Experience, Deeper (Q280-Q290)**\. This is your next individual block, following Part 16.

It covers adaptive video streaming, VoIP, file-transfer completion time, Wi-Fi/cellular characteristics, cost and battery-aware multipath, and satellite-terrestrial paths. I’ll keep the same paste-ready format for your Markdown notes.

**document: **

# Part 17 - Applications and Quality of Experience, Deeper (Q280-Q290)

**Owner:** Swamini  
**Scope:** Adaptive video streaming, voice communication, file transfers, heterogeneous wireless networks, energy and cost awareness, and satellite-terrestrial multipath scenarios.

---

## Q280. How do DASH and HLS work (segments, manifest, bitrate ladder, client buffer)? What do throughput-based and buffer-based adaptation do, and how does a second path change the throughput estimate they depend on?

### 1. What are DASH and HLS?

**DASH (Dynamic Adaptive Streaming over HTTP)** and **HLS (HTTP Live Streaming)** are adaptive video-streaming technologies.

They allow a video player to change the quality of the video during playback depending on network conditions and the player's buffer.

Both typically divide video content into smaller pieces called **segments**.

Instead of downloading one complete video file, the player requests segments one after another.

### 2. How does segmentation work?

Suppose a 10-minute video is divided into segments of 4 seconds each.

The player downloads:

- Segment 1: first 4 seconds.
- Segment 2: next 4 seconds.
- Segment 3: next 4 seconds.
- And so on.

The player can request different quality versions of each segment.

For example:

- 360p: 500 Kbps.
- 480p: 1 Mbps.
- 720p: 2.5 Mbps.
- 1080p: 5 Mbps.

These available quality levels form a **bitrate ladder**.

The player chooses which version of the next segment to download.

### 3. What is a manifest?

A manifest describes the available media representations and how to request them.

In DASH, the manifest is generally an MPD (Media Presentation Description).

In HLS, playlists describe the available streams and media segments. A master playlist can point to different quality variants.

The manifest provides information such as:

- Available bitrates and resolutions.
- Segment locations.
- Timing and duration.
- Codec and media information.
- Alternative representations.

The player uses this information to select and download segments.

### 4. What is the client buffer?

The client buffer stores downloaded video segments before they are played.

For example, if the player has downloaded 20 seconds of video ahead of playback, it has approximately 20 seconds of buffered content.

The buffer protects playback against temporary network slowdowns.

If the network becomes slow, the player can continue playing already-buffered content.

If the buffer becomes empty, playback pauses. This is called **rebuffering**.

### 5. Throughput-based adaptation

A throughput-based adaptive bitrate algorithm estimates the available network throughput and chooses a video bitrate that the network is likely to sustain.

For example:

- Estimated throughput: 6 Mbps.
- Available video bitrates: 0.5, 1, 2.5 and 5 Mbps.

The player may select 2.5 Mbps or 5 Mbps depending on its safety margin and buffer state.

The player should not blindly select the highest bitrate equal to the latest throughput measurement because throughput varies over time.

### 6. Buffer-based adaptation

A buffer-based algorithm uses the amount of video already buffered to choose the quality.

- A large buffer indicates that playback has some protection against a temporary slowdown.
- A small buffer indicates that the player should be conservative.
- A nearly empty buffer may require reducing the bitrate to avoid rebuffering.

Some systems combine throughput estimates and buffer occupancy.

### 7. How does a second path change throughput estimation?

Suppose the player has two paths:

- Wi-Fi: 8 Mbps.
- Cellular: 4 Mbps.

A multipath transport may deliver data using both paths.

In an ideal case, aggregate throughput could approach the combined usable capacity:

$$
R_{\text{aggregate}}\approx R_1+R_2
$$

However, the player must estimate the throughput of the actual data delivered to the application, not simply add two independently measured path rates.

Reasons include:

- Different RTTs.
- Different loss rates.
- Different congestion levels.
- Packet reordering.
- Retransmissions.
- Unequal path utilisation.
- Scheduler behaviour.

For example, a segment may be distributed across two paths, but some data may arrive late because one path has a much longer RTT.

The application may therefore receive the complete segment later than expected, even if the sum of the path capacities looks high.

### 8. What should a multipath-aware video player measure?

It should consider:

- Aggregate application goodput.
- Segment download completion time.
- Buffer occupancy.
- Rebuffering events.
- Bitrate changes.
- Path-level delivery rates.
- Delay and loss.
- Data arriving too late to be useful.

**Key takeaway:** DASH and HLS download segmented video using a manifest and multiple quality representations. Throughput-based adaptation uses estimated delivery capacity, while buffer-based adaptation uses playback-buffer occupancy. Multipath can increase aggregate throughput, but the player must account for reordering, unequal delays and actual segment completion time.

---

## Q281. Define startup delay, rebuffering ratio, bitrate switches and average bitrate. Which is most sensitive to path failure, which to reordering and which to random loss?

### 1. Startup delay

Startup delay is the time between the user requesting playback and the video actually beginning.

It may include:

- Initial connection setup.
- Manifest retrieval.
- Segment download.
- Buffer filling.
- Player startup processing.

A long startup delay makes the application feel unresponsive.

### 2. Rebuffering ratio

The rebuffering ratio measures how much playback time is spent stalled because the player has run out of buffered content.

A common definition is:

$$
\text{Rebuffering Ratio}=
\frac{\text{Total rebuffering time}}
{\text{Total playback time}}
$$

A lower value is generally better.

Some studies use slightly different definitions, so the exact formula must be stated when reporting experimental results.

### 3. Bitrate switches

A bitrate switch occurs when the player changes the quality representation used for subsequent video segments.

For example:

$$
1080p \rightarrow 720p \rightarrow 480p
$$

A player may reduce bitrate when network throughput falls and increase it when conditions improve.

Frequent switching can make video quality unstable.

The direction and magnitude of bitrate changes are also important.

### 4. Average bitrate

Average bitrate measures the average video bitrate delivered or played over a period.

A simplified calculation is:

$$
\text{Average Bitrate}=
\frac{\text{Total video data delivered or played}}
{\text{Duration}}
$$

For meaningful QoE evaluation, distinguish the average encoded bitrate of selected segments from the actual network goodput.

### 5. Which metric is sensitive to path failure?

A path failure can immediately reduce the aggregate available capacity.

This can affect:

- Segment download time.
- Startup delay, if failure happens during startup.
- Buffer occupancy.
- Rebuffering.
- Bitrate selection.

**Rebuffering ratio** is often particularly important because a path failure may cause the player to run out of buffered video.

However, the impact depends on how much traffic was carried by the failed path and whether the remaining path has sufficient capacity.

### 6. Which metric is sensitive to reordering?

Reordering can delay complete delivery of a segment or stream data when the receiver must wait for missing earlier data.

This can affect:

- Segment completion time.
- Buffer replenishment.
- Rebuffering.
- Startup delay.

A multipath transport may have high aggregate throughput but still deliver application data later than expected because of reordering and path-delay differences.

### 7. Which metric is sensitive to random loss?

Random loss can reduce effective delivery capacity through retransmissions or recovery mechanisms.

This can increase segment download time and cause the player to reduce bitrate.

The effects depend on the transport and application:

- Reliable video over TCP or QUIC streams may retransmit lost data.
- Late retransmissions can delay segment completion.
- Real-time media may use loss concealment or FEC rather than retransmitting every lost packet.

### 8. Summary

| Metric | What it measures | Important sensitivity |
|---|---|---|
| Startup delay | Time until playback begins | Connection setup, initial download delay and early path failure |
| Rebuffering ratio | Fraction of playback time stalled | Capacity reduction, path failure, late data and insufficient buffer |
| Bitrate switches | Changes in selected video quality | Throughput variation, loss and unstable path estimates |
| Average bitrate | Average selected/delivered video bitrate | Sustained network capacity and adaptation policy |

**Key takeaway:** Path failure can cause a sudden capacity reduction and rebuffering; reordering can delay segment completion; random loss can trigger retransmissions and bitrate reductions. No single QoE metric captures all these effects.

---

## Q282. How do deadlines differ between live and on-demand video, and what does that change about the value of a second path?

### 1. On-demand video

On-demand video is content that has already been recorded and stored.

Examples include:

- Movies.
- Recorded lectures.
- Previously uploaded videos.
- Video-on-demand services.

The viewer can usually tolerate some startup delay and buffering.

The player can download content ahead of playback and maintain a buffer.

If a segment arrives late, it may still be useful as long as it arrives before the player needs to play it.

### 2. Live video

Live video is generated and transmitted while the event is happening.

Examples include:

- Live sports.
- Video conferencing.
- Live broadcasts.
- Interactive streaming.

Live video has tighter deadlines because old content becomes less useful as time passes.

A segment that arrives after its playback deadline may be discarded or skipped.

### 3. Why are deadlines different?

For on-demand video, the player can build a relatively large buffer.

For live video, maintaining a large buffer would increase the delay between the real event and what the viewer sees.

Therefore:

- On-demand streaming can tolerate more buffering.
- Live streaming generally prioritises low end-to-end latency.
- Interactive live video requires even tighter delay control.

### 4. What does a second path provide?

A second path can improve:

- Available aggregate bandwidth.
- Resilience against one path failing.
- Continuity during network changes.
- Delivery reliability when paths have independent failure conditions.

For on-demand video, the second path can be especially useful for increasing download throughput and filling the playback buffer faster.

For live video, the second path can help maintain delivery during congestion or handover, but the scheduler must consider packet deadlines.

### 5. What is the risk?

Suppose:

- Wi-Fi RTT = 20 ms.
- Cellular RTT = 100 ms.

If live-video packets are distributed across both paths, packets sent over cellular may arrive later.

The receiver may need to wait for delayed packets, increasing playback latency.

If packets arrive after their deadlines, the additional path may not improve the user's experience.

### 6. What should a live-video scheduler do?

It should consider:

- Packet deadlines.
- Expected path delay.
- Queueing delay.
- Loss probability.
- Whether retransmission can finish before the deadline.
- Whether redundant transmission is worthwhile.

A packet that is already too late to be useful should not consume resources through unnecessary retransmission.

**Key takeaway:** On-demand video benefits from buffering and higher aggregate throughput. Live video benefits from reliability and path diversity only when data arrives before its deadline. A second path is not automatically useful if it introduces excessive delay or reordering.

---

## Q283. Walk through a VoIP pipeline: codec frame size, packetisation, RTP, the jitter buffer, loss concealment. How does the jitter buffer turn reordering into extra delay or loss?

### 1. What is VoIP?

Voice over Internet Protocol (VoIP) carries voice communication over IP networks.

Unlike file transfers, voice communication is time-sensitive. A packet arriving too late may be useless even if it is eventually delivered correctly.

### 2. Codec and frame generation

The microphone captures audio, and an audio codec converts it into compressed digital data.

Examples include:

- Opus.
- G.711.
- G.729.

The codec processes audio in frames.

For example, an audio codec may generate one frame every 20 ms.

The choice of codec and frame duration affects:

- Bitrate.
- Encoding delay.
- Packetisation.
- Processing requirements.
- Audio quality.

### 3. Packetisation

The encoded audio frames are grouped into packets.

For example, one packet may contain one 20 ms audio frame, or multiple frames may be combined.

Larger packetisation intervals reduce packet-header overhead but increase the amount of audio affected when a packet is lost and can add delay.

### 4. RTP

RTP (Real-time Transport Protocol) carries real-time media information.

An RTP header includes information such as:

- Sequence number.
- Timestamp.
- Payload type.
- Synchronisation source identifier.

The sequence number helps the receiver detect missing and reordered packets.

The timestamp helps the receiver understand the media timing.

RTP is commonly carried over UDP.

RTP itself does not guarantee reliable delivery. It provides information that applications can use to handle timing and loss.

### 5. Jitter buffer

Packets do not necessarily arrive at regular intervals.

A jitter buffer temporarily stores received packets and releases them to the audio decoder at the appropriate playback time.

Its purpose is to smooth out variations in packet arrival time.

For example:

- Packet 1 arrives at 10 ms.
- Packet 2 arrives at 25 ms.
- Packet 3 arrives at 70 ms.

The jitter buffer attempts to deliver audio at a regular playback rate despite the variable arrival times.

### 6. How does reordering affect the jitter buffer?

Suppose packets are generated in this order:

$$
P_1,\ P_2,\ P_3
$$

But they arrive in this order:

$$
P_1,\ P_3,\ P_2
$$

The receiver has received $P_3$, but $P_2$ is missing.

The jitter buffer has two choices:

**Option A: Wait for the missing packet**

It can delay playback until $P_2$ arrives.

This increases the required buffer delay.

**Option B: Continue playback**

If $P_2$ does not arrive before its playback deadline, the receiver may treat it as lost and continue without it.

This can produce an audio gap or require loss concealment.

Therefore, multipath reordering can turn into additional playback delay or effective packet loss.

### 7. Loss concealment

Packet-loss concealment attempts to reduce the audible effect of missing audio packets.

Techniques may include:

- Repeating or extrapolating previous audio.
- Interpolating missing audio.
- Using codec-specific concealment.
- Generating replacement audio based on neighbouring frames.

Concealment does not recover the original packet. It attempts to make the missing audio less noticeable.

**Key takeaway:** VoIP generates encoded audio frames, packetises them, carries them using RTP, and uses a jitter buffer to smooth arrival-time variation. Multipath reordering can force the receiver to wait longer or treat delayed packets as lost.

---

## Q284. What one-way delay budget is commonly quoted for conversational voice, and how much room does it leave for multipath reordering?

### 1. Commonly quoted delay guideline

ITU-T Recommendation G.114 discusses one-way transmission time and its effect on conversational quality.

A commonly quoted guideline is:

- **0-150 ms one-way:** generally acceptable for most conversational applications.
- **150-400 ms one-way:** may be acceptable in some cases, but the impact becomes increasingly noticeable.
- **Above 400 ms one-way:** generally unacceptable for ordinary conversational interaction.

These are planning guidelines, not strict boundaries that guarantee a particular voice quality.

The delay should be considered end-to-end, including:

- Codec processing.
- Packetisation.
- Network transmission.
- Queueing.
- Jitter-buffer delay.
- Decoding and playback.

### 2. How much room is available for multipath reordering?

Suppose the application's target one-way delay is 150 ms.

If codec processing, packetisation and other network delays already consume 100 ms, only about 50 ms remains before reaching that target.

A multipath scheduler must therefore consider how much additional delay can be introduced by sending packets across paths with different RTTs.

For example:

- Path A: low delay.
- Path B: 80 ms more delay than Path A.

If packets are distributed across both paths without deadline awareness, packets sent on B may arrive too late for smooth playback.

### 3. Why is this important?

Multipath can improve resilience and available bandwidth, but it can also increase:

- Packet reordering.
- Jitter-buffer occupancy.
- Playout delay.
- Effective packet loss when packets miss their deadlines.

A voice application may prefer a single stable low-delay path over a higher-throughput multipath combination.

### 4. Practical design implication

For conversational voice, a scheduler should consider:

- One-way delay.
- Expected arrival time.
- Packet deadlines.
- Jitter-buffer capacity.
- Whether retransmission can finish before playback.
- Whether sending redundant packets over another path is worthwhile.

**Key takeaway:** The commonly quoted conversational one-way delay guideline is approximately 150 ms, based on ITU-T G.114. Multipath reordering consumes part of that end-to-end delay budget, so low-delay scheduling matters more than maximising aggregate throughput.

**Source:** ITU-T Recommendation G.114, *One-way transmission time*.

---

## Q285. How is voice quality quantified (E-model, MOS)? Which impairments dominate in a multipath setting?

### 1. Mean Opinion Score (MOS)

MOS is a commonly used measure of perceived voice quality.

It traditionally uses a scale from 1 to 5:

| MOS | General interpretation |
|---:|---|
| 5 | Excellent |
| 4 | Good |
| 3 | Fair |
| 2 | Poor |
| 1 | Bad |

MOS can be obtained through subjective listening tests or estimated using objective models.

It provides a way to compare perceived voice quality across different network conditions.

### 2. E-model

The E-model is an analytical model described in ITU-T Recommendation G.107.

It estimates voice transmission quality using a rating factor called the **R-factor**.

The model considers impairments such as:

- Delay.
- Packet loss.
- Codec distortion.
- Equipment impairment.
- Other transmission impairments.

A simplified relationship between R-factor and MOS is commonly used to estimate perceived quality.

The E-model is useful for network planning and evaluation, but it is not a direct measurement of what every individual listener will experience.

### 3. Important multipath impairments

**A. Delay**

Different paths can have different delays. A slower path may cause packets to arrive after their intended playback time.

**B. Jitter**

Variable path delay can cause irregular packet arrival times.

**C. Reordering**

Packets may arrive in a different order from the order in which they were sent.

**D. Packet loss**

Loss can occur independently on each path or because of congestion and failures.

**E. Late packet arrival**

A packet may eventually arrive but still be unusable because it missed the playback deadline.

**F. Handover interruption**

When a mobile device changes access networks, a path may temporarily become unavailable.

### 4. Which impairments matter most?

For interactive voice, delay and jitter are particularly important because they affect conversation timing and playback.

Packet loss and late arrivals can cause audible gaps or distortion.

The relative importance depends on:

- Codec.
- Packetisation interval.
- Jitter-buffer strategy.
- Loss concealment.
- Application latency requirements.
- Network conditions.

### 5. What should our experiments measure?

For VoIP-related evaluation, useful metrics include:

- One-way delay.
- RTT, where one-way measurement is unavailable.
- Packet loss.
- Jitter.
- Reordering.
- Late packet rate.
- MOS or an appropriate quality estimate.

**Key takeaway:** MOS estimates perceived voice quality, while the E-model uses transmission impairments to calculate an R-factor and estimate quality. In multipath voice communication, delay, jitter, reordering, loss and late packet arrival are particularly important.

**Sources:** ITU-T G.107, *The E-model: A computational model for use in transmission planning*; ITU-T G.114.

---

## Q286. Why is VoIP normally carried over UDP and RTP and not TCP? What changes if it is carried over QUIC streams, or over QUIC DATAGRAM frames?

### 1. Why UDP and RTP are commonly used

VoIP is time-sensitive.

A voice packet that arrives after its playback deadline may no longer be useful.

UDP is commonly used because it does not impose TCP's reliable, in-order byte-stream delivery.

The application can decide how to handle:

- Packet loss.
- Reordering.
- Late arrivals.
- Retransmission.
- Loss concealment.

RTP adds media-specific information such as sequence numbers and timestamps.

### 2. Why can TCP be problematic for VoIP?

TCP provides reliable, in-order byte-stream delivery.

If a TCP segment is lost, later data may be held until the missing data is retransmitted and received.

This is known as **head-of-line blocking**.

For a voice stream, a delayed old audio frame may be less useful than newer audio frames that could already have been played.

TCP retransmission can therefore increase latency.

This does not mean voice can never use TCP. It means that reliable in-order delivery is often a poor fit for strict real-time media.

### 3. What if voice is carried over QUIC streams?

QUIC streams provide reliable, ordered delivery within each stream.

If a voice application sends audio over a QUIC stream, lost stream data must be recovered before the missing bytes can be delivered in order.

This can introduce delay for time-sensitive audio.

QUIC avoids TCP's transport-level head-of-line blocking between independent streams, but it does not remove ordered-delivery blocking within an individual stream.

Therefore, QUIC streams are not automatically equivalent to UDP/RTP for real-time voice.

### 4. What if voice is carried over QUIC DATAGRAM frames?

QUIC DATAGRAM frames provide unreliable datagram delivery within a QUIC connection.

They are not retransmitted by QUIC as reliable stream data.

This is more suitable for time-sensitive data because the application can decide how to handle missing or late packets.

QUIC still provides connection-level congestion control and security.

The application must provide or use appropriate media information and mechanisms for:

- Sequence tracking.
- Timestamps.
- Jitter handling.
- Loss concealment.
- Media synchronisation.

### 5. Comparison

| Property | UDP + RTP | QUIC streams | QUIC DATAGRAM |
|---|---|---|---|
| Delivery | Unreliable datagrams | Reliable, ordered stream data | Unreliable datagrams |
| Retransmission | Application-dependent | QUIC retransmits lost stream data | Not retransmitted by QUIC |
| Ordering | Application handles ordering | Ordered within each stream | Application handles ordering |
| Congestion control | Depends on transport/application design | QUIC congestion control | QUIC congestion control |
| Typical fit | Real-time voice/media | Reliable application data | Time-sensitive datagram traffic |

### 6. Important limitation

QUIC DATAGRAM does not automatically provide RTP functionality.

The application still needs appropriate media framing, timestamps, sequence information and playback logic.

**Key takeaway:** UDP/RTP is common for VoIP because it allows the application to manage late and missing packets. QUIC streams provide reliable ordered delivery, while QUIC DATAGRAM offers unreliable datagram delivery that is more suitable for real-time media.

**Sources:** RFC 3550 (RTP); RFC 9000 (QUIC); RFC 9221 (QUIC DATAGRAM).

---

## Q287. For a file transfer, how should data be split over two paths of rates $r_1$ and $r_2$? What if rates are unknown/changing, and why is a completion-time metric better than throughput here?

### 1. Basic rate-proportional splitting

Suppose a file of size $S$ is to be transferred over two independent paths.

Their usable delivery rates are:

$$
r_1,\quad r_2
$$

If the rates are stable and both paths can be used simultaneously, an ideal long-term split is proportional to their rates:

$$
D_1:D_2=r_1:r_2
$$

where:

$$
D_1+D_2=S
$$

Therefore:

$$
D_1=S\frac{r_1}{r_1+r_2}
$$

$$
D_2=S\frac{r_2}{r_1+r_2}
$$

### 2. Example

Suppose:

- Path 1: 20 Mbps.
- Path 2: 10 Mbps.
- File size: 300 MB.

The rate ratio is:

$$
20:10=2:1
$$

Therefore, the idealised split is:

- Path 1: 200 MB.
- Path 2: 100 MB.

Both paths would take approximately the same time to transmit their assigned data, assuming the rates remain stable and ignoring protocol overhead.

### 3. What if rates are unknown?

The scheduler can estimate delivery rates using recent observations.

It can monitor:

- Bytes delivered over time.
- Acknowledgement or delivery feedback.
- RTT.
- Loss.
- Retransmissions.
- Congestion-window state.
- Queueing and in-flight data.

It can then update the data allocation as better estimates become available.

### 4. What if rates change?

In mobile networks, path capacity can change because of:

- Wi-Fi interference.
- Cellular signal strength.
- Network congestion.
- Handover.
- Radio scheduling.
- Competing traffic.

A fixed 2:1 allocation may become inefficient if Path 1's rate falls or Path 2's rate increases.

A practical scheduler should adapt its estimates and avoid assigning too much data to a path that has become slow or unreliable.

### 5. Why is completion time better than throughput?

Throughput measures the rate at which data is delivered.

However, the user usually cares about how long the complete file takes to arrive.

Suppose two approaches deliver:

- Approach A: high average throughput initially but leaves a small amount of data on a very slow path.
- Approach B: slightly lower average throughput but finishes all data earlier.

Approach B may provide the better user experience.

The relevant metric is **flow completion time (FCT)**:

$$
FCT=t_{\text{completion}}-t_{\text{start}}
$$

A file is not complete until all required data has arrived and been delivered to the application.

In multipath transport, one slow remaining portion can determine the completion time even when most data has already arrived.

### 6. Other useful metrics

- Aggregate goodput.
- Flow completion time.
- Retransmission count.
- Path utilisation.
- Out-of-order data.
- Fairness against competing traffic.

**Key takeaway:** With stable paths, split data approximately in proportion to usable path rates. With changing paths, continuously update estimates. For complete file transfers, flow completion time is often more meaningful to the user than average throughput alone.

---

## Q288. Characteristics of Wi-Fi and cellular paths (RTT, variability, loss, handover events, energy)? In which mobile scenarios is multipath most valuable?

### 1. Wi-Fi characteristics

Wi-Fi is commonly used for local wireless access.

Its characteristics depend on the access point, interference, signal strength and backhaul.

Typical characteristics include:

- Often low RTT to the local network.
- Potentially high bandwidth.
- Variable throughput due to interference and contention.
- Packet loss due to interference, collisions or congestion.
- Possible sudden degradation when the device moves away from the access point.
- Generally lower additional device energy cost than continuously using cellular, although actual energy depends on the hardware and workload.

### 2. Cellular characteristics

Cellular networks provide mobile wide-area connectivity.

Their characteristics depend on signal quality, radio technology, network load, mobility and operator infrastructure.

Typical characteristics include:

- RTT that may be higher than local Wi-Fi.
- Bandwidth that varies with signal quality and cell load.
- Radio scheduling and resource sharing.
- Handover events when the device moves between cells.
- Variable packet delay and loss.
- Potentially higher energy consumption, particularly when the radio remains active or frequently changes state.

These are typical tendencies, not universal guarantees. Modern cellular networks can provide lower RTT and higher bandwidth than some Wi-Fi connections.

### 3. Comparison

| Property | Wi-Fi | Cellular |
|---|---|---|
| RTT | Often low on a good local network | Depends on radio technology and network path |
| Bandwidth | Can be high but affected by interference | Depends on signal and network load |
| Variability | Interference and contention | Mobility, signal and radio scheduling |
| Loss | Interference, contention and congestion | Radio conditions, handover and congestion |
| Handover | Access-point roaming | Cell-to-cell mobility |
| Energy | Often relatively inexpensive to maintain | Can have significant radio-energy cost |

### 4. When is multipath most valuable?

**A. Wi-Fi degradation**

If Wi-Fi becomes congested or weak, cellular can provide an alternative path.

**B. Wi-Fi coverage gaps**

When a device moves away from the access point, cellular can maintain connectivity.

**C. Cellular handover**

If cellular connectivity is temporarily disrupted during a handover, Wi-Fi may provide continuity.

**D. High-bandwidth downloads**

A device may use both Wi-Fi and cellular to increase aggregate throughput, provided the user permits cellular data usage.

**E. Reliability-sensitive applications**

A second path can reduce dependence on a single access network.

### 5. When may multipath not be useful?

Multipath can introduce:

- Extra energy consumption.
- Cellular data charges.
- Packet reordering.
- More complicated congestion control.
- Additional signalling and connection management.
- No meaningful performance improvement when one path already meets the application's needs.

**Key takeaway:** Wi-Fi and cellular have different performance and energy characteristics. Multipath is especially valuable during mobility, weak coverage, handovers and high-bandwidth transfers, but the benefit must justify extra data and energy costs.

---

## Q289. Cost-aware policies for data caps and battery (cellular as backup, cellular only when Wi-Fi is weak)? What does transport expose so OS/application can decide?

### 1. Why is cost-aware multipath needed?

A device may have multiple network connections, but using all of them simultaneously is not always desirable.

For example:

- Wi-Fi may be unlimited or inexpensive.
- Cellular data may have a monthly data cap.
- Cellular usage may consume more battery.
- Roaming data may be expensive.

Therefore, the system should consider cost and energy, not only throughput.

### 2. Example policies

**Policy A: Cellular as backup**

Use Wi-Fi normally.

Use cellular only when Wi-Fi becomes unavailable or unusable.

Advantages:

- Reduces cellular data usage.
- Reduces unnecessary energy consumption.
- Maintains connectivity during Wi-Fi failure.

**Policy B: Cellular only when Wi-Fi is weak**

Use both paths only when Wi-Fi throughput or quality falls below a threshold.

Advantages:

- Avoids using cellular unnecessarily.
- Provides extra capacity when Wi-Fi cannot meet the application's requirements.

**Policy C: Cellular for critical traffic**

Use Wi-Fi for ordinary downloads but allow cellular for time-sensitive or high-priority traffic.

**Policy D: User-controlled multipath**

Allow users to select whether cellular data can be used for multipath traffic.

### 3. Battery-aware scheduling

The operating system may consider:

- Radio energy consumption.
- Whether the cellular radio is already active.
- Whether Wi-Fi and cellular are both transmitting.
- Expected transfer duration.
- The energy required per delivered byte.
- Whether the application is running in the foreground or background.

Using two paths may improve completion time but consume more energy.

For some workloads, finishing a transfer quickly can reduce total energy. For others, keeping multiple radios active may increase energy consumption.

The result depends on the device and network.

### 4. What information should the transport expose?

The transport should expose useful measurements and controls to the operating system or application.

Potential information includes:

- Per-path RTT.
- Per-path delivery rate.
- Packet loss.
- Congestion state.
- Path availability.
- Bytes sent and received on each path.
- Estimated path quality.
- Path identifiers.
- Data usage per path.
- Connection-level throughput.

The operating system may also provide policy information to the transport:

- Whether cellular usage is permitted.
- Whether a network is metered.
- Whether a path is expensive.
- Whether the battery is low.
- Whether the application is latency-sensitive.
- Whether a particular path should be avoided.

### 5. Why should the application or OS make this decision?

The transport knows network conditions, but it may not know the user's data plan or battery preferences.

The operating system is better positioned to know:

- Network metering.
- User preferences.
- Battery status.
- Roaming state.
- Device power policies.

The application may know whether the transfer is urgent or whether extra throughput is worth additional cost.

Therefore, an effective design needs cooperation between the application, operating system and transport.

**Key takeaway:** Cost-aware multipath uses cellular selectively instead of always activating every available path. The transport should expose per-path measurements and usage information, while the OS/application supplies cost, battery and priority policies.

---

## Q290. Satellite-plus-terrestrial scenario with very different RTTs: what does multipath give and risk? Relate to multipath QUIC draft.

### 1. Scenario

Consider a device connected through two paths:

- Terrestrial path: relatively low RTT.
- Satellite path: much higher RTT.

The satellite path may provide coverage where terrestrial connectivity is unavailable or may offer additional capacity.

However, the two paths have very different delay characteristics.

### 2. What does multipath provide?

**A. Additional capacity**

The connection may use both paths to increase aggregate available bandwidth.

**B. Resilience**

If the terrestrial path fails, the satellite path may maintain connectivity.

**C. Coverage**

Satellite connectivity can extend communication to locations where terrestrial infrastructure is limited.

**D. Flexible path selection**

The transport or scheduler can select paths according to application needs and current network conditions.

### 3. What are the risks?

**A. Large RTT difference**

Data sent over the satellite path may arrive significantly later than data sent over the terrestrial path.

**B. Reordering**

Packets sent later on the terrestrial path may arrive before earlier packets sent on the satellite path.

**C. Head-of-line effects**

If the application requires ordered delivery, missing earlier data can delay delivery of later data.

**D. Congestion-control differences**

The paths may have very different bandwidth-delay products and congestion characteristics.

**E. Inefficient scheduling**

Sending deadline-sensitive data over the high-RTT path may cause it to arrive too late.

**F. Resource imbalance**

A scheduler that only considers bandwidth may send too much data over a path with a high delay.

### 4. How should a scheduler behave?

The scheduler should consider the application's needs.

For bulk transfers:

- The satellite path may contribute useful additional capacity.
- Data should be distributed based on usable delivery rate and expected completion time.
- Reordering and receiver-buffer effects must be considered.

For interactive traffic:

- The terrestrial path may be preferable because of its lower delay.
- Satellite may be used as backup or for less time-sensitive data.
- Redundant transmission may be considered for critical data if the additional bandwidth is justified.

### 5. Relation to Multipath QUIC

Multipath QUIC research and IETF work aim to allow a QUIC connection to use multiple network paths.

The design needs to address:

- Path identification.
- Path validation.
- Path-specific RTT measurements.
- Congestion control.
- Packet scheduling.
- Loss recovery.
- Connection continuity.
- Different path characteristics.

A satellite-plus-terrestrial scenario is a useful example because it exposes the limitations of treating all paths as equivalent.

A multipath transport must not assume that the lowest-RTT path and highest-bandwidth path are necessarily the same path.

**Important:** The exact mechanisms and status of multipath QUIC depend on the specific draft or implementation being discussed. Do not attribute a particular scheduling algorithm or guaranteed performance to the IETF draft unless the relevant draft version explicitly specifies it.

### 6. What should we test?

A useful experiment could compare:

1. Terrestrial path only.
2. Satellite path only.
3. Both paths with a throughput-oriented scheduler.
4. Both paths with a latency-aware scheduler.

Measure:

- Aggregate goodput.
- Flow completion time.
- RTT.
- Packet reordering.
- Retransmissions.
- Buffer occupancy.
- Application latency.

**Key takeaway:** Satellite-plus-terrestrial multipath can provide coverage, resilience and additional capacity, but large RTT differences can cause reordering and delay. Scheduling must be application-aware and should distinguish bulk traffic from latency-sensitive traffic.

---

# Part 17 - Consolidated revision

## 1. Application requirements and suitable multipath behaviour

| Application | Main objective | Main concern with multipath |
|---|---|---|
| On-demand video | High quality and continuous playback | Segment completion time and rebuffering |
| Live video | Low end-to-end delay | Deadlines and late packets |
| VoIP | Interactive voice quality | Delay, jitter, reordering and loss |
| File transfer | Complete transfer as quickly as possible | Flow completion time and aggregate goodput |
| Mobile browsing | Responsive and reliable access | Handover and path availability |
| Satellite communication | Coverage and connectivity | Very different path RTTs |

## 2. Important metrics

| Metric | Meaning |
|---|---|
| Startup delay | Time from playback request to playback start |
| Rebuffering ratio | Fraction of playback time spent stalled |
| Average bitrate | Average video bitrate over a defined period |
| Bitrate switches | Changes in selected video quality |
| One-way delay | Time taken for data to travel from sender to receiver |
| RTT | Round-trip time between endpoints |
| Jitter | Variation in packet arrival delay |
| Packet loss | Fraction or number of packets that fail to arrive |
| MOS | Mean Opinion Score for perceived media quality |
| Flow completion time | Time required to complete a transfer |

## 3. MPTCP versus MP-QUIC: application-level points

| Aspect | MPTCP | MP-QUIC |
|---|---|---|
| Transport basis | TCP | QUIC |
| Reliable data | TCP/MPTCP reliable byte-stream delivery | QUIC reliable stream delivery |
| Real-time datagrams | Not equivalent to QUIC DATAGRAM; application design is needed | QUIC DATAGRAM can carry unreliable datagram data |
| Multipath scheduling | Selects a TCP subflow for data | Selects a QUIC path according to the implementation/design |
| Reordering | Can occur across subflows with different delays | Can occur across paths, depending on packet and stream scheduling |
| Flow control | TCP receive-window and MPTCP data-level mechanisms | QUIC stream and connection flow control |
| Congestion control | Per-subflow congestion control, with coupled approaches | Depends on the MP-QUIC implementation and congestion-control design |

**Important:** Do not equate QUIC streams with QUIC DATAGRAM frames. Streams provide reliable ordered delivery; DATAGRAM frames provide unreliable datagram delivery.

## 4. How to connect Part 17 to our experiments

When evaluating MPTCP and MP-QUIC, we should not limit our comparison to raw throughput.

We should consider the application-level consequences of multipath behaviour:

1. **Bulk transfer:** Measure flow completion time as well as aggregate goodput.
2. **Video-like workloads:** Examine data-delivery variation, completion time and the effect of path failure.
3. **Latency-sensitive workloads:** Measure RTT, delay variation, reordering and late delivery.
4. **Heterogeneous paths:** Test different RTT and bandwidth combinations.
5. **Path failure:** Observe how quickly the connection continues using the surviving path.
6. **Cost and energy:** Identify which paths are used and how much data is transmitted over each.
7. **Implementation differences:** Document whether the implementation supports streams, datagrams, path-specific scheduling and the relevant measurements.

If we do not implement an actual video or VoIP application, we must describe these as application-level implications or proposed evaluation scenarios, not as experimentally measured QoE results.

## 5. Primary references and further reading

1. **MPEG-DASH information - DASH Industry Forum.**  
   https://dashif.org/

2. **Apple HLS documentation.**  
   https://developer.apple.com/streaming/

3. **ITU-T G.114 - One-way transmission time.**  
   https://www.itu.int/rec/T-REC-G.114

4. **ITU-T G.107 - The E-model.**  
   https://www.itu.int/rec/T-REC-G.107

5. **RFC 3550 - RTP: A Transport Protocol for Real-Time Applications.**  
   https://www.rfc-editor.org/rfc/rfc3550

6. **RFC 9000 - QUIC: A UDP-Based Multiplexed and Secure Transport.**  
   https://www.rfc-editor.org/rfc/rfc9000

7. **RFC 9221 - An Unreliable Datagram Extension to QUIC.**  
   https://www.rfc-editor.org/rfc/rfc9221

8. **RFC 8684 - TCP Extensions for Multipath Operation with Multiple Addresses.**  
   https://www.rfc-editor.org/rfc/rfc8684

9. **Multipath QUIC IETF working-group documents.**  
   https://datatracker.ietf.org/wg/multipatht/ 

---

## 6. Final viva checklist

Before marking Part 17 complete, make sure you can explain these without reading the notes:

- [ ] Explain DASH/HLS, segments, manifests, bitrate ladders and client buffers.
- [ ] Compare throughput-based and buffer-based video adaptation.
- [ ] Explain why aggregate path throughput may not equal useful application throughput.
- [ ] Define startup delay, rebuffering ratio, bitrate switches and average bitrate.
- [ ] Explain why live video has stricter deadlines than on-demand video.
- [ ] Walk through the VoIP pipeline from codec to jitter buffer.
- [ ] Explain how multipath reordering can cause additional playback delay.
- [ ] State the commonly quoted 150 ms one-way voice-delay guideline and its source.
- [ ] Explain MOS and the E-model.
- [ ] Compare UDP/RTP, QUIC streams and QUIC DATAGRAM.
- [ ] Derive the rate-proportional split for a two-path file transfer.
- [ ] Explain why flow completion time can be more useful than throughput.
- [ ] Compare Wi-Fi and cellular path characteristics.
- [ ] Explain cost-aware and battery-aware path-selection policies.
- [ ] Discuss the benefits and risks of satellite-plus-terrestrial multipath.

**Completion criterion:** Part 17 is ready for team review when all 11 answers are in the notes, the ITU-T delay guideline and QUIC transport distinctions are understood, and you can explain how different applications value throughput, reliability and latency differently.

**One important note for the project\:** If you have not implemented video streaming or VoIP experiments, keep the application discussion as protocol analysis and proposed evaluation scenarios. Do not report simulated or theoretical QoE improvements as measured results.

Once this is saved, the next block in your original ownership allocation is **Part 18 - History and Literature, Deeper (Q291-Q297)**\.

## Prompt:
11/3/2026, 1:33:37 AM

# Selected text:

## Selection 1
If you have not implemented video streaming or VoIP experiments, keep the application discussion as protocol analysis and proposed evaluation scenarios. Do not report simulated or theoretical QoE improvements as measured results.

## My request:
im i supposed to run the experiments according to the plan

## Response:
11/3/2026, 1:32:46 AM · gpt-6

> **Remembering**
>
>
> ****
>
> 
>
> **Reviewed MPTCP and MP-QUIC plans, experiments, schedule, and responsibilities**
>
> 
>
> Worked for 8s

**Yes. According to your original project plan, you are supposed to run real experiments and collect actual results.** The experiments are part of the project, not just optional suggestions.

The important distinction is that **you do not need to implement every application discussed in Parts 16 and 17.** You need to execute the core transport experiments specified in the plan and use the application sections to explain their implications.

## 1\. Experiments required by your plan

Your original plan specifies the following core experimental work\:

| Experiment | What you need to do | Status |
|--------|--------|--------|
| 1\. MPTCP vs MP-QUIC | Compare both protocols under asymmetric network conditions | Required |
| 2\. Scheduling comparison | Compare MinRTT/lowest-RTT and Round Robin; redundant scheduling where supported | Required core comparison, with redundancy conditional |
| 3\. Bulk transfer | Run a large file-transfer workload | Required |
| 4\. Small/high-frequency workload | Run a small-packet, high-frequency workload | Required |
| 5\. Congestion-control fairness | Demonstrate MPTCP coupled congestion control versus naive/uncoupled behaviour against competing TCP traffic | Required |
| 6\. MP-QUIC execution evidence | Obtain at least one successful TQUIC/MP-QUIC run with qlog or throughput evidence | Required |

The plan calls for approximately **2–3 asymmetric network conditions**, using controlled network emulation.

## 2\. What tools and evidence are expected?

The experimental setup in the plan uses\:

- Mininet and NetEm for network topology and delay/loss/bandwidth conditions.
- MPTCP-enabled Linux kernel.
- TQUIC/MP-QUIC implementation.
- iperf3 or an equivalent transfer workload.
- Wireshark/packet captures where useful.
- qlog and throughput measurements.

You need actual captured data, not just screenshots of commands or theoretical calculations.

For the main comparisons, record\:

- Throughput/goodput.
- Flow completion time.
- RTT and delay.
- Packet loss and retransmissions.
- Path utilisation.
- Scheduling behaviour.
- Fairness where applicable.

Run repeated trials (the earlier experimental plan specifies at least three repetitions) and preserve the raw results.

## 3\. Do you need to implement video streaming and VoIP?

**No, not as separate applications.**

Part 17 asks you to understand how multipath affects video, VoIP and other application workloads. Those are research and analysis questions.

Your actual experimental workloads are the bulk-transfer and small/high-frequency profiles specified in the plan. You can discuss how your measured delay, throughput and reordering results would affect video or voice applications without claiming that you implemented or measured those applications.

## 4\. What should the final project contain?

Your final submission should have\:

1. Experimental setup and reproducible configurations.
2. Actual MPTCP and MP-QUIC results.
3. Raw measurement data and graphs.
4. Scheduling comparison and analysis.
5. Coupled-congestion-control fairness demonstration.
6. Discussion of failures, limitations and implementation differences.
7. Evidence such as qlogs, captures and experiment logs.
8. Final comparison, conclusions and presentation/viva material.

## 5\. Where we stand

Your theory/research blocks—including Parts 16 and 17—are progressing. However, based on the last confirmed project status, the experimental work has **not yet been verified as completed**\. We should not mark it complete until we inspect the actual results.

(Important) Your deadline is **4 November 2026**, so we should prioritise experimental execution and evidence now rather than spending all the remaining time expanding theory notes.

**My recommendation\:** Finish Part 18 (Q291–Q297) efficiently, but start the experimental work in parallel immediately. I can take you through it step by step, beginning with checking your existing MPTCP/MP-QUIC setup and identifying exactly what is already working.

## Prompt:
11/3/2026, 1:35:16 AM

but im i (swamini) assigned to do this according to the plan??

## Response:
11/3/2026, 1:34:24 AM · gpt-6

> **Remembering**
>
>
> **Clarified your Swamini, networking, and protocol experiment assignments**
>
> 
>
> Worked for 7s

**No — according to the ownership allocation in your original plan, you are not individually assigned to execute the entire experimental setup.** I should have made that distinction clearer.

Your assigned theory/research work is\:

- **Part 9\:** Q159–176 — research and experimental literature.
- **Part 16\:** Q265–279 — congestion control, fairness and scheduling theory.
- **Part 17\:** Q280–290 — applications and QoE.
- **Part 18\:** Q291–297 — history and deeper literature.
- **Part 10\:** Q177–190 — you lead this section, with the shared team responsibility.

For the **experiments specifically**, the plan identifies your responsibility as **researching existing MPTCP/MP-QUIC experiments, their results and trade-offs**\. It does not explicitly assign you to run the entire experimental setup, configure Mininet, or collect all the measurements.

So the distinction is\:

| Work | Your assignment according to the plan |
|--------|--------|
| Research prior experiments and published results | **Yes** |
| Analyse congestion control, fairness and scheduling | **Yes** |
| Analyse application/QoE implications | **Yes** |
| Execute all MPTCP vs MP-QUIC experiments | **Not explicitly assigned to you** |
| Configure Mininet/NetEm and collect experimental data | **No individual assignment established** |

**Correction to my previous response\:** I shouldn't have told you to take ownership of all experiments. The project may require the team to produce experimental evidence, but that does not mean you personally have been assigned to execute every experiment.

Your immediate individual responsibility is to complete your assigned sections and contribute the literature-based experimental analysis.

## Prompt:
11/3/2026, 2:53:28 PM

done now lets move to the next part

## Response:
11/3/2026, 2:52:37 PM · gpt-6

> **Prepared Part 18 Questions 291–297**
>
> 
>
> **Drafting evidence-based history**
>
> I’m organizing XLINK’s history around deployment barriers, transport comparisons, measurement evidence, and relevant standards. I’ll keep claims balanced, distinguish laboratory results from Internet observations, and avoid asserting uncertain citations or implementation details.
>
> **Drafted evidence-based history**
>
> 
>
> **Searched 7 websites**
>
> 
>
> Worked for 28s

The next section in your original plan is **Part 18 - History and Literature, Deeper (Q291-Q297)**\. This is your final individually owned section, after Parts 9, 16 and 17. It focuses on the evolution of multipath protocols, deployment barriers, research-paper validity and how to verify technical claims. fileciteturn19file1

I'll keep the answers in the same paste-ready format, and explicitly flag points that need verification rather than presenting uncertain research details as facts.

**document: **

# Part 18 - History and Literature, Deeper (Q291-Q297)

## Q291. Build a timeline of multipath ideas. What problem did each step address?

| Period / milestone | Main idea | Problem addressed / contribution |
|---|---|---|
| SCTP multihoming (standardised in RFC 2960, later RFC 4960) | A transport association can use multiple IP addresses and switch paths after failures. | Improved resilience and failover. Traditional SCTP multihoming was primarily for path redundancy, not general simultaneous bandwidth aggregation. |
| pTCP | Research design for using multiple TCP paths as one logical connection. | Explored how to combine several paths while presenting a single reliable transport service to applications. |
| mTCP | Another research approach to multipath transport using multiple TCP connections/subflows. | Explored concurrent use of multiple interfaces and the challenges of coordinating reliability and congestion control. |
| CMT-SCTP | Concurrent Multipath Transfer over SCTP. | Extended SCTP beyond failover so data could be transmitted concurrently over multiple paths. It exposed issues such as receiver-side reordering and congestion-control fairness. |
| MPTCP working-group work | Standardised a multipath extension to TCP. | Aimed to use multiple paths while retaining compatibility with existing TCP applications and networks. |
| RFC 6824 (2013) | First major experimental MPTCP protocol specification. | Defined connection-level and subflow-level mechanisms, including capability negotiation, joining subflows and mapping data across them. |
| Apple's MPTCP deployment | MPTCP was used in a real smartphone service, notably reported for Siri. | Demonstrated that multipath transport could be deployed in a consumer service rather than remaining only a research prototype. |
| RFC 8684 (2020) | Standards Track MPTCP specification, replacing RFC 6824. | Updated and standardised MPTCP based on implementation and deployment experience. |
| Linux upstream MPTCP (Linux 5.6, 2020) | MPTCP support entered the upstream Linux kernel. | Made MPTCP more accessible to researchers and implementers using a mainstream operating system. |
| QUIC (RFC 9000, 2021) | Secure, user-space transport over UDP, with connection IDs and stream multiplexing. | Provided transport evolution without requiring changes to the TCP kernel implementation; connection migration supports continuity when network addresses change. |
| 2017 MPQUIC research | De Coninck and Bonaventure proposed and implemented a multipath extension to QUIC. | Explored simultaneous use of paths such as Wi-Fi and cellular, combining QUIC's flexibility with MPTCP-like multipath benefits. |
| Later MP-QUIC individual drafts | The design was revised through successive Internet-Draft versions. | Refined path identification, path management, packet-number handling and privacy/security considerations. |
| Current IETF multipath QUIC work | The QUIC working group has continued developing a multipath extension. | Seeks a standardised way for one QUIC connection to use multiple paths concurrently. It remains important to distinguish an Internet-Draft from a published RFC. |

**Important distinction:** SCTP multihoming, MPTCP and MP-QUIC are not interchangeable. SCTP's original multihoming primarily supports path failover; CMT-SCTP explores concurrent transfer; MPTCP adds multipath to TCP; MP-QUIC extends QUIC.

## Q292. Why were pTCP, mTCP and SCTP-based approaches not widely deployed, and what did MPTCP do differently?

Earlier multipath proposals faced a combination of deployment and engineering barriers:

1. **Application compatibility:** A new transport protocol may require application and operating-system support. Replacing TCP everywhere is difficult.
2. **Middlebox compatibility:** Firewalls, NATs and other middleboxes may block unfamiliar protocols or transport options.
3. **Operating-system changes:** Deployment may require kernel modifications, new APIs or application changes.
4. **Complexity:** Multipath introduces path management, scheduling, reordering, congestion control and failure-handling problems.
5. **Limited ecosystem support:** A technically promising protocol may fail to gain adoption if operating systems, applications and network operators do not support it.

**What MPTCP did differently:**

- It retained the TCP service model presented to existing applications.
- It established a logical connection using multiple TCP subflows.
- It used TCP options to negotiate and manage multipath operation.
- It could fall back to ordinary TCP when multipath operation was unavailable or failed, subject to the connection and implementation conditions.
- It was developed with deployment and compatibility in mind, not only theoretical throughput.

**Why this mattered:** MPTCP reduced the application-facing disruption of introducing multipath. It did not eliminate deployment problems: middleboxes can still interfere with TCP options, and both endpoints need MPTCP support for multipath operation.

Do not say that earlier approaches failed for one single reason. Their deployment outcomes depended on compatibility, implementation maturity, infrastructure support and use-case demand.

## Q293. What evidence suggests middleboxes are less hostile to MPTCP than feared, and what evidence suggests they are still a problem?

There are two sides to the evidence.

**Evidence that deployment can work:**

- MPTCP has been deployed in real services and operating systems.
- Successful deployments show that at least some real network paths allow the required TCP options and subflow behaviour.
- Linux upstream support and smartphone deployments demonstrate that MPTCP is technically deployable outside a controlled laboratory.

**Evidence that middleboxes remain a concern:**

- Some NATs, firewalls and TCP middleboxes may remove, alter or mishandle TCP options.
- Some networks may block or interfere with additional subflows.
- A connection may work on its initial TCP subflow but fail to establish or use additional subflows.
- Network policies, carrier infrastructure and access-network configuration can vary substantially.

**Why can a laboratory study and an Internet scan disagree?**

| Laboratory study | Internet scan |
|---|---|
| Uses a controlled set of routers, NATs and middleboxes. | Encounters a much wider variety of real networks. |
| Can isolate a particular cause of failure. | Observes end-to-end outcomes but may not identify the exact device causing failure. |
| May use a small number of known configurations. | May cover many networks, but the sample may not represent all users or locations. |
| Offers reproducibility. | Offers broader deployment evidence, but conditions are less controlled. |

**Conclusion:** Neither result should automatically invalidate the other. A laboratory result explains behaviour under controlled conditions; an Internet measurement estimates how often that behaviour occurs in the tested population. Both the measurement method and the network population matter.

## Q294. For two papers in the literature matrix, identify threats to validity.

### Paper 1: De Coninck and Bonaventure, “Multipath QUIC: Design and Evaluation” (CoNEXT 2017)

**Internal validity threats:**

- Results depend on the particular quic-go research implementation and its maturity.
- The outcome may depend on the selected scheduler, congestion-control behaviour, path rates, RTTs and loss configuration.
- Comparisons can be affected by whether TCP, MPTCP, QUIC and MPQUIC are equally tuned.
- A limited number of runs or insufficient reporting of variance can make small differences difficult to interpret.

**External validity threats:**

- A Mininet testbed cannot reproduce every feature of a real mobile or public Internet path.
- A 2017 research implementation may not represent current QUIC implementations or the current IETF multipath design.
- Results from selected Wi-Fi/cellular-like conditions may not generalise to all access networks.

**How to interpret it:** It is valuable evidence that multipath QUIC can be designed and evaluated, but its numerical results should not be treated as universal predictions for today's implementations.

### Paper 2: XLINK - “QoE-Driven Multi-Path QUIC Transport in Large-scale Video Services” (SIGCOMM 2021)

**Internal validity threats:**

- A/B test results depend on the experiment's participant selection, assignment, measurement and statistical treatment.
- Improvements may depend on XLINK's particular scheduling, path-management and application integration choices.
- The additional redundant traffic and operational cost must be considered alongside QoE improvements.

**External validity threats:**

- The deployment was associated with a particular large-scale short-video service and its user population.
- Results may differ for other applications, video formats, CDN architectures, countries and network conditions.
- A production system with application-level QoE information may not be comparable to a generic transport-only multipath implementation.

**How to interpret it:** XLINK provides important production evidence for application-aware multipath QUIC, but its results should not be assumed to apply unchanged to every MP-QUIC implementation.

**General lesson:** Internal validity asks whether the study supports its conclusion under its own experimental conditions. External validity asks whether that conclusion generalises to other implementations, users and networks.

## Q295. What problem did QoE-driven multipath QUIC work for large-scale video services target, and how did it differ from the IETF draft?

**XLINK** targeted video quality problems in large-scale short-video services. Its goal was to improve user-perceived quality of experience (QoE), including:

- Faster video-chunk completion.
- Lower first-video-frame latency.
- Reduced rebuffering.
- Better responsiveness and robustness during changing network conditions and mobility.

The central idea was to use QUIC's user-space implementation to connect transport decisions with application-level video QoE. The system could use information about video demand and playback quality to guide multipath scheduling and path management.

The paper reported large-scale A/B tests involving over 100,000 participants and more than 3 million video plays. Compared with single-path QUIC, it reported improvements in tail video-chunk completion time, first-frame latency and rebuffering, with an additional redundant-traffic cost.

**How this differs from the IETF multipath QUIC draft:**

| XLINK research system | IETF multipath QUIC draft |
|---|---|
| Focuses on a production video-service use case. | Defines transport-level mechanisms for managing multiple paths. |
| Uses application-level QoE information to guide scheduling and path management. | Specifies protocol mechanisms such as path identification and management. |
| Evaluates service-level outcomes such as video latency and rebuffering. | Does not prescribe a particular video QoE scheduler. |
| Includes implementation-specific operational choices. | Aims to define interoperable protocol behaviour. |

**Key distinction:** XLINK is an application-aware multipath QUIC system and production study. The IETF draft is a protocol specification effort. Do not describe XLINK's scheduling policy or measured video improvements as requirements or guaranteed results of the IETF draft.

## Q296. How did multipath QUIC evolve from the 2017 research design to the IETF draft?

The 2017 design by De Coninck and Bonaventure was an early research proposal and implementation. It demonstrated how QUIC could use multiple paths simultaneously rather than only migrating a connection from one path to another.

The later design work evolved through successive drafts and broader IETF discussion.

**Major themes in the evolution:**

1. **From research prototype to interoperable protocol design:** The early work demonstrated feasibility; later drafts refined the mechanisms needed for different implementations to interoperate.
2. **Explicit path management:** Multipath operation needs mechanisms to identify, create, validate, use and abandon paths.
3. **Per-path packet handling:** Different paths can have different loss, RTT and delivery behaviour. The design must handle packet-number and acknowledgement behaviour consistently.
4. **Security and privacy:** Adding paths exposes multiple network addresses and creates risks such as path-validation abuse or unwanted linkability. The design must account for these risks.
5. **Separation of responsibilities:** The transport extension defines how paths are managed, but it does not automatically define how an application should distribute every byte across those paths.

**Important comparison:** The 2017 paper and the IETF multipath QUIC draft are related, but they are not the same document or implementation. Do not assume that a feature, frame name, packet format or performance result from the 2017 prototype exists unchanged in the current draft.

For an exact change-by-change answer, compare the original 2017 draft, later revisions and the current working-group draft. Record the draft revision and date because Internet-Drafts change and expire.

## Q297. Find an unsupported online claim about MPTCP or MP-QUIC. How should you verify it?

**Example of an unsupported claim:**

“RFC 9443 standardises Multipath QUIC.”

This claim is incorrect. RFC 9443 is not the multipath QUIC specification.

**Verification procedure:**

1. Search the RFC number in the official RFC Editor database or IETF Datatracker.
2. Read the RFC's exact title, abstract, status and scope.
3. Check whether the document actually discusses MPTCP or multipath QUIC.
4. Search the IETF Datatracker for the relevant multipath QUIC Internet-Draft.
5. Check the document's revision, authors, publication date and current status.
6. Distinguish a published RFC from an Internet-Draft. An Internet-Draft is a work in progress and is not automatically an approved standard.
7. Prefer primary sources: RFCs, IETF Datatracker records, original research papers and official implementation documentation.

**What to write when a claim cannot be verified:**

“An online source makes this claim, but I could not confirm it in the relevant primary specification or research paper. I therefore treat it as unverified and do not use it as an established protocol fact.”

**Why this matters:** A plausible-looking RFC number, blog post or video explanation is not sufficient evidence. Verify the actual document and its scope before citing it.

---

## Consolidated revision - Part 18

| Question | Main point to remember |
|---|---|
| Q291 | Multipath evolved from failover and research proposals toward deployable transport extensions. |
| Q292 | MPTCP's key deployment strategy was preserving the TCP application interface and considering compatibility. |
| Q293 | Middlebox compatibility is network-dependent; controlled tests and Internet scans answer different questions. |
| Q294 | Separate internal validity from external validity when evaluating papers. |
| Q295 | XLINK uses application QoE to guide multipath video transport; the IETF draft specifies transport mechanisms. |
| Q296 | MP-QUIC evolved from a research prototype into a more detailed protocol-standardisation effort. |
| Q297 | Verify claims against primary sources and distinguish RFCs from Internet-Drafts. |

## References

1. De Coninck, Q. and Bonaventure, O., “Multipath QUIC: Design and Evaluation,” CoNEXT 2017.
2. De Coninck and Bonaventure, “Multipath Extension for QUIC,” October 2017 Internet-Draft.
3. RFC 4960 - Stream Control Transmission Protocol.
4. RFC 6824 - TCP Extensions for Multipath Operation with Multiple Addresses.
5. RFC 8684 - TCP Extensions for Multipath Operation with Multiple Addresses.
6. RFC 9000 - QUIC: A UDP-Based Multiplexed and Secure Transport.
7. Zheng et al., “XLINK: QoE-Driven Multi-Path QUIC Transport in Large-scale Video Services,” SIGCOMM 2021.
8. IETF Datatracker - multipath QUIC draft history and current document status.

## Viva checklist

Before considering this section complete, make sure you can explain:

- Why SCTP multihoming is not the same as concurrent multipath transfer.
- Why MPTCP's compatibility strategy helped deployment.
- Why middlebox results differ across networks and measurement methods.
- The difference between internal and external validity.
- Why XLINK is not the same thing as the IETF multipath QUIC specification.
- Why the 2017 MPQUIC implementation should not be treated as the current draft.
- How to verify an RFC number and an Internet-Draft's status.

The primary sources confirm the 2017 MPQUIC research design, XLINK's production-video focus and reported results, and the distinction between the older individual draft and later IETF work. \[[draft-deconinck-multipath-quic-00](https://datatracker.ietf.org/doc/html/draft-deconinck-multipath-quic-00?utm_source=chatgpt.com); [Multipath QUIC: Design and Evaluation](https://multipath-quic.org/conext17-deconinck.pdf?utm_source=chatgpt.com); [XLINK: QoE-Driven Multi-Path QUIC Transport in Large-scale Video Services](https://conferences.sigcomm.org/sigcomm/2021/files/papers/3452296.3472893.pdf?utm_source=chatgpt.com); [History for draft-deconinck-quic-multipath -07](https://datatracker.ietf.org/doc/draft-deconinck-quic-multipath/history/?utm_source=chatgpt.com); [draft-deconinck-quic-multipath-07](https://datatracker.ietf.org/doc/html/draft-deconinck-quic-multipath?utm_source=chatgpt.com)\]

**Save this as\:**

`08_History_Literature_Q291-297/History_and_Literature_Deeper.md`

**One important review point\:** Q296 needs a revision-by-revision comparison if your professor asks exactly what changed between the 2017 design and the current draft. The answer above gives the major design themes without pretending every mechanism remained unchanged.

Next, your individually assigned sections (Parts 9, 16, 17 and 18) are covered. The remaining work is the shared team sections and cross-review/mock-viva preparation.

## Prompt:
11/3/2026, 3:15:36 PM

done now next what

## Response:
11/3/2026, 3:14:46 PM · gpt-6

According to your original plan, the next section is **Part 19 — Trace It End to End (Q298–Q309)**\.

(Shared team section) **Pratik leads this section, but everyone must answer it.** fileciteturn19file4

### What Part 19 covers

You will trace how data travels through both protocols, from the application to the receiver.

| Questions | Topic |
|--------|--------|
| Q298–299 | Trace a 1 MB upload through MPTCP and MP-QUIC |
| Q300 | Compare the protocol stacks |
| Q301–302 | Network assumptions and protocol state |
| Q303 | What happens if a mechanism is removed? |
| Q304 | Predict protocol behaviour under different network conditions |
| Q305–306 | Security, privacy and design trade-offs |
| Q307–309 | Design improvements, packet captures and connections between mechanisms |

**My recommendation\:** Since Pratik leads this section, coordinate with him rather than independently duplicating his work. You should still prepare your own answers and be able to explain all 12 questions.

Also, don't overlook your **Part 10 (Q177–Q190)** leadership responsibility if that section hasn't been completed yet.

Let's proceed with Part 19, starting with Q298 and Q299.

## Prompt:
11/3/2026, 3:20:36 PM

ok give this complete section to paste in that section md file for this section according to what all i need to have know learn

## Response:
11/3/2026, 3:19:43 PM · gpt-6

We'll prepare the complete **Part 19 - Trace It End to End (Q298-Q309)** as a study document, not just short answers. It will cover the mechanisms, sequence of events, diagrams, comparisons, failure scenarios, and viva-level reasoning you need to understand.

This section is shared by everyone and led by Pratik in your original plan. The answers below follow the plan's 12 questions. Where behaviour depends on a particular MP-QUIC draft or implementation, I've marked that distinction rather than assuming all implementations behave identically. fileciteturn19file4

**document: **

# Part 19 - Trace It End to End (Q298-Q309)

**Purpose:** Understand how data actually travels through MPTCP and MP-QUIC, how their mechanisms interact, and what happens when network conditions or protocol mechanisms change.

**Scope:** Q298-Q309  
**Ownership:** Shared team section - Pratik leads  
**Study goal:** Be able to trace a data transfer from the sender's application to the receiver's application, explain every important layer and mechanism, and predict behaviour under different network conditions.

---

# 1. End-to-End Data Flow

## Q298. Trace a 1 MB upload over MPTCP from the application's `write()` to the receiving application's `read()`. Name every buffer, every sequence number, every ACK and every timer on the way.

### A. First understand the architecture

MPTCP presents a TCP-like byte-stream interface to the application. The application does not need to know that data is being transmitted over multiple paths.

MPTCP maintains:

- One logical MPTCP connection.
- One or more TCP subflows.
- A connection-level data sequence space.
- A separate TCP sequence space on each subflow.
- Mapping information that associates connection-level data with subflow-level TCP data.

A simplified architecture:

```text
             SENDER
+-----------------------------+
|       Application           |
|          write()            |
+-----------------------------+
              |
              v
+-----------------------------+
|      MPTCP connection       |
|                             |
| Connection-level send buffer|
| Data Sequence Number (DSN)  |
| Data-level reliability      |
+-----------------------------+
              |
              v
+-----------------------------+
|      MPTCP scheduler        |
| Chooses an eligible subflow |
+-----------------------------+
          /          \
         v            v
+-------------+  +-------------+
| TCP subflow 1|  | TCP subflow 2|
| TCP sequence |  | TCP sequence |
| number space |  | number space |
| Congestion   |  | Congestion   |
| control      |  | control      |
+-------------+  +-------------+
       |                |
       v                v
    Path 1            Path 2
       \                /
        \              /
         v            v
             NETWORK

             RECEIVER
+-----------------------------+
| TCP subflow reception       |
| TCP ACK processing          |
+-----------------------------+
              |
              v
+-----------------------------+
| MPTCP data-level processing |
| DSN mapping and reassembly   |
| Data ACK generation         |
+-----------------------------+
              |
              v
+-----------------------------+
| Application receive buffer  |
+-----------------------------+
              |
              v
           read()
```

### B. Step-by-step transmission

**Step 1 - Application writes data**

The sender's application calls:

```c
write(socket_fd, buffer, length);
```

For this example, assume the application writes 1 MB of data.

The application sees one logical socket. It does not select individual network paths or assign TCP sequence numbers.

The operating system accepts data into the socket's send-side buffering, subject to available buffer space and flow-control constraints.

**Step 2 - MPTCP assigns connection-level data sequence numbers**

MPTCP maintains a connection-level Data Sequence Number (DSN).

The DSN identifies bytes in the logical MPTCP data stream, independently of which subflow carries them.

For example, imagine the logical byte stream is divided into:

```text
Data range A: DSN 0-999
Data range B: DSN 1000-1999
Data range C: DSN 2000-2999
```

These are illustrative byte ranges, not mandatory segment sizes.

**Step 3 - The scheduler chooses a subflow**

MPTCP may have multiple established TCP subflows.

The scheduler decides which eligible subflow should carry a piece of data. Its decision can depend on information such as:

- RTT.
- Congestion window.
- Available send window.
- Whether a path is backup.
- Scheduler policy.
- Implementation-specific constraints.

For example:

```text
DSN 0-999       -> Subflow 1
DSN 1000-1999   -> Subflow 2
DSN 2000-2999   -> Subflow 1
```

The exact distribution depends on the scheduler and current path state.

**Step 4 - MPTCP maps connection-level data onto TCP subflows**

MPTCP uses the Data Sequence Signal (DSS) option to communicate data-level sequence information and map data carried by a subflow to the logical connection.

Conceptually, a DSS mapping associates:

- A connection-level Data Sequence Number (DSN).
- The corresponding subflow-level TCP sequence number.
- The length of the mapped data.
- Optionally, a data checksum, depending on the negotiated configuration.

This mapping lets the receiver reconstruct the original logical byte stream even when pieces arrive through different subflows.

**Step 5 - Each TCP subflow performs normal TCP transmission**

Each subflow has its own TCP sequence-number space.

For example:

```text
Subflow 1:
TCP sequence range 5000-5999

Subflow 2:
TCP sequence range 9000-9999
```

These sequence numbers are illustrative. They are independent of the connection-level DSNs.

Each subflow uses TCP mechanisms such as:

- TCP congestion control.
- TCP receive-window flow control.
- TCP acknowledgements.
- Retransmission timers.
- Loss detection and retransmission.

**Important:** The TCP sequence number and the MPTCP DSN are not interchangeable.

A TCP sequence number identifies bytes within one TCP subflow. A DSN identifies bytes in the overall MPTCP connection.

**Step 6 - Network transmission**

Subflow packets travel through their respective network paths.

The paths may differ in:

- RTT.
- Bandwidth.
- Loss.
- Congestion.
- Queueing delay.

Consequently, data sent later over a fast path may arrive before earlier data sent over a slow path.

**Step 7 - Receiver acknowledges subflow-level TCP data**

The receiver's TCP subflows process incoming TCP segments.

Each subflow generates TCP ACKs for data received in that subflow's sequence space.

These ACKs provide subflow-level reliability information to the sender.

A TCP ACK does not necessarily mean that the application has received the corresponding logical MPTCP data in order.

**Step 8 - MPTCP processes DSN mappings and reassembles data**

The receiver uses the DSS mappings to identify where each received piece belongs in the logical data stream.

If data arrives out of order, MPTCP must retain it until the missing earlier bytes arrive.

For example:

```text
Expected logical order:

DSN 0-999
DSN 1000-1999
DSN 2000-2999

Arrival order:

DSN 0-999
DSN 2000-2999
DSN 1000-1999
```

The receiver cannot deliver the later bytes as part of an ordinary ordered byte stream before the missing earlier range is available.

This is MPTCP-level reassembly and can cause connection-level head-of-line blocking.

**Step 9 - Receiver sends a Data ACK**

MPTCP has a connection-level acknowledgement mechanism called the Data ACK.

A Data ACK acknowledges progress in the logical MPTCP data sequence space.

This is distinct from the TCP ACKs generated by individual subflows.

The distinction is:

- TCP ACK: acknowledges received bytes in a particular subflow's TCP sequence space.
- Data ACK: acknowledges received data in the overall MPTCP connection's DSN space.

**Step 10 - Sender processes acknowledgements and retransmissions**

The sender tracks delivery at both levels.

- TCP-level loss and retransmission are handled by each subflow.
- Data-level delivery is tracked using MPTCP's DSN and Data ACK mechanisms.

If data has not been successfully delivered at the connection level, MPTCP can retransmit the missing logical data over an eligible subflow, subject to implementation behaviour and available paths.

A logical data range may therefore be retransmitted using a different subflow.

**Step 11 - Data reaches the receiving application**

Once the required earlier bytes are available and the logical byte stream is reassembled, data becomes available to the receiving application's socket.

The receiving application calls:

```c
read(socket_fd, buffer, length);
```

The application receives the ordered byte stream, not separate Wi-Fi and cellular streams.

### C. Important buffers and sequence spaces

| Component | What it stores or tracks |
|---|---|
| Sender application buffer | Data supplied by the application |
| Sender socket/send buffer | Data waiting to be transmitted or acknowledged |
| MPTCP connection-level state | DSN, data-level delivery and reassembly state |
| TCP subflow send buffer/state | Subflow transmission and retransmission state |
| Network queues | Packets waiting for transmission |
| Receiver TCP reassembly state | TCP segments received within each subflow |
| Receiver MPTCP reassembly state | Data mapped into the logical DSN space |
| Receiver socket/receive buffer | Ordered bytes available to the application |

The exact internal buffer arrangement can vary by operating-system implementation. This table describes the logical responsibilities, not a guarantee that every item is a separate physical buffer.

### D. Important sequence numbers and acknowledgements

| Mechanism | Scope | Purpose |
|---|---|---|
| TCP sequence number | One subflow | Identifies bytes in that TCP subflow |
| TCP ACK | One subflow | Acknowledges TCP-level reception |
| Data Sequence Number (DSN) | Entire MPTCP connection | Identifies logical data bytes |
| Data ACK | Entire MPTCP connection | Acknowledges logical data-level reception |
| DSS mapping | Connects the two sequence spaces | Maps subflow data to connection-level data |

### E. Timers and loss detection

There is not one single timer for the entire multipath connection.

Relevant mechanisms include:

1. **TCP retransmission timer (RTO):** Each TCP subflow maintains its own retransmission and loss-recovery state.
2. **TCP loss detection:** ACK behaviour and other TCP loss-detection mechanisms help detect missing subflow data.
3. **MPTCP data-level recovery:** MPTCP tracks logical data delivery and may retransmit data that has not been acknowledged at the data level.
4. **Connection/path management timers:** Implementations also have timers associated with connection and path management.

Do not assume that every MPTCP implementation uses one identical independent Data ACK timer. Explain the data-level recovery function and the relevant implementation's actual timer behaviour.

### F. Key takeaway

MPTCP uses two levels of reliability:

- TCP reliability inside each subflow.
- MPTCP data-level reliability across the logical connection.

This allows the connection to use multiple paths while presenting one ordered byte stream to the application.

---

## Q299. Trace a 1 MB upload over MP-QUIC, from a stream write to the receiving application's read.

### A. First understand the architecture

QUIC is a secure transport protocol built over UDP.

Multipath QUIC extends a QUIC connection so that it can use multiple network paths concurrently.

A QUIC connection can contain multiple streams. Each stream has its own ordered byte sequence.

A simplified architecture:

```text
             SENDER
+-----------------------------+
|          Application        |
|       QUIC stream write     |
+-----------------------------+
              |
              v
+-----------------------------+
|       QUIC connection       |
|                             |
| Stream state and buffers    |
| Connection flow control     |
| Stream flow control         |
| TLS-based security          |
+-----------------------------+
              |
              v
+-----------------------------+
|      Multipath scheduler    |
| Selects an eligible path    |
+-----------------------------+
          /          \
         v            v
+-------------+  +-------------+
| QUIC Path 1 |  | QUIC Path 2 |
| Packet number| | Packet number|
| Congestion   |  | Congestion   |
| control      |  | control      |
+-------------+  +-------------+
       |                |
       v                v
    UDP path 1        UDP path 2
       \                /
        \              /
         v            v
             RECEIVER
+-----------------------------+
| UDP packet reception        |
+-----------------------------+
              |
              v
+-----------------------------+
| QUIC packet processing      |
| Decryption and validation   |
| ACK and loss processing     |
+-----------------------------+
              |
              v
+-----------------------------+
| Stream reassembly           |
| Flow-control processing     |
+-----------------------------+
              |
              v
+-----------------------------+
| Application stream read     |
+-----------------------------+
```

### B. Step-by-step transmission

**Step 1 - Application writes to a QUIC stream**

The sender's application writes data to a QUIC stream.

Conceptually:

```text
stream.write(data)
```

The application writes 1 MB in this example.

QUIC maintains stream-level state, including the stream's byte offsets and flow-control limits.

**Step 2 - QUIC divides stream data into frames**

QUIC stream data is carried in STREAM frames.

A STREAM frame identifies:

- The stream ID.
- The stream offset.
- The data carried.
- Whether the frame marks the end of the stream.

The stream offset identifies the byte position within that stream.

For example:

```text
Stream 4:

Offset 0-999
Offset 1000-1999
Offset 2000-2999
```

These are illustrative ranges.

**Step 3 - QUIC checks flow-control limits**

QUIC has two important levels of flow control:

- **Stream-level flow control:** Limits how much data can be sent on an individual stream.
- **Connection-level flow control:** Limits the total amount of stream data across the connection.

The sender must respect the advertised flow-control limits.

Flow control protects the receiver from being overwhelmed. It is different from congestion control, which protects the network.

**Step 4 - Multipath scheduler selects a path**

A multipath QUIC implementation may have multiple available paths.

The scheduler selects an eligible path for transmission.

Its decision may consider:

- RTT.
- Congestion window.
- Available capacity.
- Loss.
- Path validation state.
- Application requirements.
- Implementation-specific scheduling policy.

For example:

```text
Stream offset 0-999       -> Path 1
Stream offset 1000-1999   -> Path 2
Stream offset 2000-2999   -> Path 1
```

This is an illustrative scheduling decision, not a required fixed mapping.

**Step 5 - QUIC creates encrypted packets**

QUIC places frames into QUIC packets.

The packet is encrypted using the connection's cryptographic keys and transmitted over UDP.

Multipath QUIC adds path-management and path-identification behaviour to the connection.

A critical distinction is that a QUIC stream offset and a QUIC packet number represent different things:

- Stream offset identifies the byte position in a stream.
- Packet number identifies a QUIC packet within the relevant packet-number space.

**Step 6 - Packets travel over different paths**

Packets are transmitted through the selected paths.

Paths may have different RTT, bandwidth, loss and congestion.

Packets can therefore arrive out of order.

The receiver must use stream offsets to place the received stream data correctly.

**Step 7 - Receiver processes QUIC packets**

The receiver obtains UDP datagrams and processes the QUIC packets.

It performs tasks such as:

- Packet decryption and authentication.
- Packet-number processing.
- Frame processing.
- ACK generation.
- Loss detection and recovery.
- Stream-data reassembly.

UDP itself does not provide reliable delivery. QUIC implements reliability above UDP.

**Step 8 - Receiver acknowledges packets**

QUIC uses ACK frames to acknowledge received packets.

In multipath QUIC, packet-number and acknowledgement handling must account for the multipath design specified by the particular draft or implementation.

Do not assume that the original single-path QUIC packet-number model can be described as identical to every multipath QUIC design.

**Step 9 - Lost stream data is retransmitted**

QUIC retransmits information needed to recover lost data.

An important distinction:

QUIC generally does not retransmit the exact same lost packet with the same packet number. It sends the relevant information again in a new packet.

The stream data retains its stream offset, even if it is carried in a different packet or on another eligible path.

**Step 10 - Receiver reassembles stream data**

The receiver uses stream offsets to reconstruct the ordered byte sequence for each stream.

For example:

```text
Expected stream order:

Offset 0-999
Offset 1000-1999
Offset 2000-2999

Arrival order:

Offset 0-999
Offset 2000-2999
Offset 1000-1999
```

The receiver cannot deliver the later bytes to the application as part of the same ordered stream until the missing earlier bytes are available.

This means that QUIC streams still have ordering-related blocking within an individual stream.

However, independent QUIC streams can make progress separately, subject to connection-level flow control and other shared constraints.

**Step 11 - Application reads the stream**

Once the required stream data is available, the receiver's application reads it:

```text
stream.read(buffer)
```

The application receives the ordered bytes from the stream. It does not need to manage the individual network paths.

### C. Important buffers and state

| Component | Responsibility |
|---|---|
| Application buffer | Data provided by the application |
| QUIC stream send buffer/state | Stream data, offsets and delivery state |
| QUIC connection state | Connection-level flow control, keys and shared state |
| Path-specific state | RTT, congestion window, loss and path information |
| UDP socket buffers | Datagram transmission and reception |
| QUIC packet processing state | Packet numbers, ACKs and loss recovery |
| QUIC stream receive state | Out-of-order stream data and reassembly |
| Application receive buffer | Data available to the receiving application |

Again, this is a logical model. A specific QUIC library may organise these structures differently.

### D. Important identifiers and acknowledgements

| Mechanism | Scope | Purpose |
|---|---|---|
| Stream ID | QUIC connection | Identifies an individual stream |
| Stream offset | One stream | Identifies the byte position in that stream |
| QUIC packet number | Relevant packet-number space | Identifies a transmitted packet |
| ACK frame | Packet acknowledgement | Reports received packets |
| Connection flow-control limit | Entire connection | Limits total stream data |
| Stream flow-control limit | One stream | Limits data on that stream |

### E. Timers and loss recovery

QUIC uses recovery mechanisms defined by its transport specification and implementation.

Important concepts include:

- **PTO (Probe Timeout):** A timer used to trigger probe transmissions when acknowledgements are not arriving as expected.
- **Loss detection:** Uses packet acknowledgement and timing information to identify lost packets.
- **Congestion-control state:** Controls how much data can be in flight.
- **Path validation timers and management:** Relevant when establishing or validating additional paths.

Multipath QUIC implementations may have path-specific recovery state. The exact packet-number, ACK and timer model must be checked against the draft revision being studied.

### F. Key takeaway

MP-QUIC carries stream data through QUIC packets over multiple paths.

It provides:

- QUIC stream reliability.
- Stream-level ordering.
- Connection and stream flow control.
- Encryption and authentication.
- Multipath path management and scheduling.

It does not remove all head-of-line blocking: data within an individual ordered stream still needs to be reassembled in order.

---

# 2. Compare the Two Protocol Stacks

## Q300. Draw the two stacks side by side. Place reliability, ordering, congestion control, security, path identification and scheduling at the layer where each lives.

### A. MPTCP stack

```text
+----------------------------------+
|           Application            |
|      TCP socket / byte stream    |
+----------------------------------+
|               MPTCP              |
|                                  |
| Connection-level DSN             |
| Data-level reliability           |
| DSS mapping                      |
| Data ACK                         |
| Connection-level reassembly      |
| Multipath scheduling             |
| Subflow management               |
+----------------------------------+
|          TCP subflows             |
|                                  |
| TCP sequence numbers             |
| TCP ACKs                         |
| TCP retransmission               |
| TCP congestion control           |
| TCP receive-window flow control  |
+----------------------------------+
|                IP                |
+----------------------------------+
|          Link / Physical          |
+----------------------------------+
```

### B. MP-QUIC stack

```text
+----------------------------------+
|           Application            |
|          QUIC streams             |
+----------------------------------+
|           QUIC transport          |
|                                  |
| Stream IDs and offsets           |
| Stream reliability               |
| Stream reassembly                |
| ACK and loss recovery            |
| Congestion control               |
| Connection and stream flow ctrl  |
| TLS-based security               |
+----------------------------------+
|       Multipath QUIC extension    |
|                                  |
| Path identification              |
| Path validation and management   |
| Multipath scheduling             |
| Multipath packet handling        |
+----------------------------------+
|                UDP               |
+----------------------------------+
|                IP                |
+----------------------------------+
|          Link / Physical          |
+----------------------------------+
```

The exact division between QUIC core and multipath extension depends on the draft and implementation. The diagrams show conceptual responsibilities.

### C. Mechanism comparison

| Mechanism | MPTCP | MP-QUIC |
|---|---|---|
| Application interface | TCP socket / ordered byte stream | QUIC streams |
| Reliability | TCP subflow reliability plus MPTCP data-level reliability | QUIC packet and stream-data recovery |
| Ordering | TCP ordering per subflow plus MPTCP connection-level ordering | Stream offsets and per-stream ordering |
| Congestion control | TCP congestion control on subflows, with coupled multipath algorithms where supported | QUIC congestion control, with multipath coupling or path-specific behaviour as specified by the implementation |
| Security | TCP does not inherently encrypt application data; applications may add TLS | QUIC integrates TLS-based security |
| Path identification | TCP subflows and MPTCP connection management | QUIC connection and multipath path identifiers |
| Scheduling | MPTCP scheduler selects subflow for data | Multipath QUIC scheduler selects path for packets/data |
| Transport substrate | TCP over IP | QUIC over UDP/IP |
| State location | Commonly kernel TCP/MPTCP stack | Commonly user-space QUIC library, although implementation varies |

### D. Key conceptual difference

MPTCP extends TCP and coordinates several TCP subflows under one logical connection.

MP-QUIC extends QUIC and uses its stream-based, encrypted transport architecture to support multiple paths.

Neither protocol should be described as simply sending half the data over Wi-Fi and half over cellular. Actual scheduling depends on path state, congestion control, ordering, flow control and application needs.

---

# 3. Network Assumptions and Protocol State

## Q301. What does each protocol assume about the network: a stable 4-tuple, TCP options passing, UDP passing? What breaks, and how gracefully, when each assumption is violated?

A 4-tuple identifies a transport flow using:

```text
Source IP address
Source port
Destination IP address
Destination port
```

### A. MPTCP assumptions

MPTCP uses TCP subflows and MPTCP TCP options.

It therefore depends on:

1. TCP connectivity between endpoints.
2. The ability to negotiate MPTCP through TCP options.
3. Additional subflows being established where multipath is desired.
4. Network devices not interfering with required MPTCP signalling.

**What happens if TCP options are blocked or modified?**

- MPTCP negotiation may fail.
- The connection may operate using ordinary TCP behaviour, depending on the fallback and failure conditions.
- Additional subflows may not be established.
- Multipath benefits may therefore be unavailable.

**What happens if an address or path changes?**

MPTCP can establish additional subflows using its connection-management mechanisms, subject to reachability, authentication and implementation support.

A subflow is associated with a particular network path and 4-tuple. The logical MPTCP connection is not simply identical to one fixed 4-tuple.

### B. MP-QUIC assumptions

MP-QUIC uses QUIC over UDP.

It depends on:

1. UDP traffic being permitted.
2. QUIC packets reaching the peer.
3. QUIC connection and path-management mechanisms functioning.
4. Additional paths being validated and usable.

**What happens if UDP is blocked?**

- A QUIC connection may fail to establish.
- If an alternative transport is available, an application may use a fallback strategy, but that is an application/deployment decision rather than a guarantee of multipath QUIC.

**What happens if a path's IP address or network changes?**

QUIC's connection ID and migration mechanisms help maintain a connection across address changes.

Multipath QUIC extends path management so multiple paths can be used, subject to the specific protocol design and implementation.

### C. Comparison

| Network condition | MPTCP | MP-QUIC |
|---|---|---|
| TCP available, MPTCP options pass | Can establish multipath operation if both endpoints support it | Not relevant to QUIC's UDP transport |
| TCP options blocked | Multipath negotiation or subflow establishment may fail; fallback may be possible | Not dependent on TCP options |
| UDP blocked | TCP/MPTCP may still work | QUIC may fail |
| NAT or address translation | Can complicate subflow establishment and address reachability | Can complicate UDP path validation and reachability |
| IP address changes | Additional MPTCP subflow mechanisms may help | QUIC connection IDs and migration help |
| One path fails | Can continue over another surviving subflow if available | Can continue over another surviving validated path if available |

**Important:** Neither protocol guarantees that every network transition will be seamless. Reachability, NAT behaviour, firewall rules, path validation and implementation support all matter.

---

## Q302. Where does protocol state live (kernel or library, connection or path)? What does that imply for failure, upgrade, debugging and CPU cost?

### A. MPTCP state

On common Linux deployments, MPTCP is integrated into the kernel TCP networking stack.

Its state includes:

**Connection-level state:**

- Logical MPTCP connection.
- DSN and Data ACK tracking.
- Connection-level reassembly.
- Subflow association and management.

**Subflow-level state:**

- TCP sequence numbers.
- Congestion window.
- RTT estimates.
- Retransmission state.
- Receive-window state.

The connection-level and subflow-level states work together.

### B. MP-QUIC state

Many QUIC implementations are libraries running in user space.

Their state includes:

**Connection-level state:**

- Connection IDs.
- Cryptographic keys.
- Stream state.
- Connection-level flow control.
- Connection management.

**Path-level state:**

- Path identifiers.
- RTT estimates.
- Congestion-control state.
- Loss-recovery state.
- Validation and path status.

The exact architecture depends on the implementation. QUIC is not inherently restricted to user space.

### C. Comparison

| Aspect | MPTCP on Linux | Common user-space QUIC implementation |
|---|---|---|
| Main implementation location | Kernel | User-space library |
| Connection state | Kernel networking stack | QUIC library |
| Path/subflow state | TCP subflows in kernel | Path state in QUIC implementation |
| Upgrade | May require kernel or OS changes | Library can often be upgraded with the application |
| Debugging | Kernel tracing, socket tools, packet capture | Library logs, qlog and packet capture |
| CPU considerations | Kernel processing and context-switch costs | User/kernel transitions, encryption and library processing |
| Failure isolation | Kernel networking behaviour affects multiple applications | Application/library failures can be more isolated |

### D. Why does state location matter?

**1. Failure**

A kernel networking bug can affect multiple applications using that kernel functionality.

A user-space QUIC library bug may affect applications using that library without necessarily affecting all system networking.

**2. Upgrade**

Kernel-integrated MPTCP support may require an OS/kernel update.

A user-space QUIC implementation can often be upgraded independently with an application.

**3. Debugging**

MPTCP debugging may involve:

```bash
ip mptcp
ss -ti
ss -m
```

QUIC debugging may involve:

- qlog.
- Library-specific logs.
- Packet captures.
- Connection and path statistics.

**4. CPU and performance**

Neither kernel nor user space is automatically faster.

Performance depends on:

- Packet rate.
- Copying and context switches.
- Encryption overhead.
- Scheduling implementation.
- Memory management.
- Hardware acceleration.
- Operating-system and library design.

**Key takeaway:** The location of protocol state affects deployment, debugging, upgrade flexibility and performance, but it does not independently determine which protocol is faster.

---

# 4. Remove a Mechanism and Predict What Breaks

## Q303. Delete one mechanism and say what breaks, and in which scenario: MPTCP's DSS checksum, MPTCP's Data ACK, MP-QUIC's per-path packet number space, MP-QUIC's PATH_ABANDON.

This question tests whether you understand why a mechanism exists rather than merely memorising its name.

### A. Remove the MPTCP DSS checksum

The DSS checksum can provide additional protection for the mapping between data-level and subflow-level sequence spaces.

**What may break or weaken?**

- The receiver loses that additional mapping-integrity check.
- Some forms of corruption or mapping inconsistency may be harder to detect through that mechanism.
- The connection may rely more heavily on lower-layer checks and other protocol validation.

**Important qualification:** The DSS checksum is not universally mandatory in every MPTCP connection. Its use depends on negotiation and protocol configuration.

**Scenario:** A network or implementation environment where protection against corrupted or inconsistent data mappings is important.

Do not claim that removing the checksum automatically causes all data to be corrupted. It removes an additional integrity mechanism.

### B. Remove the MPTCP Data ACK

The Data ACK provides connection-level acknowledgement of logical MPTCP data.

**What may break?**

- The sender loses the normal connection-level acknowledgement mechanism for DSN progress.
- It becomes difficult to distinguish successful subflow-level delivery from successful delivery of the logical data stream.
- Data-level retransmission and recovery become unreliable or impossible to manage as designed.

**Scenario:** A multipath connection where a TCP subflow reports delivery, but the receiver has not yet received all required logical data in order.

**Why TCP ACK alone is insufficient:** TCP ACKs acknowledge bytes within individual subflows. They do not replace MPTCP's connection-level data acknowledgement.

### C. Remove MP-QUIC's per-path packet number space

The purpose of per-path packet-number handling in the relevant multipath design is to support correct packet identification and recovery when paths behave differently.

**What may break or become harder?**

- Packet-number interpretation and ACK processing may become more complicated.
- Loss detection may be affected by packets taking paths with very different RTTs.
- Reordering across paths can make it harder to interpret packet arrival and acknowledgement behaviour.
- Recovery and congestion-control accounting may become less reliable if the protocol's packet-number model is not followed.

**Scenario:** Two paths with substantially different RTTs, where packets can arrive in an order very different from the order in which they were sent.

**Important qualification:** Explain this using the packet-number model of the specific MP-QUIC draft revision under study. Do not assume all historical research implementations and later drafts use identical packet-number rules.

### D. Remove MP-QUIC's PATH_ABANDON mechanism

PATH_ABANDON is a path-management mechanism in the relevant multipath QUIC design.

**What may break?**

- An endpoint may lose the standardised way to explicitly signal that a path should be abandoned.
- Peer path-state management may become less clear.
- A failed, unusable or unwanted path may remain represented in connection state longer than necessary.
- Scheduling and path cleanup may become less efficient or coordinated.

**Scenario:** A cellular path becomes unusable or too expensive, and an endpoint wants to stop using it while retaining another path.

**Important qualification:** Exact frame semantics must be checked against the draft revision being discussed.

### E. Summary table

| Removed mechanism | Main responsibility lost | Likely consequence |
|---|---|---|
| MPTCP DSS checksum | Additional data-mapping integrity check | Weaker detection of certain mapping errors |
| MPTCP Data ACK | Connection-level data acknowledgement | Data-level delivery and recovery cannot operate correctly as designed |
| MP-QUIC per-path packet-number space | Path-aware packet identification and recovery model | More difficult packet/ACK/loss interpretation under path asymmetry |
| MP-QUIC PATH_ABANDON | Explicit path-abandon signalling | Less coordinated path removal and state management |

**Viva technique:** For any removed mechanism, answer four things:

1. What information or function does it provide?
2. Which component uses it?
3. What scenario needs it?
4. What breaks or becomes less reliable without it?

---

# 5. Predict Behaviour Under Different Network Conditions

## Q304. Fill a prediction table: symmetric paths, RTT asymmetry, rate asymmetry, one lossy path, path failure, shared bottleneck, NAT, blocked UDP. For each, what does each protocol do and why? Mark which cells are evidence-backed and which are your reasoning.

This question is important because it connects protocol mechanisms to real network behaviour.

### A. Scenario table

| Network condition | MPTCP expected behaviour | MP-QUIC expected behaviour |
|---|---|---|
| Symmetric paths | A scheduler can distribute data across both subflows. Benefits depend on congestion control and scheduling overhead. | A scheduler can distribute data across both paths. Benefits depend on path management, congestion control and scheduling. |
| RTT asymmetry | Data sent on the lower-RTT subflow may arrive sooner. Data arriving over the slower subflow may cause connection-level reordering and blocking. | Data on different paths may arrive out of order. Stream-offset reassembly is required; a missing byte range can block that stream. |
| Rate asymmetry | A scheduler may send more data over the higher-capacity path, but RTT, congestion window and reordering matter. | A scheduler may favour the path with more available capacity, subject to congestion and recovery state. |
| One lossy path | TCP loss recovery may reduce the affected subflow's performance. The scheduler may prefer the other subflow if eligible. | QUIC loss recovery affects packets sent on the lossy path. The scheduler may use another eligible path. |
| One path fails | The surviving subflow may continue carrying connection data if it remains usable. | The surviving path may continue carrying connection data if it remains validated and usable. |
| Shared bottleneck | Coupled congestion control is important to avoid unfairness and overloading a shared bottleneck. | Multipath congestion-control design must consider shared congestion and fairness; behaviour depends on implementation. |
| NAT | NAT may affect subflow reachability and address signalling; additional subflows may fail. | NAT can affect UDP path reachability and validation; connection IDs and path validation help but do not eliminate all problems. |
| UDP blocked | MPTCP may still operate if TCP and its required signalling are permitted. | QUIC/MP-QUIC cannot normally operate over a path where UDP traffic is blocked. |

### B. Evidence-backed versus reasoned predictions

Mark your table using three labels:

- **[SPEC]** - Directly supported by a protocol specification.
- **[PAPER]** - Supported by a research paper or experimental result.
- **[REASONING]** - A prediction based on protocol mechanisms, not a directly measured result.

Example:

| Claim | Evidence label |
|---|---|
| MPTCP uses multiple TCP subflows and DSS mappings | [SPEC] |
| MPTCP has connection-level data acknowledgement | [SPEC] |
| MP-QUIC uses multipath path-management mechanisms | [DRAFT] |
| A slow path can cause data reordering | [REASONING] based on path-delay differences |
| A particular scheduler gives 20% higher throughput | [PAPER] only if a specific experiment supports it |

Do not assign a numerical throughput improvement without an actual measurement or a cited experiment.

### C. Why can adding a path decrease useful throughput?

Adding a second path does not guarantee higher application goodput.

It can decrease useful throughput because:

1. **Reordering:** A fast path may deliver later data before earlier data on a slow path.
2. **Head-of-line blocking:** The receiver may have to wait for missing earlier bytes in an ordered stream.
3. **Retransmissions:** Loss on one path may create additional recovery traffic.
4. **Congestion-control interaction:** A poorly coordinated controller may behave inefficiently or unfairly.
5. **Shared bottlenecks:** Two paths may not represent two independent capacity resources.
6. **Scheduling overhead:** The scheduler may make poor decisions when path conditions change rapidly.
7. **Buffer pressure:** Out-of-order data may occupy receive memory while waiting for missing data.

**Key takeaway:** More paths create more opportunities, but also more coordination and reassembly costs.

---

# 6. Security, Privacy and Design Trade-offs

## Q305. Compare the security and privacy of the two: threats in RFC 6181 against QUIC's threat model. What does multipath expose, and how could many paths or subflows be abused for denial of service?

### A. MPTCP security considerations

RFC 6181 discusses security considerations for MPTCP.

Important concerns include:

- Attackers attempting to inject or manipulate subflows.
- Abuse of address signalling.
- Resource exhaustion through additional subflow creation.
- Risks from unauthenticated or improperly validated path information.
- Denial-of-service attacks against connection state and network resources.

MPTCP includes mechanisms such as authentication for subflow joining to help prevent an attacker from simply attaching an unrelated TCP connection to an existing MPTCP connection.

However, authentication does not eliminate every attack or resource-exhaustion risk.

### B. QUIC security model

QUIC uses TLS-based cryptographic protection.

Its security model includes:

- Encryption of protected packet contents.
- Authentication and integrity protection.
- Connection IDs.
- Address validation and path validation mechanisms.
- Protection against certain forms of packet injection and manipulation.

QUIC's use of encryption improves confidentiality and integrity, but it does not make the protocol immune to denial-of-service attacks.

### C. What additional privacy risks come from multipath?

Using multiple paths can expose more network information.

For example:

1. **Multiple IP addresses:** The peer may learn several addresses associated with one connection.
2. **Location inference:** Different network addresses can reveal information about a user's network attachment or approximate location.
3. **Linkability:** An observer may correlate activity across different interfaces or networks.
4. **Network identity:** The use of Wi-Fi and cellular paths may reveal information about a user's access networks.
5. **Traffic correlation:** Observers may compare timing and volume across paths.

### D. How could many paths be abused for denial of service?

An attacker or malicious peer may attempt to create excessive path or subflow state.

Potential consequences:

- More memory consumption.
- More connection-management work.
- More cryptographic or validation processing.
- Increased packet-processing load.
- More scheduler and congestion-control state.
- Increased bandwidth consumption.

A protocol implementation therefore needs validation, resource limits, rate limiting and sensible path-management policies.

### E. Comparison

| Aspect | MPTCP | MP-QUIC |
|---|---|---|
| Security foundation | TCP plus MPTCP-specific authentication and security mechanisms; application encryption may be separate | QUIC integrates TLS-based security |
| Path addition | Subflow joining and authentication mechanisms | QUIC path-management and validation mechanisms |
| Privacy exposure | Multiple addresses and subflows | Multiple addresses, connection IDs and path activity |
| DoS concerns | Excessive subflows and connection state | Excessive path validation, packet processing and connection state |
| Confidentiality | Not inherently provided by TCP/MPTCP alone | Encrypted transport packets |

**Key takeaway:** Encryption protects data, but security also includes authentication, resource management, path validation and resistance to denial of service.

---

## Q306. Which requirement does each protocol's design most clearly reflect: backward compatibility or a clean slate? What did each pay for that choice?

### A. MPTCP: backward compatibility

MPTCP was designed as an extension of TCP.

Its goal was to allow existing TCP applications to benefit from multipath transport without requiring them to understand individual paths.

**Advantages:**

- Retains a TCP-like application interface.
- Can support legacy applications through existing socket APIs.
- Builds on TCP's established reliability model.
- Can fall back to ordinary TCP behaviour in supported failure situations.

**Costs:**

- Must work with TCP's existing architecture and sequence-number model.
- Depends on TCP options and middlebox compatibility.
- Needs coordination between subflow-level and connection-level reliability.
- Inherits some TCP design constraints.

### B. QUIC: cleaner transport design

QUIC was designed as a new transport protocol over UDP.

It introduced features such as:

- Integrated TLS-based security.
- Multiple independent streams.
- Connection IDs.
- User-space implementation in many deployments.
- Connection migration.

**Advantages:**

- More flexibility for transport evolution.
- Stream multiplexing avoids TCP's connection-wide byte-stream ordering dependency.
- Easier deployment of protocol updates through user-space implementations.
- Integrated encryption.

**Costs:**

- Requires UDP connectivity.
- QUIC implementations must implement transport reliability, congestion control and flow control.
- User-space implementations introduce their own performance and operational considerations.
- Encryption can make passive network inspection more difficult.

### C. MP-QUIC's position

Multipath QUIC combines QUIC's architecture with the goal of concurrent path use.

It can benefit from QUIC's flexibility, but it must still solve:

- Path validation.
- Packet and ACK handling across paths.
- Congestion control.
- Scheduling.
- Reordering.
- Resource and privacy concerns.

### D. Comparison

| Design choice | MPTCP | QUIC / MP-QUIC |
|---|---|---|
| Primary philosophy | Extend an existing transport | Design a new transport architecture |
| Application compatibility | TCP socket compatibility | QUIC-aware application/library interface |
| Network substrate | TCP | UDP |
| Security | May be provided by application protocols such as TLS | Integrated TLS-based transport security |
| Main trade-off | Compatibility with TCP and its constraints | New implementation and deployment requirements |

**Key takeaway:** MPTCP prioritises extending an established transport with minimal application disruption. QUIC prioritises transport flexibility and evolution, while accepting the need for new implementations and UDP connectivity.

---

# 7. Critical Design Thinking

## Q307. Which design decision in each protocol would you change with hindsight, and what would the change cost?

This is an open-ended design question. There is no single correct answer. A good answer must identify a real limitation and explain the trade-off of changing it.

### A. Possible MPTCP improvement

**Proposed change:** Improve the scheduler's awareness of application deadlines and receiver-side reordering costs.

A scheduler could consider:

- Path RTT.
- Path capacity.
- Congestion window.
- Loss rate.
- Expected arrival time.
- Amount of out-of-order data already buffered.
- Application deadlines.

**Why change it?**

A scheduler that only focuses on path speed may send data over a path that has high delay, creating reordering and application-level blocking.

**Potential benefit:**

- Reduced out-of-order buffering.
- Better completion time.
- Improved latency for deadline-sensitive traffic.

**Cost:**

- More complex scheduling.
- Additional state and computation.
- More difficult tuning.
- Potential loss of throughput if the scheduler becomes too conservative.

### B. Possible MP-QUIC improvement

**Proposed change:** Make application-aware scheduling easier while preserving transport-level fairness and security.

The transport could expose useful path statistics or allow an application to provide hints such as:

- Data priority.
- Deadline.
- Stream importance.
- Path cost or energy preference.

**Why change it?**

Different applications have different requirements. A bulk file transfer values total completion time, while a real-time application may value low delay and low jitter.

**Potential benefit:**

- Better application-specific scheduling.
- More efficient path use.
- Better handling of battery and data-cost constraints.

**Cost:**

- More complex APIs.
- Greater implementation burden.
- Risk of applications making poor scheduling decisions.
- Potential privacy and policy concerns.
- Need to preserve congestion-control fairness.

### C. How to answer in a viva

Use this format:

> I would change [mechanism] because it causes [specific limitation] in [scenario]. My proposed improvement is [change]. It could improve [benefit], but it would cost [complexity, fairness, performance or deployment trade-off].

Avoid answers such as "I would make it faster" or "I would remove all overhead." Explain the mechanism and the cost.

---

# 8. Packet Capture and Verification

## Q308. Given a Wireshark capture of each protocol that includes a handshake and an added path, what can you read and what is hidden? How would you verify from the capture that the second path carries data?

### A. What can be observed in an MPTCP capture?

Depending on the capture location and Wireshark version, you may be able to inspect:

- TCP SYN and SYN-ACK.
- MPTCP capability negotiation.
- MPTCP option types.
- Subflow establishment.
- MP_JOIN activity.
- DSS mappings.
- TCP sequence numbers and ACKs.
- Data ACKs.
- FIN/RST and connection termination.
- Source and destination addresses and ports.

MPTCP uses TCP options to carry MPTCP signalling.

### B. What can be observed in a QUIC / MP-QUIC capture?

You may be able to inspect:

- UDP source and destination ports.
- QUIC long-header packets during connection establishment.
- Version information.
- Connection IDs.
- QUIC handshake traffic.
- Packet sizes and timing.
- Addresses and ports associated with different paths.
- Some visible QUIC frame information, depending on encryption and packet keys.

After encryption is established, many QUIC frame contents are protected.

A passive capture may not reveal stream payloads, stream offsets, or path-management frame details without the relevant decryption keys and compatible analysis tools.

### C. What is visible and what is hidden?

| Information | MPTCP | MP-QUIC |
|---|---|---|
| Source/destination IP and port | Usually visible | Usually visible |
| Initial transport handshake | TCP handshake visible | QUIC Initial handshake packets visible |
| Path/subflow creation | MPTCP TCP options may be visible | Multipath control information may be encrypted |
| Data payload | Visible unless protected by application encryption | Encrypted in QUIC |
| Sequence/packet information | TCP sequence numbers and MPTCP options visible | QUIC packet numbers and stream information may be protected or unavailable without keys |
| Timing and packet sizes | Visible | Visible |
| Retransmission behaviour | Can be inferred from TCP sequence and ACK patterns | Requires QUIC-aware analysis; exact interpretation may need qlog |

### D. How do you verify that the second path carries data?

**For MPTCP:**

1. Identify the initial MPTCP connection.
2. Find the additional subflow establishment, commonly involving MP_JOIN.
3. Identify the second subflow's source/destination IP and port tuple.
4. Filter packets belonging to that second subflow.
5. Check for data-bearing TCP packets and DSS mappings.
6. Confirm that the subflow carries actual data, not just handshake or control packets.
7. Compare packet counts and byte counts across both subflows.

A second subflow existing does not prove it carries application data. You must find data-bearing traffic.

**For MP-QUIC:**

1. Identify the QUIC connection.
2. Identify the additional path using the relevant path-management information.
3. Confirm that the path is established and validated, where the design requires validation.
4. Identify packets transmitted over the second path using the available path identifiers, connection information and endpoint logs.
5. Check whether the packets carry stream data or other data-bearing frames.
6. Use qlog or implementation logs to associate packets with paths and stream data.
7. Compare bytes and packet counts across paths.

Because multipath control frames and other QUIC frame contents may be encrypted, a packet capture alone may not be sufficient.

### E. Useful tools

- **Wireshark:** Packet-level inspection.
- **tcpdump:** Capture network packets.
- **MPTCP Linux tools:** Inspect MPTCP connection and subflow state.
- **qlog:** Inspect QUIC events, recovery and path-related information when supported.
- **iperf3 or HTTP transfer tools:** Generate workloads for measurement.

Example Linux capture command:

```bash
sudo tcpdump -i any -w multipath_capture.pcap
```

Open the resulting file in Wireshark.

For MPTCP, useful inspection commands include:

```bash
ip mptcp
ss -ti
ss -m
```

The exact availability and output depend on the Linux kernel and installed tools.

### F. Key takeaway

A capture showing two addresses or two handshakes is not enough to prove useful multipath data transfer.

You must verify that both paths carry actual data, using packet evidence and, where needed, endpoint logs.

---

# 9. Connect the Mechanisms Across Both Protocols

## Q309. Pick five mechanisms across both protocols and draw the arrows between them: which MPTCP problem led to which MP-QUIC design decision, and where did MP-QUIC keep MPTCP's answer?

This question tests whether you understand the relationship between the protocols without assuming that MP-QUIC simply copies MPTCP.

### A. Five important connections

#### Connection 1 - MPTCP subflows and MP-QUIC paths

**MPTCP:**

- A logical connection contains multiple TCP subflows.
- Each subflow has its own TCP state and network 4-tuple.

**MP-QUIC:**

- A logical QUIC connection can use multiple paths.
- Path management identifies and maintains the paths used by the connection.

**Shared idea:** One logical transport connection can use multiple network paths.

**Difference:** MPTCP builds on multiple TCP subflows; MP-QUIC manages multiple paths within the QUIC architecture.

#### Connection 2 - MPTCP DSN and QUIC stream offsets

**MPTCP problem:**

Data sent through different subflows can arrive out of order. The receiver needs a way to reconstruct the original logical byte stream.

**MPTCP solution:**

- Connection-level DSN.
- DSS mappings.
- Data-level reassembly.

**QUIC approach:**

- Stream IDs identify streams.
- Stream offsets identify positions within streams.
- Stream reassembly reconstructs ordered stream data.

**Shared idea:** Logical data positions are independent of the particular network packet or path used to carry them.

**Difference:** MPTCP uses a connection-level data sequence space; QUIC uses per-stream byte offsets.

#### Connection 3 - MPTCP Data ACK and QUIC ACK/recovery

**MPTCP:**

- TCP ACKs acknowledge subflow-level data.
- Data ACK acknowledges logical MPTCP data delivery.

**QUIC:**

- ACK frames acknowledge QUIC packets.
- Stream delivery and loss recovery determine whether stream data needs to be sent again.

**Shared idea:** Packet/subflow reception and application-data delivery are related but distinct concepts.

**Difference:** MPTCP explicitly uses a connection-level Data ACK in addition to TCP ACKs. QUIC's reliability is organised around packet acknowledgement and retransmission of the relevant information.

#### Connection 4 - MPTCP scheduling and MP-QUIC scheduling

**MPTCP:**

- A scheduler chooses which subflow should transmit data.
- It must consider path characteristics and reordering.

**MP-QUIC:**

- A multipath scheduler chooses which path should carry packets or data.
- It must consider congestion, loss, RTT and application requirements.

**Shared idea:** The transport needs a policy for distributing traffic across available paths.

**Difference:** The scheduling unit and available information depend on each protocol's architecture and implementation.

#### Connection 5 - MPTCP congestion-control coupling and MP-QUIC multipath fairness

**MPTCP problem:**

If each subflow behaves like an independent TCP flow, one multipath connection may take more than its fair share of a shared bottleneck.

**MPTCP solution:**

Coupled congestion-control algorithms attempt to balance the goals of improving multipath throughput and behaving fairly toward competing single-path TCP flows.

**MP-QUIC requirement:**

A multipath QUIC design also needs to consider congestion control and fairness when several paths are used.

**Shared idea:** Multipath transport must not treat every path as an unrelated unlimited source of capacity.

**Difference:** The exact coupling model and congestion-control behaviour depend on the MP-QUIC design and implementation. Do not assume it uses MPTCP's LIA, OLIA or BALIA.

### B. Connection diagram

```text
MPTCP PROBLEM / MECHANISM
          |
          v
Multiple TCP subflows
          |
          v
One logical connection
          |
          +------------------------------+
          |                              |
          v                              v
DSN + DSS mapping                Subflow scheduling
          |                              |
          v                              v
Logical reassembly               Path selection
          |                              |
          +---------------+--------------+
                          |
                          v
              MULTIPATH QUIC DESIGN
                          |
          +---------------+----------------+
          |               |                |
          v               v                v
      QUIC streams    Path management   Multipath scheduler
      and offsets     and identifiers   and congestion control
          |               |                |
          v               v                v
      Reassembly       Multiple paths    Path selection
          |               |                |
          +---------------+----------------+
                          |
                          v
              One logical QUIC connection
```

### C. What did MP-QUIC keep conceptually from MPTCP?

MP-QUIC keeps several broad multipath principles:

- One logical connection can use multiple paths.
- Paths need to be identified and managed.
- Data may arrive out of order.
- The receiver must reconstruct logical application data.
- A scheduler must decide where traffic should be sent.
- Congestion control and fairness matter.
- Path failures should not necessarily destroy the whole logical connection.

But it implements these ideas using QUIC's own stream, packet, security and path-management architecture.

### D. What should not be claimed?

Do not say:

- MP-QUIC is just MPTCP over UDP.
- MP-QUIC uses exactly the same sequence numbers as MPTCP.
- MP-QUIC uses MPTCP's DSS option.
- MP-QUIC automatically solves all head-of-line blocking.
- MP-QUIC automatically provides better throughput.
- All MP-QUIC implementations use the same scheduler and congestion-control algorithm.

---

# 10. Master Comparison - MPTCP vs MP-QUIC

| Feature | MPTCP | MP-QUIC |
|---|---|---|
| Underlying transport | TCP | QUIC over UDP |
| Logical connection | Multiple TCP subflows | One QUIC connection with multiple paths |
| Application abstraction | TCP-like ordered byte stream | QUIC streams |
| Data identification | DSN and DSS mappings | Stream IDs and stream offsets |
| Packet/transport identification | TCP sequence numbers per subflow | QUIC packet numbers under the relevant packet-number model |
| Acknowledgement | TCP ACK plus MPTCP Data ACK | QUIC ACK frames and stream recovery |
| Reliability | TCP subflow reliability plus MPTCP data-level recovery | QUIC loss recovery and reliable stream data |
| Ordering | Connection-level ordered byte stream | Ordered bytes within each stream |
| Congestion control | TCP congestion control with multipath coupling where supported | QUIC congestion control and multipath-specific behaviour |
| Scheduling | Selects a TCP subflow | Selects a QUIC path |
| Security | TCP does not inherently encrypt data | TLS-based security integrated into QUIC |
| Path management | MPTCP subflow and address-management mechanisms | QUIC multipath path-management mechanisms |
| Main deployment dependency | TCP and MPTCP support; TCP options must work | UDP and QUIC support |
| Common implementation location | Kernel-integrated implementations | Often user-space libraries |

---

# 11. Important Viva Questions and Model Answers

### 1. Why does MPTCP need both TCP ACK and Data ACK?

TCP ACK acknowledges bytes received within an individual subflow. Data ACK acknowledges progress in the logical MPTCP data sequence space. A subflow may receive data even though the logical byte stream still has a missing earlier range.

### 2. What is the difference between DSN and TCP sequence number?

DSN identifies bytes in the overall MPTCP connection. TCP sequence number identifies bytes within one TCP subflow.

### 3. Does MP-QUIC use TCP sequence numbers?

No. MP-QUIC uses QUIC's packet-number and stream-offset mechanisms, not TCP sequence numbers.

### 4. Does QUIC use UDP for reliability?

No. UDP is an unreliable datagram transport. QUIC implements its own reliability, loss detection and congestion-control mechanisms above UDP.

### 5. Does QUIC eliminate head-of-line blocking?

It avoids TCP's connection-wide byte-stream head-of-line blocking between independent streams. However, missing data can still block delivery within an individual ordered QUIC stream.

### 6. If a packet is lost in QUIC, is the exact same packet retransmitted?

Generally no. QUIC sends the relevant information again in a new packet, normally with a new packet number. Stream data retains its stream offset.

### 7. What happens if one MPTCP subflow fails?

The logical connection may continue using surviving subflows if they remain usable. If no usable path remains, communication may fail.

### 8. What happens if one MP-QUIC path fails?

The connection may continue over another usable path, depending on path state, validation and implementation behaviour.

### 9. Why can multipath reduce performance?

Reordering, loss, retransmissions, congestion-control interactions, shared bottlenecks and scheduling overhead can outweigh the extra path capacity.

### 10. Why is a second path not necessarily a second independent capacity resource?

Both paths may share a physical bottleneck, upstream link, access network or congestion point.

### 11. What is the difference between flow control and congestion control?

Flow control prevents the sender from overwhelming the receiver. Congestion control prevents the sender from overwhelming the network.

### 12. What is the difference between a QUIC stream offset and a QUIC packet number?

A stream offset identifies a byte's position within a stream. A packet number identifies a transmitted QUIC packet.

### 13. Why does MPTCP use DSS?

DSS communicates the mapping between subflow TCP sequence numbers and the connection-level DSN.

### 14. Why can Wireshark alone be insufficient for MP-QUIC analysis?

QUIC protects much of its transport information through encryption. Endpoint logs or qlog and suitable decryption keys may be required to understand stream and path behaviour.

### 15. How do you prove that both paths carried application data?

Identify the two paths, inspect data-bearing packets or endpoint logs, and verify that actual data bytes were transmitted over each path. A second handshake alone is not proof.

---

# 12. What You Must Be Able to Draw Without Notes

Before the viva, practise drawing these diagrams from memory:

1. MPTCP end-to-end data flow from `write()` to `read()`.
2. MP-QUIC end-to-end data flow from stream write to stream read.
3. MPTCP connection-level DSN versus subflow-level TCP sequence numbers.
4. QUIC stream IDs, stream offsets and packet numbers.
5. MPTCP and MP-QUIC protocol stacks side by side.
6. A two-path reordering example.
7. A path failure with traffic continuing over the surviving path.
8. The relationship between scheduling and congestion control.
9. A packet capture showing initial connection setup and a second path.
10. The mechanism-to-mechanism connection diagram from Q309.

---

# 13. Practical Self-Assessment

Use this checklist to test whether you genuinely understand the section.

- [ ] I can trace an MPTCP upload from application write to receiver read.
- [ ] I can explain the difference between TCP sequence numbers and DSNs.
- [ ] I can explain the difference between TCP ACK and Data ACK.
- [ ] I understand why MPTCP needs DSS mappings.
- [ ] I can trace a QUIC stream write through packet transmission and receiver reassembly.
- [ ] I can distinguish stream offsets from packet numbers.
- [ ] I understand QUIC ACKs, loss recovery and PTO.
- [ ] I can explain stream-level versus connection-level flow control.
- [ ] I can draw both protocol stacks.
- [ ] I can explain what happens if TCP options are blocked or UDP is blocked.
- [ ] I understand where kernel and user-space protocol state may live.
- [ ] I can explain the purpose of the four mechanisms in Q303.
- [ ] I can predict behaviour under all eight network conditions in Q304.
- [ ] I can compare the security and privacy trade-offs.
- [ ] I can explain what is visible and encrypted in packet captures.
- [ ] I can verify that a second path actually carries data.
- [ ] I can connect at least five MPTCP mechanisms or problems to MP-QUIC design ideas.

**Completion standard:** Do not mark this section complete merely because you have saved the answers. You should be able to explain Q298 and Q299 using diagrams, answer Q303 and Q304 through cause-and-effect reasoning, and defend the distinctions in Q300 and Q309.

## Save this file

Use this folder and filename\:

```text
09_End_to_End_Trace_Q298-309/
└── End_to_End_Trace_MPTCP_MPQUIC.md
```

## How to study this section

I recommend this order\:

1. **Q298-299 first\:** Understand the complete data journey. These are the foundation of the section.
2. **Q300-302\:** Understand where each mechanism lives and how the two protocols differ.
3. **Q303-304\:** Practise predicting failures and network behaviour.
4. **Q305-307\:** Understand security and design trade-offs.
5. **Q308-309\:** Practise packet-level verification and connect the mechanisms.

**One important note\:** This section is now drafted, but the exact MP-QUIC packet-number model, `PATH_ABANDON` semantics and path-management details must be checked against the particular draft revision your team is using. Don't mix details from the 2017 research implementation with later IETF draft designs.

Next, we should check your original plan's remaining shared sections and make sure your individually led **Part 10 (Q177-Q190)** is also complete.

## Prompt:
11/3/2026, 3:25:34 PM

done what next now

## Response:
11/3/2026, 3:24:42 PM · gpt-6

> **Reviewed original plan sections and assignments**
>
> 
>
> Worked for 6s

The next section in the original plan is **Part 20 — Adjacent Technologies and “Why Not X” (Q310–Q322)**\.

(Pratik leads · Everyone studies)

This section is Pratik's responsibility, so you should coordinate with him rather than independently duplicating his work. fileciteturn20file1

**For your own assigned work, there is one important thing to check before moving on\:**

- **Part 10 (Q177–Q190)\:** You lead this section. Have you completed and saved it?
- **Part 19 (Q298–Q309)\:** Just completed; shared section.
- **Parts 1, 2, 11, 12 and 21\:** Shared sections that everyone must prepare.

My recommendation: **Let's verify and finish your Part 10 first**, if it isn't already complete. Then we can do a full mock viva covering your assigned sections and the shared questions.

## Prompt:
11/3/2026, 3:28:55 PM

not have to do this section part 20, lets move ahead now

## Response:
11/3/2026, 3:28:03 PM · gpt-6

> **Searched files for Part 10 Questions 177–190 content**
>
> 
>
> Worked for 15s

Okay, we’ll skip **Part 20 (Q310-Q322)**\. It is Pratik-led, so you don't need to prepare it as your individual section.

Let's move to the next part of **your assigned work: Part 10 (Q177-Q190)**, which you lead and which is shared with the team.

I've checked the **original plan**, not the condensed version. Part 10 is titled **Applications and Recommendations (Q177-Q190)**\. It is a shared Tier 1 section, and you lead the teach-back.

Let's complete it now. The plan specifically requires each recommendation to state its **hypothesis, supporting evidence, and what would change your mind**\.

Save this as\:

`10_Applications_Recommendations_Q177-190/Applications_and_Recommendations.md`

**document: **

# Part 10 - Applications and Recommendations (Q177-Q190)

**Part:** 10  
**Questions:** Q177-Q190  
**Scope:** Application requirements, scenario predictions, and final protocol recommendations  
**Status:** Shared section - Swamini leads

## How to approach this section

A protocol should not be recommended simply because it achieves higher throughput in one experiment. The correct choice depends on what the application needs.

For every recommendation, distinguish:
- **Hypothesis:** What do we expect?
- **Reasoning:** Why should that happen?
- **Evidence:** What measurement, specification, or published result supports it?
- **Limitation:** What could make the recommendation wrong?

Do not present a prediction as an experimental result.

---

# A. Application needs

## Q177. What does an adaptive-bitrate video client need from the transport? How does adding a path change rebuffering, and why might backup-only beat aggregation for video?

An adaptive-bitrate (ABR) video client needs:
1. Sufficient goodput to download video segments before the playback buffer runs out.
2. Predictable delivery times.
3. Low enough delay and loss to avoid repeated segment-download delays.
4. Stable throughput estimates so that the client can select an appropriate video bitrate.
5. Connection continuity when network conditions change.

**How multipath can help:**

Adding a second path can increase available capacity or provide an alternative when the primary path becomes congested or fails. This may reduce segment download time and prevent rebuffering.

However, aggregation is not always beneficial. If segments or data are distributed across paths with very different RTTs, the client may receive some data late. Reordering and waiting for delayed data can affect when a complete segment becomes usable.

**Why backup-only may be better:**

With backup-only operation, one path carries normal traffic while another is kept available for failure or degradation. This avoids continuously distributing data across paths with very different delays. It can preserve stable delivery while still providing resilience.

**Hypothesis:** For video with a sufficient primary path, backup-only may produce more stable playback than aggressive aggregation. Aggregation may be better when the primary path alone cannot sustain the required bitrate.

**What would change my mind:** If measurements show that aggregation consistently reduces segment completion time and rebuffering without causing harmful delay variation, aggregation would be preferable.

## Q178. Video segments over MPTCP versus over MP-QUIC: how does one stream per segment change blocking behaviour?

The important distinction is how the application maps video data onto transport streams.

**MPTCP:**
- MPTCP presents one reliable byte stream to the application.
- Data can travel over different TCP subflows.
- Each subflow has its own TCP sequence space, while MPTCP uses a connection-level Data Sequence Number (DSN).
- If data sent over a slower path arrives late, later data may need to wait for missing earlier data before the application can consume the continuous byte stream.

**MP-QUIC:**
- QUIC supports multiple independent streams within one connection.
- An application can map separate video segments or objects to separate QUIC streams.
- A delayed stream does not inherently block delivery of data on every other independent stream.
- However, data within an individual stream remains ordered, and application dependencies can still create waiting.

**Important distinction:** One stream per segment is an application design choice, not an automatic property of MP-QUIC. MPTCP also does not automatically create a separate application stream for each segment.

**Hypothesis:** MP-QUIC can provide better isolation between independently requested video segments when the application maps them to separate streams.

**Cost:** More streams and more complicated application-level scheduling may be required. A segment that depends on another segment cannot be played early merely because it arrived on a separate stream.

**What would change my mind:** If the application uses only one ordered stream, or if segment dependencies dominate, the practical advantage of separate QUIC streams may be small.

## Q179. For file transfer, which metric dominates? When does aggregation help, and when does it not?

For large file transfers, the main metric is usually **completion time**, closely related to application goodput.

Other useful measurements include:
- Total transfer time.
- Application-level goodput.
- Retransmissions and packet loss.
- CPU and memory overhead.
- Fairness when multiple connections share a bottleneck.

**When aggregation helps:**

If two paths have genuinely independent available capacity, sending data over both can increase aggregate throughput and reduce completion time.

For example, a device might use a Wi-Fi path and a cellular path whose bottlenecks are independent.

**When aggregation does not help:**

1. **Shared bottleneck:** Both paths eventually pass through the same constrained link, so using both may not increase available capacity.
2. **Receiver-limited:** The receiver cannot process or store data quickly enough to benefit from extra network capacity.
3. **Small files:** Connection setup, scheduling, and recovery overhead may be larger than the time saved.
4. **Highly asymmetric paths:** A slow path may introduce reordering and delay while contributing little useful throughput.
5. **Congestion:** Additional traffic may increase congestion and reduce performance for competing flows.

**Hypothesis:** Aggregation is most useful for large transfers over independent paths when the receiver and network can use the additional capacity.

**What would change my mind:** If the second path does not increase useful goodput or reduces completion time only negligibly, single-path or backup operation may be preferable.

## Q180. Why do latency, jitter and loss matter more than throughput for VoIP? Why can multipath hurt jitter, and which mode suits it?

Voice over IP (VoIP) is delay-sensitive and interactive.

Important metrics:
- **Latency:** Delay between speaking and hearing the other person.
- **Jitter:** Variation in packet arrival times.
- **Packet loss:** Missing voice packets that may create gaps or distortion.

Throughput matters, but voice traffic generally requires much less bandwidth than large file transfers. A connection can have high throughput and still provide poor voice quality if packets arrive too late or irregularly.

**Why multipath can hurt jitter:**

Different paths can have different RTTs, congestion levels and queueing delays. Packets sent close together may arrive far apart. The receiver may need a jitter buffer to smooth delivery, but a larger buffer adds latency.

**Possible modes:**

- **Redundant:** Send duplicate data over multiple paths. This can improve the chance that at least one copy arrives on time, but consumes additional bandwidth.
- **Lowest-latency only:** Use the path with the best delay characteristics. This can reduce jitter, but offers less aggregation.
- **Backup:** Use one primary path and switch when it fails or becomes unsuitable. This offers resilience without continuously distributing packets.

**Hypothesis:** For conversational VoIP, a low-latency path or carefully configured redundancy may be more useful than ordinary throughput aggregation.

**What would change my mind:** If measured jitter and late-packet rates improve under aggregation, without increasing end-to-end delay, aggregation may be suitable.

## Q181. Why might a redundant scheduler suit VoIP or live video but waste capacity for file transfer? What does it cost in goodput?

A redundant scheduler sends copies of data over more than one path.

**Why it can help real-time applications:**

For VoIP or live video, a packet that arrives too late may be practically useless. If one copy is lost or delayed, another copy may arrive in time. This can improve delivery reliability and reduce deadline misses.

**Why it wastes capacity for file transfer:**

For a reliable file transfer, duplicate copies of the same data usually do not provide additional application content. The receiver needs each byte only once. Sending duplicates consumes network capacity that could have carried new data.

**Cost in goodput:**

If the same data is transmitted over two paths, total transmitted traffic increases. Application goodput does not increase proportionally because duplicate bytes are not new useful data.

For example, if the sender transmits 1 MB of unique application data twice, it has sent 2 MB of traffic but delivered only 1 MB of unique content.

**Hypothesis:** Redundancy is more attractive when timely delivery is more important than bandwidth efficiency. It is usually less attractive for bulk file transfer.

**What would change my mind:** If the paths are extremely unreliable and redundancy substantially reduces file completion time, it may be useful even for some file-transfer scenarios.

## Q182. For each application, is aggregation, failover or handover the main benefit? Which protocol would you recommend, and under what condition would you change your mind?

| Application | Main benefit | Initial recommendation | Condition that may change it |
|---|---|---|---|
| Large file transfer | Aggregation | MPTCP or a suitable MP-QUIC implementation, depending on deployment requirements and measured performance | Shared bottleneck, receiver limitation, or poor path scheduling |
| Adaptive video | Stable delivery and failover; aggregation when capacity is insufficient | Prefer the approach that gives stable segment completion and low rebuffering | Aggregation wins in measured playback and rebuffering tests |
| VoIP | Low latency and resilience | Lowest-latency path, with carefully evaluated redundancy or backup | Redundancy demonstrably reduces late packets without excessive delay |
| Mobile application | Handover and continuity | A protocol with suitable connection continuity and deployment support | Middlebox, network, or implementation constraints |
| General browsing | Continuity and low latency | Depends on the deployed transport and network support | Measured improvements justify multipath complexity |

**Important:** This is a conditional recommendation, not a universal ranking. MPTCP and MP-QUIC capabilities depend on the implementation, scheduler, network environment and application.

---

# B. Scenario predictions

## Q183. One path has 2% random loss. Which protocol do you expect to do better and why? State the result that would refute you.

A path with 2% random packet loss can cause retransmissions, reduce congestion windows and increase completion time.

The result depends on:
- Whether the other path is less lossy.
- Whether paths have independent bottlenecks.
- The congestion-control algorithm.
- The scheduler's ability to avoid or reduce use of the lossy path.
- Whether the application benefits from redundant transmission.

**Hypothesis:** A multipath implementation that can move traffic away from the lossy path may achieve better useful throughput and completion time than a single-path transfer using that path.

I would not automatically claim that MP-QUIC is better than MPTCP. Both protocol families can use multiple paths, and their actual performance depends on their implementations and scheduling policies.

**What would refute the hypothesis:** If measurements show that multipath does not improve goodput or completion time, or that reordering, retransmissions and congestion-control effects make performance worse.

**Evidence to collect:** Per-path packet loss, retransmissions, goodput, completion time, RTT and path utilisation.

## Q184. One path has 150 ms RTT and one has 20 ms. What does each protocol's default scheduler do, and which application suffers most?

The two paths have significantly different delays.

A scheduler that prefers the lowest-RTT path may send most data over the 20 ms path. A scheduler that distributes traffic across paths may also use the 150 ms path, potentially increasing reordering and completion delays.

**MPTCP:**
- The Linux MPTCP scheduler is implementation-dependent.
- A minimum-RTT-oriented scheduler may prefer the 20 ms path.
- The exact behaviour must be checked for the kernel version and scheduler configuration.

**MP-QUIC:**
- Behaviour depends on the specific multipath draft and implementation.
- Do not assume every MP-QUIC implementation has the same default scheduler.
- Check the implementation's scheduler and configuration before making a definitive claim.

**Which application suffers most?**

- **VoIP:** Sensitive to delay and jitter, so it may suffer significantly.
- **Interactive applications:** Can be affected by increased response time.
- **Video:** May suffer if segment completion becomes unpredictable.
- **Large file transfer:** May tolerate higher delay better, although reordering and congestion can still reduce performance.

**Hypothesis:** Applications with strict latency requirements are more likely to suffer from indiscriminate use of a high-RTT path.

**What would change my mind:** If measured scheduling and buffering prevent late delivery and improve overall application performance, using both paths may still be beneficial.

## Q185. A path suddenly goes down. Which protocol do you expect to recover faster, and what in the trace confirms the reason?

Both MPTCP and MP-QUIC are designed to support multipath operation, but recovery depends on path-failure detection, timers, available alternative paths and implementation behaviour.

**MPTCP:**
- The connection can continue over another available subflow.
- Failure detection and recovery depend on TCP retransmission behaviour, subflow state and MPTCP implementation details.

**MP-QUIC:**
- QUIC has connection-level mechanisms and path-management mechanisms.
- A multipath implementation may continue using another validated path.
- Exact behaviour depends on the draft revision and implementation.

**Which is faster?**

There is no universally correct answer without specifying the implementations and test conditions. I would compare the time from failure to resumed useful application delivery.

**What should the trace show?**
1. The time the path becomes unavailable.
2. Failure detection or timeout events.
3. Retransmissions or path-management events.
4. Traffic moving to the surviving path.
5. The time useful application data resumes.

**Hypothesis:** The implementation with faster failure detection and a ready alternative path will recover faster.

**What would change my mind:** A measured trace showing that the other implementation resumes useful delivery sooner under the same failure conditions.

## Q186. The client sits behind a firewall that blocks UDP. What happens to MP-QUIC and to MPTCP, and what does that say about recommending one?

QUIC runs over UDP. If a firewall blocks the relevant UDP traffic, an MP-QUIC connection may fail to establish or may become unusable.

MPTCP uses TCP subflows. It may work in an environment where TCP is allowed, but MPTCP itself can also encounter middlebox interference or unsupported TCP options.

**Deployment implications:**
- MP-QUIC depends on UDP connectivity and implementation support.
- MPTCP depends on TCP connectivity and support for MPTCP negotiation and operation.
- Neither protocol should be assumed to work through every firewall or middlebox.

**Hypothesis:** In an environment that blocks UDP but permits ordinary TCP, MPTCP is likely to be easier to deploy.

**What would change my mind:** If the network permits QUIC through an approved UDP port or provides a suitable alternative deployment path, MP-QUIC may become viable.

## Q187. A legacy application cannot be modified. Which protocol can you deploy, and what does each option cost?

A legacy application that uses the normal socket API may be able to use MPTCP without application-level changes, provided the operating system and network support it.

**MPTCP:**
- Can provide a multipath transport beneath an existing application.
- The application can continue using a regular byte-stream socket interface.
- Deployment still requires compatible operating-system support and network conditions.

**MP-QUIC:**
- QUIC is commonly implemented in user space and applications generally need to integrate with a QUIC library.
- A legacy TCP application cannot automatically become a QUIC application without an adaptation layer, proxy or other integration.
- Multipath support adds further implementation requirements.

**Recommendation:** For an unmodifiable legacy TCP application, MPTCP is generally the more practical option if the operating system and network support it.

**Cost:** MPTCP deployment may require kernel and network configuration, and middleboxes can interfere. A QUIC-based approach may require application changes or a proxy architecture.

**What would change my mind:** If a suitable transparent proxy or integration layer is available and operationally acceptable, a QUIC-based deployment may become practical.

---

# C. From results to recommendation

## Q188. Beyond performance, which deployment and operational factors belong in a recommendation?

A protocol recommendation must consider more than throughput.

Important factors:

1. **Monitoring:** Can operators inspect connection state, path utilisation, packet loss and failures?
2. **Load balancers:** Do network devices understand or interfere with the protocol's connection behaviour?
3. **Kernel upgrades:** For MPTCP, are the required kernel features and versions available and maintained?
4. **Library maturity:** For MP-QUIC, is the chosen implementation stable, maintained and compatible with the required draft or specification?
5. **Firewall and NAT compatibility:** Can the protocol operate in the target network?
6. **Security:** Are authentication, encryption and path validation handled correctly?
7. **Resource overhead:** What are the CPU, memory, battery and bandwidth costs?
8. **Debugging:** Can failures be diagnosed using logs, packet captures and implementation-specific tools?
9. **Application integration:** Does the application need modification?
10. **Operational complexity:** Can the organisation deploy, update and maintain the protocol reliably?

**Conclusion:** The best protocol is not necessarily the one with the highest laboratory throughput. It must also be deployable, maintainable, observable and suitable for the application's requirements.

## Q189. Which recommendations rest on our own measurements, which on published studies, and which on reasoning alone?

Every conclusion should be labelled by its evidence source.

| Evidence category | Meaning | Example |
|---|---|---|
| Own measurements | Directly measured in our experimental setup | MPTCP achieved a particular goodput under a specified RTT and loss configuration |
| Published studies | Reported by a research paper or technical publication | A study observed a scheduling or fairness advantage under its own test conditions |
| Reasoning | A prediction derived from protocol mechanisms or application requirements | A delayed path may increase reordering and hurt latency-sensitive traffic |

**Rules:**
- Never describe a theoretical prediction as an experimental result.
- A published result does not automatically prove what our implementation will do.
- Include the setup and conditions when reporting a measurement.
- If a claim has not been verified, label it as unverified.

A useful evidence label for the final report is:

- **Measured:** Confirmed in our experiment.
- **Literature-supported:** Reported in a cited study.
- **Reasoned prediction:** Based on protocol behaviour, but not measured.
- **Unverified:** Evidence is insufficient.

## Q190. Write the final recommendation as a table of application, condition and protocol with the strength of evidence. What would you retract if you found your second path was not actually in use?

The final recommendation should be conditional and should not claim that one protocol is universally superior.

| Application | Network condition | Recommendation | Evidence strength |
|---|---|---|---|
| Large file transfer | Independent paths with available capacity | Evaluate MPTCP or MP-QUIC aggregation | Measured only if tested; otherwise reasoned prediction |
| Video streaming | Primary path is stable and sufficient | Prefer stable delivery or backup operation over unnecessary aggregation | Reasoned prediction unless QoE was measured |
| Video streaming | Primary path cannot sustain the required bitrate | Evaluate aggregation and measure segment completion and rebuffering | Requires application-level measurements |
| VoIP | One path has consistently lower delay and jitter | Prefer the low-latency path | Reasoned prediction unless measured |
| VoIP or live media | Loss makes timely delivery unreliable | Evaluate redundancy if extra bandwidth is available | Reasoned prediction unless tested |
| Mobile connectivity | Path failure or network transition is expected | Evaluate multipath failover and continuity | Requires failure or handover measurements |
| Legacy TCP application | TCP works but UDP is blocked | Prefer MPTCP if supported by the system and network | Deployment reasoning |

### What if the second path was not actually in use?

If a trace shows that the second path was never carrying application data, I would retract any claim that:

- Multipath aggregation increased throughput.
- The protocol successfully balanced traffic across paths.
- The second path improved resilience during the test.
- The experiment demonstrated the benefit of using two paths.

I would instead report that the connection may have negotiated or discovered a second path, but actual data utilisation was not demonstrated.

To support a multipath claim, I would verify:
1. Both paths were established and usable.
2. Application data was transmitted over both paths.
3. Per-path byte or packet counters increased.
4. The trace identifies traffic on the separate paths.
5. The application-level result is consistent with the observed path usage.

**Final principle:** A protocol's capability to use multiple paths is not proof that a particular experiment actually used multiple paths.

---

# Final viva revision - Part 10

Be ready to answer these without notes:

1. Why can backup-only be better than aggregation for video?
2. Why does MP-QUIC's stream model offer a different blocking behaviour from MPTCP?
3. When does multipath aggregation help a large file transfer?
4. Why is jitter often more important than throughput for VoIP?
5. Why does redundant scheduling waste capacity for file transfers?
6. Why can a high-RTT path hurt application performance?
7. How would you prove that a failed path was detected and traffic moved to another path?
8. Why might MPTCP be easier to deploy for a legacy application?
9. What deployment factors matter beyond performance?
10. What would you retract if the second path was not actually used?

## The main takeaway

**MPTCP and MP-QUIC should be evaluated against application requirements, not ranked using throughput alone.**

- File transfer often values goodput and completion time.
- Video values stable segment delivery and low rebuffering.
- VoIP values low latency, low jitter and timely packet delivery.
- Mobile applications value continuity and recovery.
- Legacy applications value compatibility and ease of deployment.

A good recommendation must state its conditions, evidence and limitations.

## What to do next

1. Save this as the Part 10 Markdown file.
2. Mark Q177 and Q183 as especially important: both are in your cross-training set.
3. Practise the 10 viva questions at the end without looking at the answers.

After this, we should move to the **final shared sections: Part 11 (Q191-Q205) and Part 21 (Q323)**, then check the shared core Parts 1 and 2.

## Prompt:
11/3/2026, 3:32:00 PM

done lets move ahead

## Response:
11/3/2026, 3:31:08 PM · gpt-6

> **Retrieved exact Part 11 questions**
>
> 
>
> Worked for 5s

Next is **Part 11 - Viva Curveballs (Q191-Q205)**\.

According to the original plan, this is a **shared Tier 1 section led by Pratik**\. You should still prepare all 15 questions because everyone must answer them. The plan specifically says to treat questions about experimental results as predictions unless you have actual measurements.

Save it as\:

`11_Viva_Curveballs_Q191-205/Viva_Curveballs.md`

**document: **

# Part 11 - Viva Curveballs (Q191-Q205)

**Questions:** Q191-Q205  
**Ownership:** Everyone - Pratik leads  
**Tier:** 1  
**Purpose:** Defend design choices, explain limitations, and answer "why this, why not that?"

For questions involving experimental results, distinguish measured findings from predictions. If a run has not been performed, say what you expect and what observation would prove you wrong.

---

## Q191. Why not use MPTCP for everything, since it is mature in the Linux kernel?

MPTCP is a practical multipath solution, particularly when applications use TCP sockets and the operating system supports MPTCP.

However, it is not suitable for every deployment.

**Reasons:**
1. It requires compatible MPTCP support at the endpoints.
2. TCP options used for MPTCP negotiation can be affected by middleboxes.
3. Applications using UDP or requiring QUIC-specific features cannot automatically benefit from MPTCP.
4. Performance depends on congestion control, scheduling and path characteristics.
5. Kernel-level deployment and upgrades require operational support.

**Alternative:** MP-QUIC can provide multipath within a QUIC-based architecture, which may suit applications already using QUIC.

**Cost of choosing MPTCP:** Dependence on kernel support, TCP compatibility and network behaviour.

**Conclusion:** MPTCP is a mature option, not a universal solution. The application and deployment environment determine whether it is appropriate.

## Q192. Why not use MP-QUIC for everything, since it avoids TCP-option middlebox problems? What is still unfinished?

MP-QUIC extends QUIC to support multiple paths. Since QUIC runs over UDP, it avoids relying on TCP options for multipath negotiation.

However, it is not automatically deployable everywhere.

**Limitations:**
1. UDP may be blocked or restricted by firewalls.
2. Multipath QUIC's standardisation and implementation maturity must be checked against the exact draft revision.
3. Implementations may differ in supported features and scheduling behaviour.
4. Deployment requires suitable QUIC implementation support.
5. Multipath introduces additional path-management, congestion-control and scheduling complexity.

**What remains important to verify:**
- Current standardisation status.
- Which scheduling behaviour is specified versus implementation-defined.
- Which implementations support the required draft mechanisms.
- Whether the implementation is stable enough for the intended deployment.

**Alternative:** MPTCP may be more practical for an existing TCP application and a Linux environment with MPTCP support.

**Conclusion:** Avoiding TCP-option problems does not mean MP-QUIC avoids every deployment problem.

## Q193. Why not open several ordinary connections and let the application choose? Give a concrete cost.

An application can open multiple ordinary TCP or QUIC connections and distribute requests across them.

However, this is not equivalent to a single multipath transport connection.

**Concrete costs:**
1. The application must manage multiple connections and their states.
2. Each connection may perform its own setup and congestion-control process.
3. Data ordering and reassembly across connections become application responsibilities.
4. Connection failures and retries must be handled by the application.
5. Multiple independent connections may compete unfairly with other traffic.
6. Application changes may be required.

**Alternative:** MPTCP provides a single reliable byte stream over multiple TCP subflows. MP-QUIC provides multiple QUIC streams within a connection and multipath functionality in supporting implementations.

**Conclusion:** Multiple ordinary connections can be useful, but they shift connection coordination, scheduling and data assembly to the application.

## Q194. Why not use ECMP or link bonding instead of either protocol?

ECMP and link bonding provide multipath-related functionality, but at different network layers and with different assumptions.

**ECMP - Equal-Cost Multi-Path:**
- Network routers can distribute flows across equal-cost routes.
- It commonly uses flow-based hashing.
- It does not necessarily split one transport flow's packets across paths.
- A single flow may remain on one route.

**Link bonding:**
- Combines multiple network interfaces into a logical interface.
- Can provide redundancy or increased capacity, depending on the bonding mode.
- Usually requires support and configuration at the network or link layer.

**MPTCP and MP-QUIC:**
- Provide multipath capabilities at the transport layer.
- Can coordinate multiple paths as part of a transport connection.
- Can react to transport-level delivery and congestion information.

**Why not ECMP or bonding?**

They may not provide the endpoint-level transport behaviour required by the application, and they may require network infrastructure or configuration outside the application's control.

**Conclusion:** ECMP and bonding are valid alternatives in suitable environments. They solve related but different problems.

## Q195. Why did you choose Mininet, NetEm, iperf3 and Wireshark? What would change on a real testbed?

These tools serve different purposes in a controlled networking experiment.

| Tool | Purpose |
|---|---|
| Mininet | Creates virtual hosts, switches and network topologies |
| NetEm | Emulates network impairments such as delay, loss, duplication and rate-related conditions |
| iperf3 | Measures throughput between endpoints |
| Wireshark | Captures and inspects packets and protocol behaviour |

**Why use them?**

They allow repeatable tests under controlled conditions. For example, we can configure two paths with different RTTs and loss rates, then compare transfer performance.

**Limitations of an emulated testbed:**
- It does not fully reproduce real Wi-Fi or cellular behaviour.
- CPU scheduling and virtualisation can influence measurements.
- Radio interference, mobility and real handovers are not naturally represented.
- Real devices may have different power and processing constraints.

**What changes on a real testbed?**

We would need to account for:
- Real Wi-Fi and cellular variation.
- Mobility and handover.
- Radio interference.
- Device CPU and battery usage.
- Real network middleboxes and carrier policies.

**Conclusion:** Emulation is useful for controlled comparisons, while real testbeds are needed to evaluate practical deployment behaviour.

## Q196. Your MP-QUIC results come from a different implementation than the one in the project brief. Is the comparison still valid, and what do you tell Sir?

The comparison may still be useful, but it must be qualified.

Different implementations can have different:
- Scheduling algorithms.
- Congestion-control mechanisms.
- Path-management behaviour.
- Recovery mechanisms.
- Buffering and implementation optimisations.
- Support for different draft revisions.

Therefore, a result from one MP-QUIC implementation cannot automatically be generalised to every MP-QUIC design.

**What I would tell Sir:**

"We evaluated the available implementation rather than claiming to evaluate every possible MP-QUIC implementation. The comparison is valid for the tested configurations, but implementation differences limit how broadly we can generalise the result."

**How to improve validity:**
1. Identify the exact implementation and version.
2. Record its draft or protocol revision.
3. Document scheduler and congestion-control settings.
4. Keep network conditions and workloads consistent.
5. Clearly state the implementation difference as a limitation.

**Conclusion:** The result is implementation-specific evidence, not proof of universal protocol superiority.

## Q197. Your MPTCP and MP-QUIC runs use different congestion control. Does that invalidate the comparison, and how do you handle it?

Different congestion-control algorithms can produce different throughput, fairness and loss-recovery behaviour.

For example, one algorithm may increase its sending rate more aggressively, while another may be more conservative.

This means the observed performance difference could come from congestion control rather than the multipath protocol design itself.

**Does it invalidate the comparison?**

Not completely. It remains a comparison of the tested implementations and configurations. However, it does not isolate the effect of the protocol design.

**How to handle it:**
1. Record the congestion-control algorithm used by each implementation.
2. Explain that the algorithms differ.
3. Avoid attributing every performance difference to multipath design.
4. If possible, compare configurations with more closely matched congestion-control behaviour.
5. Report both the original comparison and any controlled follow-up separately.

**Conclusion:** Different congestion-control algorithms are a confounding variable. The comparison remains informative but has limited causal strength.

## Q198. MP-QUIC shows higher throughput. Give three explanations that have nothing to do with protocol design and the test that separates each.

A higher throughput result does not automatically prove that MP-QUIC has a better protocol design.

Three alternative explanations are:

**1. Different congestion-control algorithms**

One implementation may use a more aggressive congestion-control algorithm.

- **Test:** Record the algorithms and, where possible, repeat using comparable congestion-control settings.
- **Interpretation:** If the difference disappears, congestion control may explain much of the original result.

**2. Different implementation efficiency**

One implementation may have better CPU efficiency, buffering, packet processing or memory management.

- **Test:** Measure CPU usage, memory use and packet-processing performance while keeping the workload and network conditions consistent.
- **Interpretation:** If the faster implementation also uses substantially more CPU or has more efficient processing, implementation overhead may explain the difference.

**3. Different configuration or path utilisation**

One implementation may use both paths effectively while the other may send most traffic over only one path. Buffer sizes or scheduler settings may also differ.

- **Test:** Inspect per-path byte counters, packet captures, scheduler configuration and buffer settings.
- **Interpretation:** If one implementation did not actually use both paths, the result cannot be attributed to successful multipath aggregation.

**Conclusion:** Before attributing a throughput difference to protocol design, check congestion control, implementation efficiency and actual path utilisation.

## Q199. You have a result you cannot explain. What do you do, and what do you write in the report?

I would not immediately accept or discard the result.

**Steps:**
1. Repeat the experiment.
2. Check whether the network conditions were configured correctly.
3. Verify that both paths were established and carrying data.
4. Inspect packet captures and protocol logs.
5. Check congestion-control and scheduler settings.
6. Compare application-level measurements with network-level counters.
7. Look for measurement errors, background traffic and resource bottlenecks.
8. Record any remaining uncertainty.

**What I would write:**

"The observed result was not fully explained by the available measurements. We repeated the test and inspected the configuration and traces. The possible explanations are listed, but the cause remains unverified."

**Conclusion:** An unexplained result should be reported honestly, not forced into a convenient explanation.

## Q200. What is the most important limitation of your study, and how does it change what you can conclude?

The most important limitation must be selected based on the actual experiment performed.

Possible limitations include:

- Using emulated rather than real mobile networks.
- Comparing different implementations.
- Using different congestion-control algorithms.
- Testing only a small number of network conditions.
- Using a limited set of workloads.
- Not testing enough repetitions.
- Not verifying that both paths carried application data.

**Why it matters:**

A limited experiment supports conclusions only within its tested conditions.

For example, an emulated test showing that one implementation achieves higher throughput does not prove it will perform better on real Wi-Fi and 5G networks.

**What I would say:**

"Our results establish behaviour under the tested configurations. They do not establish universal superiority across all networks, implementations and applications."

**Conclusion:** State the limitation that most directly affects the strength and scope of your findings.

## Q201. What changes if the two paths share a bottleneck, and what would you add to the experiment to test that?

If two paths share a bottleneck, they may compete for the same constrained resource.

For example, Wi-Fi and cellular traffic may eventually pass through a shared upstream network or constrained server connection.

**What changes?**
- Aggregating traffic may not increase total available capacity.
- Both paths may contribute to congestion at the shared bottleneck.
- Additional traffic can increase queueing delay.
- Congestion control may react to the shared resource in different ways.
- Multipath may provide little throughput benefit or even reduce useful performance.

**What would I add?**

Create two test conditions:

1. **Independent bottlenecks:** Each path has a separate constrained link.
2. **Shared bottleneck:** Both paths pass through the same constrained link.

Then compare:
- Aggregate goodput.
- Completion time.
- RTT and queueing delay.
- Packet loss and retransmissions.
- Per-path utilisation.

**Hypothesis:** Aggregation should provide a greater benefit when paths have independent bottlenecks.

**What would refute it:** If the shared-bottleneck configuration provides the same improvement under otherwise comparable conditions, the hypothesis would need revision.

## Q202. What changes on a real phone with 5G and Wi-Fi? Which findings would you expect to survive?

A real phone introduces factors that are difficult to represent fully in a controlled emulation.

**Additional factors:**
1. Radio interference and changing signal strength.
2. Variable Wi-Fi and cellular RTT.
3. Mobility and handovers.
4. Battery consumption.
5. CPU and memory constraints.
6. Carrier policies and network middleboxes.
7. Different path availability over time.

**Which findings may survive?**

General transport principles are likely to remain relevant:
- Different path delays can cause reordering.
- A shared bottleneck can limit aggregation benefits.
- Redundant transmission consumes additional capacity.
- Applications have different latency and throughput requirements.

However, exact throughput, recovery time and scheduler rankings may change.

**Conclusion:** Mechanistic findings may generalise, but numerical performance results must be validated on real devices and networks.

## Q203. Is MP-QUIC better than MPTCP? Why is that the wrong question, and what answerable questions replace it?

Asking whether one protocol is universally better is too broad.

The protocols have different architectures, deployment requirements and application integration models.

A better comparison asks specific questions:

1. Which performs better for large file transfers under independent path conditions?
2. Which provides more stable video segment delivery?
3. Which recovers faster after a path failure?
4. Which works in a network where UDP is blocked?
5. Which is easier to deploy for an existing TCP application?
6. Which provides better performance under a shared bottleneck?
7. What are the CPU, memory and battery costs?
8. How do their scheduling and congestion-control choices affect fairness?

**Conclusion:** The correct question is not "Which protocol is better?" but "Which protocol is better for this application, implementation and network condition?"

## Q204. In which of your measurements was the second path harmful? What does that say about when not to enable multipath?

This question must be answered using actual measurements. If the experiment has not demonstrated harmful second-path behaviour, do not invent an example.

**Possible conditions where a second path can be harmful:**
- It has much higher RTT than the primary path.
- It has high packet loss.
- It shares a bottleneck with the primary path.
- It contributes little additional capacity.
- Its use creates significant reordering.
- Scheduling and recovery overhead exceed the benefit.

**What should be measured?**
- Goodput with one path versus two.
- Completion time.
- RTT and delay variation.
- Retransmissions.
- Per-path traffic.
- CPU and processing overhead.

**Prediction:** If the second path contributes little useful capacity while increasing delay or reordering, enabling it may reduce application performance.

**Conclusion:** Multipath should be enabled when its measured benefit exceeds its additional cost. More paths do not automatically mean better performance.

## Q205. Explain both protocols to a first-year student in five minutes. What do you draw, what is the one sentence on each, and what do you leave out?

I would begin with the problem: a device may have Wi-Fi and cellular connectivity, but an ordinary transport connection may not automatically use both paths.

### MPTCP

**One sentence:** MPTCP allows one TCP connection to use multiple TCP subflows over different network paths while presenting a single reliable byte stream to the application.

Draw:

- One application.
- One MPTCP connection.
- Two TCP subflows.
- Two network paths.
- A receiver combining the data into one ordered byte stream.

Mention:
- MP_CAPABLE establishes MPTCP capability.
- MP_JOIN adds another subflow.
- DSS maps subflow sequence numbers to connection-level data sequence numbers.

### MP-QUIC

**One sentence:** MP-QUIC extends QUIC so that a QUIC connection can use multiple network paths.

Draw:

- One application.
- One QUIC connection.
- Multiple QUIC streams.
- Multiple network paths.
- A receiver handling the streams.

Mention:
- QUIC uses UDP.
- QUIC streams provide independent ordered byte streams.
- Multipath support requires path-management and scheduling mechanisms.
- The exact mechanisms depend on the draft revision and implementation.

### Main comparison

| MPTCP | MP-QUIC |
|---|---|
| Built on TCP subflows | Built on QUIC over UDP |
| Presents one reliable byte stream | Supports multiple independent streams |
| Uses DSN and DSS mappings | Uses QUIC stream IDs, offsets and packet mechanisms |
| Integrated with supported operating systems' TCP stack | Commonly implemented through QUIC libraries |
| Can face TCP-option middlebox issues | Can face UDP restrictions |

**What I would leave out in a five-minute explanation:**
- Detailed congestion-control equations.
- Every packet-header field.
- All draft-specific path-management details.
- Implementation-specific performance numbers.

The goal is to explain the architecture and the reason multipath exists before discussing internal mechanisms.

---

# Final revision checklist

Before the viva, ensure you can answer:

- Why not MPTCP for everything?
- Why not MP-QUIC for everything?
- Why not multiple ordinary connections?
- Why not ECMP or link bonding?
- What does each experimental tool contribute?
- How do implementation and congestion-control differences affect fairness?
- How do you investigate an unexplained result?
- Why does a shared bottleneck matter?
- Which conclusions can be generalised to real networks?
- Why is "Which protocol is better?" the wrong question?
- How do you verify that the second path actually carried data?

## Four-beat answer structure

For every curveball, use this order:

1. **What:** State the mechanism or issue.
2. **Why:** Explain why it matters.
3. **Alternative and cost:** Explain what else could be used and its trade-off.
4. **Evidence:** State what you measured, what the literature supports, or what remains unverified.

**Final takeaway:** A strong technical answer does not defend a protocol blindly. It identifies the conditions where a design works, the cost it introduces, and the evidence needed to justify the conclusion.

**Next\:** Part 12 - Transport Foundations, Deeper (Q206-Q221). It is shared and Pratik leads, but it is Tier 2 for everyone. We'll prepare it next.

## Prompt:
11/3/2026, 3:43:48 PM

im sharing again, the complete plan, analyze deeply and give in what are all my final delivearbles, all parts, diagams, etc etc given everything, then what weve completed and what i have to still do

[Attachment: mptcp-mpquic-understanding-plan(2).md]

## Response:
11/3/2026, 3:43:03 PM · gpt-6

> **Inspecting document sections and diagrams**
>
>
> **Organizing deliverables**
>
> I’m mapping every required output and reconciling the latest plan with earlier notes. The current plan parks hands-on work, keeps Part 8 theory-only, and prioritizes unfinished shared sections plus Swamini’s assigned parts.
>
> **Organized deliverables**
>
> 
>
> **Inspected document diagrams and retrieved lines 580 through 833**
>
> 
>
> Worked for 1m

I’ve gone through the **complete 833-line plan you uploaded**, including the ownership table, all 21 parts, the 323-question bank, the required diagrams, the reading list, progress tracker, and the parked hands-on tasks.

The most important distinction is this\:

**Your individual responsibility is not to complete all 323 questions to the same depth.** You own four main parts, lead one shared part, and must be prepared for the common Tier 1 material and your cross-training questions.

Also, this uploaded plan explicitly says that experiments and implementation are **parked**, not mandatory for the current understanding phase. That supersedes any earlier interpretation that you must complete a full MPTCP-versus-MP-QUIC benchmark before the deadline.

# 1\. Your exact responsibility

# Swamini - individual ownership

**Part 9 - Existing research** (Tier 2)

Q159-176 · You own and teach this part.

---

**Part 10 - Applications and recommendations** (Tier 1)

Q177-190 · Shared by everyone; you lead it.

---

**Part 16 - Congestion control, fairness and scheduling** (Tier 1)

Q265-279 · Your most important individual theory block.

---

**Part 17 - Applications and QoE, deeper** (Tier 2)

Q280-290 · You own and teach this part.

---

**Part 18 - History and literature, deeper** (Tier 3)

Q291-297 · You own this part, but it is lower priority.

Your assigned teach-back question is\:

> Why could adding a second path decrease useful application throughput?

You should be able to explain this without notes, using an example involving different path RTTs, packet reordering, receive-buffer pressure and head-of-line blocking.

## 2\. Shared parts you must complete

These are explicitly assigned to everyone in Section 6 of the plan.

| Part | Questions | Priority | Status from our work |
|--------|--------|--------|--------|
| 1\. Why multipath exists | Q1-14 | Tier 1 | Still to verify |
| 2\. TCP and transport fundamentals | Q15-28 | Tier 1 | Still to verify |
| 10\. Applications and recommendations | Q177-190 | Tier 1 | **Completed** |
| 11\. Viva curveballs | Q191-205 | Tier 1 | **Completed** |
| 12\. Transport foundations, deeper | Q206-221 | Tier 2 | Still to do |
| 19\. Trace it end to end | Q298-309 | Tier 1 | **Completed** |
| 21\. A-Z term drill | Q323 | Tier 1 | Still to do |

You do not own Part 20. It belongs to Pratik.

**Important\:** Parts 1, 2, 10, 11, 12, 19 and 21 are common responsibilities even though some have a designated lead. You should not skip them just because they are not your individual research block.

# 3\. What you must know from the other members' parts

You do not have to study every question in Krina's, Kaushal's and Pratik's sections to the same depth as they do. However, the plan gives you a specific cross-training set.

These are your ten cross-training questions\:

| Owner | Questions you must prepare |
|--------|--------|
| Krina - MPTCP | Q29, Q30, Q33, Q35, Q40, Q42, Q46, Q52, Q72, Q74 |
| Kaushal - QUIC | Q75, Q79, Q81, Q87, Q90, Q93, Q94, Q97, Q108, Q110 |
| Pratik - methods and integration | Q135, Q139, Q140, Q146, Q153, Q154, Q157, Q158, Q298, Q299 |

These are particularly important because the plan says the other three people should be able to answer the ten cross-training questions from each owner's area.

You should also understand the comparison in Part 7, especially the whiteboard comparison in Q133. The plan specifically expects everyone to be able to draw that table from memory.

# 4\. All diagrams and visual deliverables

This is important: the plan does not ask you to submit only written question answers. It explicitly expects drawings, technical guides and evidence-based diagrams.

Here is the complete breakdown of the visuals relevant to you.

## A. Diagrams explicitly assigned to your block

[![PPT - Balia ( Ba lanced li nked a daptation) A new MPTCP congestion control algorithm PowerPoint Presentation - ID:2472509](https://images.openai.com/static-rsc-4/_GHRPrVWkHp3Y9Tv_gAuoYIJPeoTV2Dts9W7Gztef_u9nCZ1GkmmXDfrBSlUmRiGt9lTrzN0axmkA4CQaxjGkDGQS7aFcKeMDHjHdHgInUPk4L80K73cDyQB3J5sfZCX46uivDrk-PL779tMn2ZQcdfRy5GCn59RsPraKgPbjeUbCN60QGlsvjxGy42cllgE?purpose=fullsize)](https://www.slideserve.com/sugar/balia-ba-lanced-li-nked-a-daptation-a-new-mptcp-congestion-control-algorithm)

**1\. Throughput against RTT ratio**

Show how aggregation can behave as the RTT difference between paths increases. This is an explanatory intuition diagram, **not experimental data**\.

Part 16 · Section 7 reading/drawing requirements

---

[![A Brief Review of Multipath TCP for Vehicular Networks](https://images.openai.com/static-rsc-4/Md1ur5F-8w5bOW38U0Czlk-elSM_VV661BUJW5N78jCYYDjwnLpHZK-ZEvR1J0CJyzWG7WzSXdUqZPpDqSa5SFybwf3GEVtHOBotpgMS1V351QIXUsykFBQRjPCAufTpleHVaio9_XHK8tgdDM__SkGPPgv9pIEuofIseaOqF2VNwrkw9A9rvpPCykxyTHze?purpose=fullsize)](https://www.mdpi.com/1424-8220/21/8/2793)

**2\. The “second path hurts” timeline**

Show data sent on a fast and a slow path, out-of-order arrival, waiting for missing earlier bytes, receive-buffer occupation and the resulting reduction in useful application delivery.

Part 16 · Supports your teach-back question

---

[![Literature Matrix Template - Printable Word Searches](https://images.openai.com/static-rsc-4/pWPvKEV9NEwq29Z7KLmZzIPI6oYSrwBo9dOPXxNiG4eBhzD5CBlkXoclE8XSIxHdhvh_6x7jRxMLp4Bo6DvwKMitUm1LCK8QGjAk8wvNb2WGDERO43nNTsAPWvqPQj5QpD6_CczR8ZYHojV7EOoRe8cHYGPI4C1c-ElbK90jjKfl1ca0ZAtsRbIiUAkl9r6-?purpose=fullsize)](https://davida.davivienda.com/viewer/literature-matrix-template.html)

**3\. Literature matrix**

Compare the papers using the fields required in Q160: implementation/version, emulator, path parameters, workload, metrics, congestion control and scheduler.

Part 9 · Required research deliverable

## B. Other diagrams and tables you need as part of the team

| Visual | What it must show | Question/part |
|--------|--------|--------|
| MPTCP architecture | Application, MPTCP connection, subflows, IP and both sequence spaces | Q40, Q42 |
| MP-QUIC architecture | Paths, path IDs, connection IDs and packet-number spaces | Q94-98 |
| MPTCP vs MP-QUIC comparison | Setup, adding/removing paths, ordering, loss detection, ACKs and congestion control | Q133 |
| End-to-end MPTCP stack | Application `write()` to receiver `read()`, buffers, sequence numbers, ACKs and timers | Q298 |
| End-to-end MP-QUIC stack | Stream write to receiver read, frames, packet numbers, ACKs and recovery | Q299 |
| Side-by-side protocol stacks | Where reliability, ordering, congestion control, security, path identification and scheduling live | Q300 |
| Prediction table | Both protocols under symmetric/asymmetric paths, loss, failure, shared bottleneck, NAT and blocked UDP | Q304 |
| Evidence chain | Connect a technical claim to the RFC, paper, capture or log supporting it | Section 7, Pratik's drawing requirement |
| Final recommendation table | Application, conditions, recommended protocol and evidence strength | Q190 |

For the MPTCP and MP-QUIC architecture drawings, the plan assigns the main detailed versions to Krina and Kaushal. You should still understand them well enough to follow the comparison and the end-to-end trace.

## C. Other visual outputs that are tables rather than drawings

You should also have\:

- The application recommendation matrix from Q190.
- The literature comparison matrix from Q160.
- A comparison of the published findings and their experimental conditions for Q167-169.
- The history timeline from Q291.
- The two-column protocol comparison from Q133.

These are not optional decorations. They help demonstrate that you can connect claims to mechanisms and evidence.

# 5\. Written deliverables you should have

The plan's Section 5 and Section 8 make the expected output clearer than simply saying “answer the questions.”

| Deliverable | What it contains | Your responsibility |
|--------|--------|--------|
| Written answers | Answers in your own words, using what / why / cost / how to check | All your owned questions and shared questions |
| One-page technical guide | Condensed explanation of your assigned topic | Your individual block |
| Architecture/technical diagrams | Mechanisms explained visually | Your three diagrams, plus relevant team diagrams |
| Literature matrix | Structured comparison of research papers | Part 9 |
| Gap list | Questions you cannot yet answer, unclear mechanisms and unsupported claims | Individual and shared |
| Evidence references | RFC/draft sections, papers or explicit “not verified” labels | Every substantive technical claim |
| Recommendation matrix | Application, conditions, protocol and evidence strength | Part 10 |
| A-Z glossary | Definitions of all listed terms, one or two sentences each | Part 21 |
| Team additions | New questions starting at Q401, with owner and tier | Only if you discover gaps not already covered |

**The four-beat answer format applies throughout\:**

1. What is the mechanism?
2. Why does it exist?
3. What does it cost or what alternative does it sacrifice?
4. How would you verify it?

The plan also insists on distinguishing **what the specification says** from **what a particular implementation does**\. When a claim cannot be checked, say “not verified” rather than presenting it as a fact.

# 6\. What we have completed together

Based on the work we've already completed in our conversations, this is the status I can confirm\:

## Completed sections

These sections have already been drafted as complete, paste-ready Markdown content.

A couple of important qualifications\:

- **Part 9 (Q159-176)\:** I cannot confidently mark this complete from the work history I can verify here. We have discussed your literature research, and there is a research block covering Q159-176, but I would like to check the actual written section before treating it as finished.
- **Diagrams\:** Completing the written sections does not automatically mean the associated diagrams have been drawn, saved and checked. We should verify those separately.

# 7\. What you still need to do

Here is the practical remaining-work checklist, in priority order.

**Remaining-work tracker** (/ checked)

This is a checklist for tracking your remaining work in this conversation; it does not automatically update your files or the team's original progress tracker.

# 8\. What about experiments and hands-on work?

The uploaded plan is explicit in Section 1 and Section 802 onward\:

(Parked - not part of the current required study phase)

These are to be attempted only after the learning plan is complete and Tier 1 is solid\:

1. Check whether the chosen QUIC implementation can open a second path.
2. Capture an MPTCP handshake in Wireshark and annotate the options.
3. Set up two-path MPTCP in Mininet and prove the second subflow is used.
4. Run MP-QUIC or document why reproduction was not feasible.
5. Run a small benchmark with repetitions and preserve versions, commands and logs.

If the selected QUIC build cannot support multipath, the plan explicitly accepts documenting why reproduction was not feasible.

**So do not spend your remaining study time trying to build a full multipath implementation before completing the required theory.** Part 8 is currently theory-only.

# 9\. What your final project preparation should look like

By the time you are ready for the viva, your personal folder should contain something like this\:

```text
Swamini_Project_MPTCP_MPQUIC/
│
├── 01_Part_9_Existing_Research/
│   ├── Existing_Research_Q159-176.md
│   └── Literature_Matrix.md
│
├── 02_Part_10_Applications/
│   └── Applications_and_Recommendations.md
│
├── 03_Part_16_Congestion_Fairness/
│   ├── Congestion_Fairness_Scheduling.md
│   ├── Throughput_vs_RTT.png
│   └── Second_Path_Hurts_Timeline.png
│
├── 04_Part_17_Applications_QoE/
│   └── Applications_and_QoE.md
│
├── 05_Part_18_History_Literature/
│   └── History_and_Literature_Deeper.md
│
├── 06_Part_19_End_to_End_Trace/
│   └── End_to_End_Trace_MPTCP_MPQUIC.md
│
├── 07_Shared_Parts/
│   ├── Part_1_Why_Multipath.md
│   ├── Part_2_Transport_Fundamentals.md
│   ├── Part_11_Viva_Curveballs.md
│   ├── Part_12_Transport_Foundations.md
│   └── Part_21_AZ_Term_Drill.md
│
├── 08_Comparison_and_Diagrams/
│   ├── MPTCP_vs_MPQUIC_Comparison.png
│   ├── MPTCP_Architecture.png
│   ├── MPQUIC_Architecture.png
│   └── Side_by_Side_Stack.png
│
├── 09_Revision/
│   ├── Cross_Training_Questions.md
│   ├── Gap_List.md
│   ├── One_Page_Technical_Guide.md
│   └── Mock_Viva_Notes.md
│
└── README.md
```

This is a suggested organisation of the deliverables, not a folder structure explicitly mandated by the plan.

# 10\. My recommended order from here

The plan's learning order and the work we have already completed suggest this sequence\:

1. **Verify Part 9** and its literature matrix. It is your individual research responsibility.
2. Complete **Part 1 and Part 2**, because they are shared Tier 1 foundations.
3. Complete **Part 12**, which builds on Part 2 and is currently unfinished.
4. Complete **Part 21**, the A-Z term drill.
5. Check the three diagrams for Parts 9 and 16, and the shared comparison diagrams.
6. Prepare your cross-training questions and practise the Part 7 comparison.
7. Finish with mock viva practice, using the four-beat answer method.

The plan's original deadline is 4 November 2026, with 3-4 November reserved for buffer and light revision. Since the current date is 3 November, prioritise unfinished Tier 1 material and your own Tier 1 block over polishing Tier 3 material.

**One important thing before we continue\:** I would not mark your project completely finished just because six sections are drafted. The actual completion criteria include being able to explain the mechanisms, draw the diagrams, support claims with evidence and answer questions aloud.

My suggested next step is to verify **Part 9 (Q159-176)** against the literature matrix and written answers, then continue with the unfinished shared sections.

## Prompt:
11/3/2026, 4:25:00 PM

now part 12 transport foundations, Q206-221 and A-Z drill part 21 is remaining to do, then separate file md for the 30 cross training questions from each 3 members, then the diagrams, literature matrix is done, then one page technical guide, evidence references, these are the remainig works, lets complete this one by one correctly

## Response:
11/3/2026, 4:24:07 PM · gpt-6

> **Retrieved exact source questions Q206–221 from files**
>
> 
>
> Worked for 34s

We'll complete these in order and keep each deliverable as a separate, ready-to-save Markdown file. For every question, I'll preserve the plan's focus and use the same four-part structure: **what it is, why it exists, its cost or caveat, and how to verify it**\. I'll also flag details that need a primary-source check rather than presenting an uncertain rule as fact.

## Step 1 - Part 12: Transport Foundations, Deeper (Q206-Q221)

This is a shared Tier 2 section led by Pratik, but it is important for everyone because it connects the TCP, MPTCP, UDP and QUIC mechanisms. The exact question set in your plan contains 16 questions, from the TCP header and state machine through to the meaning of *connection*, *flow*, *subflow* and *path*\.

Save the following as\:

`12_Transport_Foundations_Q206-221/Transport_Foundations_Deeper.md`

**document: **

# Part 12 - Transport Foundations, Deeper (Q206-Q221)

**Project:** MPTCP vs MP-QUIC  
**Scope:** Shared questions - everyone  
**Lead:** Pratik  
**Tier:** 2  
**Answer structure:** What / Why / Cost or caveat / How to check

---

## Q206. Draw the TCP header from memory. Which fields carry reliability, flow control and options? The option space is at most 40 bytes: why does that limit matter for MPTCP's design?

### What
A TCP header has a minimum size of 20 bytes and a maximum size of 60 bytes. Its main fields are:

| Field | Size | Purpose |
|---|---:|---|
| Source port | 16 bits | Identifies sending application endpoint |
| Destination port | 16 bits | Identifies receiving application endpoint |
| Sequence number | 32 bits | Identifies the first data byte in the segment |
| Acknowledgment number | 32 bits | Identifies the next byte expected from the peer |
| Data offset | 4 bits | Gives the TCP header length |
| Reserved | 3 bits | Reserved for future use |
| Flags | 9 bits | Includes control flags such as SYN, ACK, FIN, RST, PSH, URG, ECE and CWR |
| Window size | 16 bits | Advertises the receiver's available window |
| Checksum | 16 bits | Detects corruption in the TCP segment and pseudo-header |
| Urgent pointer | 16 bits | Supports the TCP urgent-data mechanism |
| Options + padding | Variable | Supports MSS, window scaling, SACK, timestamps and other extensions |

The sequence and acknowledgment numbers provide byte-stream reliability. The advertised window provides receiver flow control. The checksum detects corruption.

### Why
TCP options allow the protocol to negotiate or communicate capabilities beyond the original fixed header. MPTCP uses TCP options to negotiate and manage multipath operation.

For example:
- `MP_CAPABLE` negotiates MPTCP during connection establishment.
- `MP_JOIN` allows another subflow to join an existing MPTCP connection.
- `DSS` carries Data Sequence Number mappings and Data ACK information.

### Cost or caveat
The TCP option area is limited to 40 bytes because the TCP header cannot exceed 60 bytes. Multiple options must share this space.

This creates a practical constraint: timestamps, SACK information and MPTCP options may compete for space. Options may need to be omitted, shortened or sent in different packets depending on what fits.

Middleboxes may also strip or modify TCP options, which is one reason MPTCP needs compatibility mechanisms.

### How to check
- Draw the fixed 20-byte header and the variable option area separately.
- Check the TCP header format in RFC 9293.
- Check the MPTCP option formats in RFC 8684.
- In Wireshark, inspect SYN, SYN/ACK and data packets to see which options are present.

---

## Q207. Walk through the TCP state machine for setup and teardown (SYN_SENT, ESTABLISHED, FIN_WAIT, CLOSE_WAIT, TIME_WAIT). What does TIME_WAIT protect against, and what does RST do? Why does every MPTCP subflow go through this on its own?

### What
TCP uses a state machine to manage connection establishment, data transfer and termination.

**Connection establishment:**

1. The active endpoint sends SYN and enters `SYN_SENT`.
2. The passive endpoint receives SYN, sends SYN/ACK and enters `SYN_RECEIVED`.
3. The active endpoint sends ACK.
4. Both endpoints enter `ESTABLISHED`.

**Connection termination:**

- The endpoint that actively closes sends FIN and enters `FIN_WAIT_1`.
- After its FIN is acknowledged, it enters `FIN_WAIT_2`.
- The peer that receives FIN enters `CLOSE_WAIT` and informs its application that the peer has closed its sending direction.
- When that application closes its side, the peer sends FIN and enters `LAST_ACK`.
- The active closer acknowledges the peer's FIN and generally enters `TIME_WAIT`.

TCP supports half-close: one direction can be closed while the other direction remains open.

### Why
`TIME_WAIT` protects against delayed duplicate segments from an old connection being mistaken for traffic belonging to a new connection with the same endpoint pair.

It also allows the endpoint that actively closes to retransmit the final ACK if the peer retransmits its FIN.

`RST` (reset) aborts a TCP connection rather than performing the orderly FIN-based shutdown. It is used when a connection is invalid or must be terminated immediately.

### Cost or caveat
`TIME_WAIT` temporarily retains connection state and can consume resources when many short-lived connections are created.

MPTCP has one logical connection but uses multiple TCP subflows. Each subflow is a TCP connection and therefore has its own TCP state machine, sequence numbers and TCP-level termination.

Closing one subflow does not necessarily mean that the entire MPTCP connection has ended. MPTCP has connection-level mechanisms for closing the complete data-level connection.

### How to check
- Draw the TCP three-way handshake and four-way close.
- Inspect `SYN_SENT`, `ESTABLISHED`, `FIN_WAIT_1`, `FIN_WAIT_2`, `CLOSE_WAIT`, `LAST_ACK` and `TIME_WAIT` using `ss -tan`.
- Compare a normal TCP close with an MPTCP connection containing multiple subflows.
- Primary source: RFC 9293.

---

## Q208. What do the MSS, window-scale, SACK-permitted and timestamp options do, and why are they negotiated only in the SYN? Which would you expect to be per subflow and which per connection in a multipath design, and why?

### What
These TCP options provide capabilities that endpoints negotiate during connection establishment.

| Option | Purpose |
|---|---|
| MSS | Announces the maximum TCP data segment size the sender is willing to receive |
| Window Scale | Allows the 16-bit TCP window field to represent larger receive windows |
| SACK-Permitted | Indicates that the endpoint supports Selective Acknowledgment |
| Timestamps | Carries timestamp values used for RTT measurement and PAWS protection |

### Why
These options are negotiated in SYN packets because both endpoints need to agree on the capabilities and parameters that will apply to that TCP connection before normal data transfer begins.

In MPTCP, each subflow is a separate TCP connection. Therefore, TCP-level parameters are negotiated and maintained per subflow.

Examples:
- MSS depends on the subflow's path and MTU.
- TCP window scaling is negotiated for that subflow.
- SACK capability is negotiated for that subflow.
- TCP timestamps and their state are maintained at the subflow level.

MPTCP additionally maintains connection-level data sequence information through DSS. That information is distinct from the TCP sequence space of an individual subflow.

### Cost or caveat
Do not confuse a TCP option being negotiated in a SYN with it necessarily being a connection-wide MPTCP property.

A multipath connection may have subflows with different MTUs, RTTs and TCP-level conditions. Treating all their TCP parameters as identical would be incorrect.

The exact interaction of individual TCP options with MPTCP must be checked against RFC 8684 rather than inferred from ordinary TCP alone.

### How to check
- Compare the SYN packets of two MPTCP subflows.
- Inspect MSS, Window Scale, SACK-Permitted and Timestamps in Wireshark.
- Check RFC 9293 for TCP options and RFC 8684 for MPTCP-specific behaviour.

---

## Q209. How does a SYN flood work, and how do SYN cookies stop it? Why does it matter that a server can stay stateless early in a handshake, for MPTCP's third ACK and for QUIC's Retry packet?

### What
A SYN flood is a denial-of-service attack in which an attacker sends many TCP SYN requests but does not complete the three-way handshake.

The server normally allocates state for a half-open connection after receiving a SYN and sending SYN/ACK. A large number of incomplete handshakes can exhaust this state.

**SYN cookies** reduce this risk by encoding information about the pending connection into the server's SYN/ACK sequence number. The server can validate the client's final ACK and reconstruct the required state without retaining ordinary half-open connection state for every request.

### Why
The principle is to delay expensive state allocation until the peer demonstrates that it can receive and return a valid response.

QUIC has a related mechanism called **Retry**:
- A server can send a Retry packet containing a token.
- The client sends another Initial packet with that token.
- The server validates the token before committing more resources.

This helps address source-address spoofing and resource-exhaustion risks.

MPTCP uses the TCP three-way handshake and its own capability negotiation. Its `MP_CAPABLE` exchange involves information in the handshake, including a final ACK. The server must handle this exchange without assuming that every initial SYN represents a completed, legitimate connection.

### Cost or caveat
SYN cookies and QUIC Retry are related in purpose but are not the same mechanism.

- SYN cookies protect TCP's half-open connection state.
- QUIC Retry performs address validation using a token.
- MPTCP's `MP_CAPABLE` exchange is an extension to TCP's handshake, not a separate SYN-cookie mechanism.

Stateless operation also has limits: the server must still validate inputs and protect against resource consumption after the handshake.

### How to check
- Draw the ordinary TCP three-way handshake.
- Draw the same handshake with SYN cookies enabled.
- Draw QUIC Initial → Retry → Initial with token → server validation.
- Check RFC 9293 and RFC 9000's address-validation and Retry sections.
- Check RFC 8684 for the exact `MP_CAPABLE` handshake.

---

## Q210. What are delayed ACKs and Nagle's algorithm? How do they interact, and how can they distort RTT samples and small-message latency, for example for VoIP-like traffic?

### What
**Delayed ACK:** A TCP receiver may wait briefly before sending an ACK, allowing it to acknowledge multiple received segments together or combine an ACK with outgoing data.

**Nagle's algorithm:** A TCP sender limits the transmission of additional small segments while previously transmitted data remains unacknowledged. It can combine small writes into larger segments.

### Why
Both mechanisms reduce unnecessary small packets and improve network efficiency.

For example, an application that writes a few bytes repeatedly may otherwise produce many small TCP segments. Nagle's algorithm can reduce this overhead, while delayed ACKs can reduce the number of ACK packets.

### Cost or caveat
The interaction can increase latency:

1. An application sends a small amount of data.
2. The sender has unacknowledged data, so Nagle's algorithm may hold another small write.
3. The receiver delays its ACK.
4. The sender waits for the ACK before sending the next small segment.

This can create an undesirable delay for interactive applications.

For VoIP-like traffic, timely delivery is often more important than reducing packet count. However, actual VoIP systems commonly use UDP/RTP rather than TCP, so this is primarily a useful illustration of small-message latency.

Delayed ACKs can also affect the timing of ACK-based RTT measurements. A measured RTT may include receiver ACK delay rather than representing only network propagation and queueing.

### How to check
- Compare small TCP writes with Nagle enabled and disabled.
- Inspect packet timing and ACK behaviour in Wireshark.
- Check whether the application uses `TCP_NODELAY`.
- Use RFC 9293 for TCP behaviour and the relevant operating-system documentation for implementation details.

---

## Q211. How does Linux auto-tune the receive buffer, and why must the buffer be at least the bandwidth-delay product to fill a path? Why is that rule stricter for a multipath connection?

### What
The **bandwidth-delay product (BDP)** estimates how much data can be in flight on a path:

$$
BDP = Bandwidth \times RTT
$$

For example, for a path with a capacity of 100 Mbps and an RTT of 100 ms:

$$
BDP = 100 \times 10^6 \times 0.1
= 10^7 \text{ bits}
$$

$$
= 1.25 \text{ MB}
$$

A sender and receiver need enough window and buffer capacity to keep approximately this amount of data in flight if they want to fully utilise the path.

Linux TCP receive-buffer auto-tuning adjusts receive-buffer sizes within configured limits based on connection conditions and system settings.

### Why
If the receive window is smaller than the BDP, the sender may run out of permitted in-flight data before the path is fully utilised.

This creates a window-limited connection even if the network itself has spare capacity.

For multipath, the receiver must also deal with data arriving out of order across subflows. Data arriving on a faster path may need to wait for earlier data that is delayed on a slower path.

Consequently, a multipath receiver may need additional buffering for both in-flight data and reordering.

### Cost or caveat
The BDP is a useful capacity estimate, not a universal exact buffer-size rule.

The required buffer depends on:
- Receive-window limits.
- Application read rate.
- Path rates and RTTs.
- Congestion windows.
- Reordering and scheduling behaviour.
- Whether paths share a bottleneck.

Do not simply add the BDPs of two paths and claim that this is always the required MPTCP receive buffer. The connection-level receive buffer and the extra space needed to tolerate cross-path reordering are related but distinct considerations.

### How to check
- Calculate BDP for each path using its bandwidth and RTT.
- Inspect Linux TCP buffer settings, including `net.ipv4.tcp_rmem`.
- Compare throughput when the receive buffer is below and above the path BDP.
- For MPTCP, inspect connection-level and subflow-level statistics.
- Primary sources: Linux TCP documentation and RFC 9293. Treat any specific multipath buffer formula as unverified until checked against the relevant literature.

---

## Q212. What are MSS, MTU and path MTU discovery? What goes wrong when two paths of one connection have different MTUs?

### What
- **MTU (Maximum Transmission Unit):** The maximum size of an IP packet that can be transmitted over a link without fragmentation at that layer.
- **MSS (Maximum Segment Size):** The maximum amount of TCP payload a receiver is willing to accept in one TCP segment.
- **Path MTU:** The smallest MTU along the complete path between two endpoints.
- **Path MTU Discovery (PMTUD):** A mechanism for discovering the path MTU so packets can be sized appropriately.

For ordinary IPv4 without options, a 1500-byte IP MTU generally permits a TCP MSS of 1460 bytes: 1500 minus the 20-byte IPv4 header and 20-byte TCP header.

### Why
Packets larger than a path's supported MTU may be fragmented (where permitted) or dropped. Correct packet sizing avoids fragmentation and black-hole problems.

### Cost or caveat
Two subflows of one MPTCP connection may use different paths with different MTUs.

A segment size that works on one path may be too large for another. The sender must respect the constraints of the subflow used to transmit the data.

This can result in different MSS values and different packetisation on different subflows. It does not mean that the application sees two different byte streams.

QUIC also has to respect path MTU constraints. Its packetisation and path validation mechanisms must account for the size that can safely travel over each path.

### How to check
- Draw two paths with different MTUs.
- Calculate the corresponding TCP MSS values.
- Inspect packet sizes and fragmentation in Wireshark.
- Check RFC 9293 for MSS and RFC 8899 for Datagram Packetization Layer PMTU Discovery.

---

## Q213. How does TCP tolerate reordering: the duplicate-ACK threshold, SACK, RACK-TLP? Why does persistent reordering between paths damage loss detection?

### What
TCP uses several mechanisms to detect missing data and recover from loss.

**Duplicate ACKs:** When a receiver gets data beyond a missing byte range, it may repeatedly acknowledge the last contiguous byte it has received.

**Fast retransmit:** Traditionally, three duplicate ACKs trigger retransmission of the presumed missing segment without waiting for the retransmission timeout.

**SACK (Selective Acknowledgment):** Allows the receiver to report additional blocks of data that have arrived, so the sender can identify which ranges are missing.

**RACK (Recent ACK):** Uses transmission timing and acknowledgment information to infer loss.

**TLP (Tail Loss Probe):** Sends a probe when the tail of a flight may have been lost and ordinary duplicate-ACK evidence is unavailable.

### Why
Reordering is not necessarily loss. These mechanisms help TCP distinguish missing data from data that has simply arrived later.

SACK gives the sender a more detailed picture of what the receiver has already received. RACK uses time-based information to improve loss detection, while TLP helps recover tail losses more quickly.

### Cost or caveat
Multipath increases the likelihood of reordering because different paths can have different delays.

For example:
1. Earlier bytes are sent on a high-RTT path.
2. Later bytes are sent on a low-RTT path.
3. Later bytes arrive first.
4. The receiver generates duplicate ACKs or SACK information.
5. The sender may incorrectly interpret the missing earlier bytes as loss.

Persistent or substantial reordering can therefore cause spurious retransmissions and unnecessary congestion-window reductions.

MPTCP also has a separate data-level sequence space. A subflow's TCP-level ordering and the connection's data-level ordering are not identical.

### How to check
- Draw a packet timeline with one delayed segment and several later segments.
- Inspect duplicate ACKs and SACK blocks in Wireshark.
- Compare loss recovery with and without induced reordering.
- Primary sources: RFC 2018 (SACK), RFC 8985 (RACK-TLP) and RFC 9293.

---

## Q214. What is a spurious retransmission? How do DSACK and undo mechanisms detect and reverse its effects, and why does multipath make spurious retransmissions more likely?

### What
A **spurious retransmission** occurs when a sender retransmits data that was not actually lost. The original transmission may simply have been delayed or reordered.

**DSACK (Duplicate SACK)** allows a receiver to report that it received duplicate data. This can help the sender recognise that a retransmission was unnecessary.

TCP undo mechanisms can reverse certain congestion-control responses when the sender determines that a retransmission was spurious.

### Why
A sender should reduce its congestion window when it detects genuine congestion-related loss. But if it mistakes reordering for loss, it may reduce its sending rate unnecessarily.

Detecting spurious retransmissions helps avoid treating harmless delay variation as congestion.

### Cost or caveat
Multipath makes spurious retransmissions more likely because packets can travel over paths with different RTTs and queueing delays.

A packet sent earlier on a slow path may arrive after a later packet sent on a fast path. The resulting duplicate ACKs or loss-timer expiry can cause an unnecessary retransmission.

DSACK and undo mechanisms are useful, but they do not eliminate every ambiguity or every consequence of reordering.

### How to check
- Create a test with two paths of different RTTs.
- Compare the original transmission and retransmission timestamps.
- Inspect DSACK information and congestion-window changes.
- Check RFC 2883 for DSACK and RFC 3522 for Eifel-based spurious retransmission detection.

---

## Q215. What is ECN, and how does it differ from loss as a congestion signal? What does it change for a coupled congestion controller?

### What
**ECN (Explicit Congestion Notification)** allows network devices to indicate congestion by marking packets instead of necessarily dropping them.

The IP header contains ECN codepoints. A congestion-aware router can mark a packet when congestion develops. The receiver communicates this information to the sender, which can reduce its sending rate.

### Why
Traditional TCP often infers congestion from packet loss. ECN provides an additional signal: congestion can be reported before a packet is dropped.

This can reduce unnecessary retransmissions and help control queueing delay.

### Cost or caveat
ECN requires support and correct configuration across the communication path. Some devices may not preserve or correctly handle ECN markings.

For multipath congestion control, the sender must account for congestion information associated with individual subflows and apply the appropriate coupled response.

The exact response depends on the congestion-control algorithm and its ECN support. Do not assume every MPTCP or MP-QUIC implementation uses identical ECN behaviour.

### How to check
- Compare a congestion experiment using packet loss with one using ECN marking.
- Inspect ECN codepoints and feedback in packet captures.
- Check the congestion-control algorithm's documentation.
- Primary sources: RFC 3168 (ECN) and RFC 6356 (coupled congestion control for MPTCP).

---

## Q216. Compare drop-tail queues with active queue management (RED, CoDel, fq_codel): how does each shape queueing delay and loss? Why does the queue discipline at the bottleneck matter when comparing two protocols?

### What
A **queue discipline (qdisc)** controls how packets are queued and transmitted at a network interface.

| Queue discipline | Behaviour | Main effect |
|---|---|---|
| Drop-tail | Accepts packets until the queue is full, then drops new arrivals | Can create large queues and high delay |
| RED | Randomly drops or marks packets as average queue size increases | Attempts to signal congestion before the queue is full |
| CoDel | Uses packet sojourn time to detect persistent queueing delay | Attempts to control excessive delay |
| fq_codel | Combines flow queueing with CoDel | Provides per-flow isolation and queue-delay control |

### Why
The queue discipline influences:
- Queueing delay.
- Packet loss.
- Burst handling.
- Fairness between flows.
- How congestion signals reach transport protocols.

A protocol's measured throughput and latency depend not only on its transport design but also on the queueing behaviour of the network.

### Cost or caveat
A comparison can be misleading if MPTCP and MP-QUIC are tested under different queue disciplines or different queue configurations.

For example, a large drop-tail queue may allow high throughput but introduce substantial delay. A low-delay queue discipline may change the relative performance of schedulers and congestion-control algorithms.

`fq_codel` also separates flows into queues. The definition of a flow at the network layer may differ from the logical connection being studied.

### How to check
- Record the qdisc and its configuration for every experiment.
- Use `tc qdisc show` to inspect Linux queue disciplines.
- Keep queue settings identical when comparing protocols.
- Repeat tests under more than one queue discipline if queue behaviour is part of the research question.
- Primary sources: RFC 7567 (AQM recommendations), RFC 8289 (CoDel) and RFC 8290 (FQ-CoDel).

---

## Q217. What must the receiver's buffer hold when the two paths differ, and why is it governed by the slower path's RTT rather than by the sum of the two bandwidth-delay products? Derive the rule of thumb yourself, then check it against the literature.

### What
A multipath receiver must hold data that has arrived but cannot yet be delivered in order to the application.

Suppose:
- Path 1 is fast, with rate $R_f$ and RTT $T_f$.
- Path 2 is slower, with rate $R_s$ and RTT $T_s$.
- $T_s > T_f$.

If earlier data is delayed on the slow path, later data can arrive on the fast path and wait in the receiver's reassembly buffer.

A useful first-order estimate of the additional reordering buffer is:

$$
B_{\text{reorder}} \approx R_f \times (T_s-T_f)
$$

This estimates how much later data the fast path could deliver during the RTT difference, assuming it is continuously used and the relevant data ordering creates a corresponding gap.

### Why
The problem is not simply the sum of the bandwidth-delay products of both paths.

The receiver already accounts for data in flight and its normal receive-window constraints. The extra buffer requirement comes from data that arrives ahead of an earlier missing range and must wait for in-order delivery.

The delay difference between paths determines how long later data may accumulate before the earlier data arrives.

### Cost or caveat
The expression above is an **intuition-building approximation**, not a universal buffer-sizing formula.

Actual buffer demand depends on:
- Scheduling policy and which sequence ranges are assigned to each path.
- Path rates and RTTs.
- Congestion windows and receive windows.
- Whether one path stalls or loses packets.
- Application read rate.
- Retransmission and reinjection behaviour.

It is therefore unsafe to state that the receiver buffer is always governed by the slower path's RTT, or that one fixed formula applies to every multipath implementation.

The plan explicitly asks for the exact rule to be verified against literature. Keep the approximation labelled as such until a primary source supports a more precise formula.

### How to check
1. Draw an earlier data block sent on a high-RTT path.
2. Draw later data blocks arriving on a low-RTT path.
3. Mark the period during which the later data must wait.
4. Estimate the amount of fast-path data arriving during that period.
5. Compare the estimate with the receive-buffer and reordering analysis in the relevant MPTCP literature.

---

## Q218. What does UDP give you (ports, a checksum) and what does it not (reliability, ordering, congestion control)? What must any protocol built on UDP rebuild, and how do firewalls and NATs typically treat UDP compared with TCP?

### What
UDP is a connectionless transport protocol that provides:
- Source and destination ports.
- Datagram boundaries.
- A length field.
- A checksum for error detection (mandatory in IPv6, with limited exceptions; IPv4 permits a zero checksum).

UDP does not provide:
- Reliable delivery.
- In-order delivery.
- Retransmission.
- Connection establishment.
- Built-in congestion control.
- Stream-based flow control.

### Why
UDP is intentionally simple. Applications and protocols can build the behaviour they need on top of it.

QUIC builds several transport functions over UDP, including:
- Reliable delivery for streams.
- Stream-level ordering.
- Loss detection and recovery.
- Congestion control.
- Flow control.
- Connection establishment and security integration through TLS 1.3.

QUIC also supports unreliable DATAGRAM frames through an extension, where retransmission is not provided.

### Cost or caveat
A protocol built on UDP must implement congestion control and avoid overwhelming the network. It must also manage loss, retransmission, flow control and security where those features are required.

Firewalls and NATs often maintain state for both TCP and UDP, but their handling differs:
- TCP devices can track connection states such as SYN, established and FIN.
- UDP has no TCP-style handshake or connection state, so NATs commonly use timers for UDP mappings.
- Some networks block or restrict UDP, while others allow it.
- UDP mappings may expire when idle.

Do not claim that UDP is always blocked or always less compatible than TCP. Behaviour depends on the network and middlebox configuration.

### How to check
- Compare TCP and UDP packet headers.
- Inspect NAT and firewall behaviour in a controlled test.
- Check QUIC's transport design in RFC 9000 and its loss detection in RFC 9002.
- Check RFC 768 for UDP and RFC 8085 for UDP usage guidelines.

---

## Q219. Follow a `write()` call down the Linux stack: socket buffer, TCP, IP, queueing discipline, driver, NIC offloads. Where does MPTCP sit in that path, and where does the equivalent QUIC library code run?

### What
A simplified Linux TCP send path is:

```text
Application
    |
    | write()
    v
Socket interface
    |
    v
TCP send buffer
    |
    v
TCP processing
    |
    v
IP layer
    |
    v
Queueing discipline (qdisc)
    |
    v
Network driver
    |
    v
NIC
    |
    v
Network
```

The receiver performs the corresponding receive-side processing before data is made available to its application.

### Why
The operating system separates application-level operations from transport, network and link-layer processing.

**Where MPTCP sits:**

Linux MPTCP is implemented in the kernel. It provides a connection-level transport layer that manages the logical MPTCP connection and its subflows. Data is mapped to individual TCP subflows, which then use the normal lower networking layers.

Simplified:

```text
Application
    |
    v
MPTCP socket / connection layer
    |
    v
Subflow TCP sockets
    |
    v
IP -> qdisc -> driver -> NIC
```

**Where QUIC runs:**

QUIC is generally implemented in a user-space library rather than as a native TCP-like kernel transport.

Simplified:

```text
Application
    |
    v
QUIC library
    |  streams, reliability, congestion control,
    |  packetisation, encryption
    v
UDP socket
    |
    v
IP -> qdisc -> driver -> NIC
```

### Cost or caveat
The diagram is conceptual. Actual Linux internals include additional layers, data structures, offloads and optimisations.

For example:
- TSO (TCP Segmentation Offload) allows the NIC to segment large TCP data buffers.
- GSO (Generic Segmentation Offload) performs segmentation later in the stack.
- GRO (Generic Receive Offload) combines received packets for more efficient processing.

MPTCP's kernel implementation and a user-space QUIC implementation can therefore have different CPU, memory-copy and scheduling costs. A performance comparison must not attribute every difference to the transport protocol design alone.

### How to check
- Inspect Linux MPTCP documentation and kernel architecture.
- Trace socket and packet behaviour using suitable Linux tracing tools.
- Compare CPU utilisation and packet captures.
- Check the implementation documentation for the QUIC library being tested.
- Draw the two stacks side by side.

---

## Q220. What does TCP Fast Open do, and why has it seen limited adoption? How does it interact with MPTCP?

### What
**TCP Fast Open (TFO)** allows data to be sent during the TCP handshake in certain circumstances.

A client that has previously obtained a valid TFO cookie from a server can include that cookie in a later SYN and send data with the SYN. This can reduce the latency associated with waiting for the normal handshake to finish before sending application data.

### Why
For short request-response exchanges, the TCP handshake can represent a significant fraction of total communication time.

TFO attempts to reduce this startup cost by allowing eligible data to travel earlier.

### Cost or caveat
TFO has not been universally deployed because:
- Both endpoints and the network path must support it.
- Middleboxes may interfere with or mishandle the relevant TCP options.
- Server-side state and security considerations must be managed.
- Applications and operating systems may not enable it by default.
- Its benefit is limited for long transfers where handshake time is a small fraction of total completion time.

MPTCP and TFO address different problems:
- TFO reduces connection-startup latency.
- MPTCP enables one logical connection to use multiple subflows.

They should not be treated as interchangeable features. Their exact interaction depends on the MPTCP and TFO implementation and the relevant handshake behaviour. Do not assume that every MPTCP implementation supports TFO in every configuration.

### How to check
- Inspect SYN packets for the TCP Fast Open option and any SYN data.
- Compare first-time and cookie-based connections.
- Check RFC 7413 for TCP Fast Open.
- Check the Linux kernel documentation for implementation-specific support and restrictions.
- Verify MPTCP/TFO interaction against the implementation being tested rather than assuming it.

---

## Q221. Define "connection", "flow", "session", "subflow" and "path" precisely in each of TCP, MPTCP, QUIC and MP-QUIC. Where does the same word mean different things?

### What
These terms describe different levels of communication. Their meanings are not interchangeable.

| Term | TCP | MPTCP | QUIC | MP-QUIC |
|---|---|---|---|---|
| Connection | A logical TCP association identified by endpoint addresses and ports | One logical multipath transport connection containing one or more TCP subflows | A QUIC association identified by connection IDs and protocol state, not only a fixed 4-tuple | One logical QUIC connection using multiple paths |
| Flow | Often a packet flow identified by a 5-tuple: source/destination IP, source/destination port and protocol | May refer to an individual subflow at the IP/network level | Often refers to a UDP packet flow or network 5-tuple; not the same as a QUIC stream | May refer to one path's packet flow; terminology depends on the draft or implementation |
| Session | Not a precise core TCP transport object; often application-defined | Usually application-level or informal terminology, not a synonym for a subflow | Often application- or protocol-context terminology, not necessarily the QUIC connection itself | Depends on application or specification context |
| Subflow | Not a standard TCP concept | An individual TCP connection that belongs to one MPTCP connection | Not a standard QUIC concept | A path-specific transport component only if the particular multipath design uses that term |
| Path | The network route packets take between endpoints | A network route used by an MPTCP subflow | The network route used by QUIC packets; a connection may migrate between paths | One of the network routes used by the multipath QUIC connection |

### Why
The distinction is important because a multipath protocol separates the logical transport connection from the individual network routes used to carry packets.

For MPTCP:
- The application sees one logical connection.
- The MPTCP layer manages that connection.
- Multiple TCP subflows carry its data.
- Each subflow uses a network path.

For QUIC:
- The application uses one QUIC connection.
- QUIC supports multiple streams inside that connection.
- The connection can use connection IDs to survive certain address or port changes.
- A stream is not a path or a subflow.

For MP-QUIC:
- The goal is to use multiple network paths within one logical QUIC connection.
- The exact terms and mechanisms must be tied to the particular multipath QUIC draft or implementation being discussed.

### Cost or caveat
The word **flow** is especially ambiguous. In networking, it often means packets sharing a 5-tuple. In application discussions, it may be used informally for a data stream or communication session.

Similarly, **session** is often application-defined rather than a precise TCP, MPTCP or QUIC transport object.

Do not use:
- QUIC stream and QUIC connection as synonyms.
- MPTCP subflow and MPTCP connection as synonyms.
- Path and flow as automatically equivalent.
- The 2017 research MPQUIC design and a later IETF multipath QUIC draft as if they were identical.

### How to check
For every diagram or answer:
1. Identify the application-visible logical connection.
2. Identify the transport-level connection.
3. Identify the individual subflows or paths.
4. Identify any streams carried inside the connection.
5. State which specification or implementation defines the term.

Primary sources:
- RFC 9293 - TCP.
- RFC 8684 - MPTCP.
- RFC 9000 - QUIC.
- The exact multipath QUIC Internet-Draft revision used by the project.

---

# Part 12 - Final Revision Sheet

| Question | Core concept to remember |
|---|---|
| Q206 | TCP header, sequence/ACK numbers, receive window, 40-byte option limit |
| Q207 | TCP state machine, FIN, RST and TIME_WAIT |
| Q208 | MSS, Window Scale, SACK and Timestamps are TCP-level negotiated capabilities |
| Q209 | SYN flood, SYN cookies and QUIC Retry |
| Q210 | Delayed ACK + Nagle can increase small-message latency |
| Q211 | BDP determines the approximate in-flight data needed to fill a path |
| Q212 | MTU, MSS and path MTU discovery |
| Q213 | Duplicate ACKs, SACK, RACK-TLP and reordering |
| Q214 | Spurious retransmission, DSACK and undo |
| Q215 | ECN marks congestion instead of relying only on loss |
| Q216 | Queue disciplines affect delay, loss and measured protocol performance |
| Q217 | Cross-path reordering creates receiver-buffer requirements |
| Q218 | UDP is a minimal datagram transport; QUIC builds transport functions over it |
| Q219 | MPTCP is kernel-based in Linux; QUIC commonly runs in user space over UDP |
| Q220 | TCP Fast Open reduces eligible connection-startup delay |
| Q221 | Distinguish logical connection, flow, session, subflow, stream and path |

# Important Source and Verification Notes

Use these primary references when checking the final answers:

| Reference | Relevant questions |
|---|---|
| RFC 768 - User Datagram Protocol | Q218 |
| RFC 9293 - Transmission Control Protocol | Q206-Q208, Q210, Q212 |
| RFC 2018 - TCP Selective Acknowledgment | Q213 |
| RFC 2883 - An Extension to the Selective Acknowledgement (SACK) Option for TCP | Q214 |
| RFC 3168 - The Addition of Explicit Congestion Notification (ECN) to IP | Q215 |
| RFC 3522 - The Eifel Detection Algorithm for TCP | Q214 |
| RFC 5681 - TCP Congestion Control | Q213, Q215 |
| RFC 6298 - Computing TCP's Retransmission Timer | Q207, Q213 |
| RFC 7413 - TCP Fast Open | Q220 |
| RFC 7567 - IETF Recommendations Regarding Active Queue Management | Q216 |
| RFC 8289 - CoDel | Q216 |
| RFC 8290 - The Flow Queue CoDel Packet Scheduler and Active Queue Management Algorithm | Q216 |
| RFC 8684 - TCP Extensions for Multipath Operation with Multiple Addresses | Q206-Q208, Q211, Q217, Q219, Q221 |
| RFC 8899 - Packetization Layer Path MTU Discovery for Datagram Transports | Q212 |
| RFC 8985 - The RACK-TLP Loss Detection Algorithm for TCP | Q213 |
| RFC 9000 - QUIC: A UDP-Based Multiplexed and Secure Transport | Q209, Q218, Q219, Q221 |
| RFC 9002 - QUIC Loss Detection and Congestion Control | Q218, Q219 |
| RFC 6356 - Coupled Congestion Control for Multipath TCP | Q215 |

## Claims to keep qualified

1. **Q208:** TCP options are negotiated per TCP subflow; do not assume every MPTCP property is per subflow.
2. **Q209:** SYN cookies and QUIC Retry have related anti-resource-exhaustion goals but are not the same mechanism.
3. **Q211:** BDP is an estimate of in-flight data, not an exact universal receive-buffer setting.
4. **Q217:** The buffer expression is a simplified reordering estimate, not a verified universal rule.
5. **Q219:** Kernel versus user-space placement is a useful architectural distinction, but implementation details can vary.
6. **Q220:** TFO's interaction with MPTCP must be checked for the specific implementation.
7. **Q221:** MP-QUIC terminology and mechanisms must be tied to the exact draft revision.

**Revision target:** Be able to draw the TCP header, handshake and close; explain BDP and reordering with a numerical example; draw the Linux MPTCP and user-space QUIC stacks; and distinguish a connection, stream, subflow and path without mixing their sequence spaces.

### Part 12 status

(Draft prepared) The complete Q206-Q221 answer file is now drafted. Before marking it fully verified, the two points that deserve particular attention are **Q217's exact receiver-buffer rule** and **Q220's implementation-specific MPTCP/TFO interaction**\. The other answers also need the cited RFC sections checked during your source-reference pass.

Next, we should do **Part 21 - Q323 A-Z term drill**, as a separate Markdown file.

## Prompt:
11/3/2026, 4:32:24 PM

done now next

## Response:
11/3/2026, 4:31:31 PM · gpt-6

> **Retrieved exact Q323 Part21 source lines preceding line 750**
>
> 
>
> Worked for 14s

## Step 2 - Part 21: A-Z Term Drill (Q323)

This is the final shared question in the plan. The instruction is to define every listed term in **one or two sentences from memory**, identify the question that covers it, and turn any uncovered term into a gap for the team additions section.

Save this as\:

`13_AZ_Term_Drill_Q323/AZ_Term_Drill.md`

I’ve kept the plan’s A-Z grouping and retained the **$$verify$$** flags. Where the plan does not give a clear question number for a term, I’ll mark it as a related-question reference rather than pretend it is explicitly covered.

**document: **

# Part 21 - A-Z Term Drill (Q323)

**Project:** MPTCP vs MP-QUIC  
**Scope:** Everyone  
**Question:** Q323  
**Purpose:** Define every term in one or two sentences, identify where it is covered, and identify gaps that may need new team questions.

---

## A

| Term | Definition | Related question(s) |
|---|---|---|
| **ACK delay** | The time between receiving data and sending an acknowledgment. QUIC communicates ACK delay information so the sender can interpret RTT measurements more accurately. | Q213, Q299 |
| **ACK ranges** | QUIC ACK frames can acknowledge multiple ranges of packet numbers, allowing the receiver to report which packets arrived even when packets were reordered or lost. | Q299, Q213 |
| **ADD_ADDR** | An MPTCP option that advertises an additional address at which the peer may establish another subflow. It helps endpoints discover additional paths. | Q43-Q55, Q223 |
| **Aggregation** | Using multiple paths simultaneously to combine their available capacity for one logical connection. Actual gain depends on path independence, scheduling, congestion control and receiver limitations. | Q177-Q182, Q287 |
| **AIMD** | Additive Increase, Multiplicative Decrease: a congestion-control approach that gradually increases sending rate and reduces it multiplicatively when congestion is detected. It is central to traditional TCP congestion-control behaviour. | Q265-Q270 |
| **AEAD nonce** | A nonce is a value supplied to an authenticated-encryption algorithm along with a key. QUIC constructs packet-protection nonces using packet-number-related information; nonce uniqueness under a given key is essential for security. | Q305, Q299 |
| **Anti-amplification limit** | A QUIC server that has not validated a client's address is restricted in how much data it may send to that address. This limits the ability of an attacker to use a spoofed source address to make a server send much more traffic than it receives. | Q209, Q305 |
| **AQM** | Active Queue Management controls queue growth by dropping or marking packets before a queue becomes full. Examples include RED and CoDel. | Q216 |
| **ATSSS [verify]** | Access Traffic Steering, Switching and Splitting is a 3GPP framework for managing traffic across multiple access networks in 5G systems. Its exact steering modes and the roles of MPTCP and other mechanisms should be checked against the relevant 3GPP specification. | Q315 |

## B

| Term | Definition | Related question(s) |
|---|---|---|
| **Backup path** | A path kept available for use when the preferred path becomes unavailable or unsuitable. It provides resilience but may not contribute to normal throughput aggregation. | Q177, Q182, Q185 |
| **BALIA** | Balanced Linked Adaptation is a coupled congestion-control algorithm designed for multipath transports. It aims to balance responsiveness, aggressiveness and friendliness across subflows. | Q265-Q273 |
| **Bandwidth-delay product (BDP)** | The product of a path's bandwidth and RTT, representing the approximate amount of data that can be in flight while fully utilising the path. | Q211, Q217 |
| **BBR** | Bottleneck Bandwidth and Round-trip propagation time is a model-based congestion-control algorithm that estimates bottleneck bandwidth and propagation delay. Its behaviour under coupled multipath operation depends on the implementation and coupling strategy. | Q273 |
| **BLEST** | Blocking Estimation-based Scheduler is an MPTCP scheduling approach that tries to avoid sending data on a slower path when doing so could cause excessive in-order delivery blocking. | Q274-Q278 |
| **Bufferbloat** | Excessive queueing in network buffers that creates high latency even when packets are not being dropped. It can make interactive applications slow and distort RTT-based scheduling decisions. | Q216, Q276 |

## C

| Term | Definition | Related question(s) |
|---|---|---|
| **Congestion window (cwnd)** | A sender-side limit on the amount of unacknowledged data it may have in flight, imposed by congestion control. It is distinct from the receiver's advertised flow-control window. | Q211, Q215, Q277 |
| **Connection ID (CID)** | A QUIC identifier used to identify a connection independently of a fixed IP-address and port tuple. It helps QUIC maintain a connection when network addresses change. | Q221, Q299 |
| **Coupled congestion control** | A congestion-control approach in which multiple subflows of one multipath connection coordinate their sending rates rather than behaving as completely independent TCP flows. | Q265-Q273 |
| **CRYPTO frame** | A QUIC frame that carries cryptographic handshake data. It is used during the QUIC/TLS handshake and is not an application data stream frame. | Q299, Q305 |
| **CUBIC** | A TCP congestion-control algorithm that increases its congestion window using a cubic function of time since the last congestion event. It is widely used in Linux TCP implementations. | Q265-Q273, Q197 |

## D

| Term | Definition | Related question(s) |
|---|---|---|
| **Data ACK** | An MPTCP-level acknowledgment indicating the next Data Sequence Number expected by the receiver. It acknowledges data at the connection level, not merely bytes on one TCP subflow. | Q298, Q211, Q303 |
| **Data Sequence Number (DSN)** | The sequence number used by MPTCP to identify data in the logical connection-wide byte stream. It is distinct from the TCP sequence number maintained by each subflow. | Q298, Q300 |
| **DATA_FIN** | An MPTCP signal indicating that the sender has finished sending data on the logical MPTCP connection. It is different from an ordinary TCP FIN that closes an individual subflow. | Q298, Q303 |
| **DATAGRAM frame** | A QUIC DATAGRAM extension frame that carries unreliable application data. It is not retransmitted by QUIC when lost, making it useful for some latency-sensitive traffic. | Q261, Q286 |
| **Delayed ACK** | A TCP behaviour in which the receiver waits briefly before sending an ACK, potentially acknowledging multiple segments together. It can reduce ACK traffic but may increase latency for small exchanges. | Q210 |
| **DSACK** | Duplicate Selective Acknowledgment is a TCP SACK extension that reports duplicate data received by the receiver. It can help the sender detect spurious retransmissions. | Q214 |
| **DSS** | Data Sequence Signal is an MPTCP TCP option used to map subflow TCP sequence numbers to connection-level Data Sequence Numbers and to carry Data ACK information. | Q206, Q208, Q298, Q303 |
| **DSS checksum** | An optional checksum associated with MPTCP DSS mappings that helps detect corruption or inconsistencies in the mapping between subflow sequence space and data sequence space. | Q303 |

## E

| Term | Definition | Related question(s) |
|---|---|---|
| **ECF [verify]** | The plan lists ECF without expanding it. Its intended meaning in this project is not established by the supplied plan, so do not invent a definition; ask the team or inspect the source where it was introduced. | Gap - confirm source and intended expansion |
| **ECMP** | Equal-Cost Multi-Path routing distributes traffic across multiple routes with equal routing cost. It generally operates at the network layer and does not itself provide one transport connection with coordinated multipath reliability. | Q194, Q310 |
| **ECN** | Explicit Congestion Notification allows network devices to mark packets to signal congestion instead of relying only on packet drops. The transport endpoints use the feedback to adjust sending behaviour. | Q215, Q273 |

## F

| Term | Definition | Related question(s) |
|---|---|---|
| **Failover** | Switching traffic to an alternative path when the currently used path fails or becomes unsuitable. Unlike aggregation, the alternative path may remain idle until needed. | Q177, Q182, Q185 |
| **Fallback to TCP** | Using ordinary TCP when a more advanced transport cannot be established or supported. This can improve compatibility but may remove multipath or other transport features. | Q186, Q192 |
| **FEC** | Forward Error Correction adds redundant information so a receiver can recover some lost data without requesting retransmission. It trades additional bandwidth for potentially lower recovery delay. | Q279 |
| **Flow control** | A mechanism that prevents a sender from overwhelming the receiver's available buffering capacity. TCP uses its advertised receive window; QUIC has connection-level and stream-level flow-control mechanisms. | Q211, Q218, Q277 |
| **fq_codel** | Fair Queue Controlled Delay is a Linux queue discipline combining per-flow queueing with CoDel active queue management. It aims to reduce persistent queueing delay while providing flow isolation. | Q216 |

## G

| Term | Definition | Related question(s) |
|---|---|---|
| **Goodput** | The rate of useful application data delivered successfully, excluding protocol headers, retransmitted data and other overhead. It can be lower than raw throughput. | Q179, Q287 |
| **GSO and GRO** | Generic Segmentation Offload allows large packets to be segmented later in the networking stack, while Generic Receive Offload combines received packets to reduce processing overhead. | Q219 |

## H

| Term | Definition | Related question(s) |
|---|---|---|
| **Handover** | Moving an active communication from one network attachment or access network to another. Multipath can support make-before-break transitions by using the new path before the old one disappears. | Q177, Q182, Q288 |
| **Head-of-line (HOL) blocking** | A condition in which later data cannot be delivered or processed because an earlier piece of data is missing or delayed. TCP can create connection-wide transport HOL blocking; QUIC streams reduce cross-stream transport blocking, but ordering within a stream remains. | Q178, Q213, Q274, Q280 |
| **Header protection** | QUIC packet protection that obscures selected bits of the packet header, including parts of the packet number, to make traffic analysis and manipulation harder. It is distinct from payload encryption. | Q305, Q299 |
| **HTTP/3** | The HTTP mapping that runs over QUIC. It uses QUIC streams and QPACK for header compression rather than using TCP as HTTP/2 does. | Q178, Q280, Q317 |
| **Hybrid access** | A network arrangement that combines different access technologies, such as fixed broadband and cellular, often using a proxy or aggregation point to manage traffic across them. | Q177, Q288, Q319 |

## I

| Term | Definition | Related question(s) |
|---|---|---|
| **Infinite mapping** | An MPTCP fallback mechanism that allows a connection to continue using a single TCP subflow when normal DSS mapping cannot be used or maintained. It sacrifices normal multipath data mapping to preserve compatibility or continuity. | Q222-Q225, Q303 |
| **`initial_max_path_id`** | A transport parameter used in the multipath QUIC design to communicate the initial range or limit of path identifiers that may be used. Its exact semantics must be checked against the particular draft revision being studied. | Q262-Q264, Q296 - verify exact draft |

## J

| Term | Definition | Related question(s) |
|---|---|---|
| **Jain's fairness index** | A metric for measuring how fairly a resource is distributed among flows. For rates $x_i$, it is $J=(\sum x_i)^2/(n\sum x_i^2)$, with values closer to 1 indicating greater equality. | Q265, Q266 |
| **Jitter** | Variation in packet arrival delay. High jitter makes it harder for real-time applications to deliver audio or video smoothly. | Q180, Q283-Q285 |
| **Jitter buffer** | A receiver-side buffer that temporarily stores real-time packets to smooth out variations in arrival time. A larger buffer can reduce late packet loss but increases playback delay. | Q283, Q284 |

## K

| Term | Definition | Related question(s) |
|---|---|---|
| **Karn's algorithm** | A TCP RTT-measurement rule that avoids using ambiguous acknowledgments of retransmitted segments to update RTT estimates. This prevents retransmission ambiguity from corrupting the RTT estimator. | Q213, Q214 |
| **Key update** | A QUIC mechanism for updating traffic-protection keys during a connection. It limits how long a single packet-protection key is used. | Q305, Q299 |

## L

| Term | Definition | Related question(s) |
|---|---|---|
| **LIA** | Linked Increases Algorithm is a coupled congestion-control algorithm for MPTCP. It coordinates subflow congestion windows to balance the goals of improving multipath throughput and remaining fair to competing single-path TCP flows. | Q268-Q271 |
| **Long header** | A QUIC packet header form used during connection establishment and certain control operations. It includes fields such as version and connection IDs; short headers are used for ordinary protected application traffic. | Q299 |
| **Loss recovery** | The mechanisms used by a transport to detect missing data and recover from it, often through retransmission or other repair. TCP and QUIC have different packet and acknowledgment models for this process. | Q213, Q298, Q299 |

## M

| Term | Definition | Related question(s) |
|---|---|---|
| **Make-before-break** | Establishing or activating a new path before terminating the old path. It helps reduce interruptions during handover. | Q177, Q182, Q288 |
| **Middlebox** | A network device between endpoints that performs functions such as NAT, firewalling, proxying or traffic inspection. It may affect transport behaviour by modifying, filtering or blocking packets and options. | Q186, Q223, Q293 |
| **MP_CAPABLE** | The MPTCP option used during the initial handshake to negotiate MPTCP capability and exchange key material. | Q43-Q55, Q209, Q298 |
| **MP_FAIL** | An MPTCP option used to signal a data-level mapping failure associated with a particular Data Sequence Number. It helps communicate that the normal mapping cannot be relied upon. | Q222-Q225 |
| **MP_FASTCLOSE** | An MPTCP option used to close an MPTCP connection quickly using connection-level key information. It is distinct from simply closing one TCP subflow. | Q222, Q298 |
| **MP_JOIN** | The MPTCP option used to authenticate and join an additional TCP subflow to an existing MPTCP connection. | Q43-Q55, Q298 |
| **MP_PRIO** | An MPTCP option used to signal whether a subflow should be treated as a backup path or a regular path. | Q43-Q55, Q177 |
| **MSS** | Maximum Segment Size is the maximum TCP payload size that a receiver is willing to accept in a single TCP segment. It is related to, but not identical to, the path MTU. | Q208, Q212 |
| **MTU** | Maximum Transmission Unit is the largest packet size that can be transmitted over a link without fragmentation at that layer. Different paths may have different MTUs. | Q212 |

## N

| Term | Definition | Related question(s) |
|---|---|---|
| **Nagle's algorithm** | A TCP mechanism that reduces small-packet overhead by holding additional small writes while previously sent data remains unacknowledged. It can increase latency for interactive applications. | Q210 |
| **NAT** | Network Address Translation changes packet address or port information, commonly allowing multiple private devices to share a public address. NAT behaviour can affect path establishment and address reachability. | Q186, Q301, Q262 |
| **NAT rebinding** | A change in the public-facing address or port mapping assigned by a NAT while communication is ongoing. QUIC's connection IDs can help a connection survive certain address or port changes. | Q221, Q301 |

## O

| Term | Definition | Related question(s) |
|---|---|---|
| **OLIA** | Opportunistic Linked-Increases Algorithm is a coupled congestion-control algorithm for MPTCP designed to improve on limitations of LIA while retaining TCP-friendliness and multipath resource use. | Q270, Q271 |
| **Opportunistic retransmission** | A recovery approach in which data may be retransmitted or reinjected over another available path when doing so is expected to improve delivery. It can reduce recovery delay but may consume extra capacity or create duplicates. | Q274, Q298, Q303 |
| **Ossification** | The process by which network behaviour becomes difficult to change because middleboxes and deployed systems depend on existing protocol formats or behaviours. It makes deployment of new transport features harder. | Q191-Q194, Q223, Q293 |

## P

| Term | Definition | Related question(s) |
|---|---|---|
| **Packet number space** | A QUIC concept in which packet numbers are maintained within separate spaces, such as Initial, Handshake and Application Data. The exact packet-number-space model for multipath QUIC depends on the draft revision. | Q299, Q303 |
| **Path ID** | An identifier used by a multipath QUIC design to distinguish one path from another within a connection. Its exact use and signalling rules are draft-version dependent. | Q262-Q264, Q296 |
| **PATH_ABANDON** | A multipath QUIC frame in the relevant IETF design used to indicate that a path is being abandoned. Its exact semantics should be checked against the project's selected draft revision. | Q299, Q303 |
| **PATH_ACK** | A multipath QUIC frame associated with acknowledging path-related validation or management information. Check the precise definition in the selected draft revision. | Q299, Q296 - verify |
| **PATH_CHALLENGE** | A QUIC path-validation frame used to test whether a peer can receive and return a challenge on a particular path. | Q301, Q299 |
| **Path manager** | The component or logic that decides which network addresses and paths should be used, added, prioritised or removed. It may operate in the kernel, userspace or an application-controlled component. | Q262, Q302 |
| **Penalisation** | Reducing the sending preference or resources assigned to a path that performs poorly, for example because of loss, delay or congestion. The exact policy is scheduler- and implementation-dependent. | Q274-Q278 |
| **PEP** | Performance Enhancing Proxy: a middlebox that modifies or splits transport behaviour to improve performance over a particular network. It can improve performance but may weaken end-to-end transport semantics. | Q312, Q314, Q319 |
| **PMTUD** | Path MTU Discovery is the process of determining the largest packet size that can traverse a path without fragmentation or being dropped due to size. | Q212 |
| **PTO** | Probe Timeout is a QUIC loss-recovery timer that causes a sender to send probe packets when acknowledgments have not arrived in time. It is not simply identical to TCP's retransmission timeout. | Q299, Q213 |

## Q

| Term | Definition | Related question(s) |
|---|---|---|
| **QoE** | Quality of Experience describes how users perceive the quality of an application, such as video playback or voice communication. It includes factors such as startup delay, rebuffering, latency and quality changes. | Q177-Q190, Q280-Q286 |
| **QPACK** | The header-compression mechanism used by HTTP/3. It is designed to work with QUIC's stream model while avoiding the connection-wide blocking problem associated with some earlier header-compression designs. | Q178, Q280, Q317 |
| **qlog** | A structured logging format and ecosystem for recording QUIC events. It helps developers inspect connection behaviour, packet events, loss recovery and performance. | Q195, Q199, Q308 |

## R

| Term | Definition | Related question(s) |
|---|---|---|
| **RACK-TLP** | A TCP loss-detection approach combining time-based RACK loss detection with Tail Loss Probe. It helps detect losses without relying exclusively on duplicate ACK thresholds or waiting for a long retransmission timeout. | Q213 |
| **Receive window** | The amount of additional data a receiver advertises that it can accept. It is a flow-control limit and is distinct from the sender's congestion window. | Q211, Q277 |
| **Reinjection** | Sending data again over another subflow or path when the original transmission is delayed or considered lost. It can improve delivery but may create duplicate transmissions. | Q298, Q303 |
| **Resource pooling** | The multipath goal of making several paths behave more like one shared pool of network capacity, rather than treating them as completely independent resources. | Q268, Q269 |
| **Retry packet** | A QUIC packet sent by a server to request that the client retry connection establishment with a token. It supports address validation before the server allocates more state. | Q209, Q299 |
| **RTO** | Retransmission Timeout is the TCP timer used to retransmit data when acknowledgment progress has not occurred within the estimated timeout. It is calculated using RTT estimates and variation. | Q207, Q213 |
| **RTT** | Round-Trip Time is the time taken for a packet or signal to travel to a peer and for a corresponding response to return. It includes propagation, processing and potentially queueing delay. | Q184, Q267, Q276 |

## S

| Term | Definition | Related question(s) |
|---|---|---|
| **SACK** | Selective Acknowledgment allows a TCP receiver to report blocks of data received beyond the last contiguous byte. It helps the sender recover efficiently from multiple losses. | Q208, Q213 |
| **Scheduler** | The component that decides which path or subflow should carry particular data. Its decisions affect throughput, latency, reordering and application-level blocking. | Q274-Q278 |
| **Shared bottleneck** | A network resource, such as a router link, that is used by more than one path. Two paths sharing a bottleneck may not provide the combined capacity suggested by adding their individual rates. | Q201, Q268, Q272 |
| **Slow start** | A TCP congestion-control phase in which the congestion window grows rapidly, generally exponentially per RTT, until a threshold or congestion event changes the behaviour. | Q265, Q266 |
| **Spin bit** | An optional QUIC header bit that can provide an observable indication of RTT to on-path measurement systems. It is designed to support measurement without exposing all transport state. | Q305, Q308 |
| **Spurious retransmission** | A retransmission of data that was not actually lost; the original packet may simply have been delayed or reordered. It can cause unnecessary congestion-window reduction. | Q214 |
| **Stateless reset** | A QUIC mechanism that allows an endpoint to signal that it no longer has state for a connection. It helps terminate connections when normal connection state is unavailable. | Q305, Q299 |
| **Stream** | A QUIC abstraction for an ordered sequence of bytes within a connection. Multiple streams can progress independently, although data within an individual stream remains ordered. | Q178, Q221, Q299 |
| **Subflow** | An individual TCP connection that forms part of an MPTCP connection. Each subflow has its own TCP sequence space and TCP-level state. | Q207, Q221, Q298 |
| **SYN cookie** | A TCP defence against SYN floods in which the server encodes necessary handshake information into its SYN/ACK sequence number instead of retaining ordinary state for every incomplete connection. | Q209 |

## T

| Term | Definition | Related question(s) |
|---|---|---|
| **TCP Fast Open (TFO)** | A TCP extension that can allow data to be sent in the SYN when a valid cookie is available, reducing startup latency for eligible connections. | Q220 |
| **TIME_WAIT** | A TCP state retained after active connection closure to allow delayed segments to expire and to ensure the final ACK can be retransmitted if needed. | Q207 |
| **Token (MPTCP)** | A value derived from MPTCP key material and used to identify an existing MPTCP connection when another subflow attempts to join it. It is involved in the MP_JOIN process. | Q43-Q55, Q298 |
| **TSO** | TCP Segmentation Offload allows the operating system to pass a large TCP data buffer to the NIC, which divides it into appropriately sized TCP segments. It reduces CPU overhead. | Q219 |

## U

| Term | Definition | Related question(s) |
|---|---|---|
| **UDP** | User Datagram Protocol provides datagram delivery with ports and a checksum, but does not itself provide reliable delivery, ordering, retransmission or congestion control. QUIC builds these additional transport features over UDP. | Q218 |
| **Userspace path manager** | Path-management logic implemented in a user-space library or application rather than directly in the kernel. It can make application-specific decisions but depends on the library's access to network interfaces and system APIs. | Q262, Q302 |

## V

| Term | Definition | Related question(s) |
|---|---|---|
| **Version negotiation** | A QUIC mechanism that allows endpoints to identify incompatible QUIC versions and negotiate or select a mutually supported version. | Q192, Q299 |

## W

| Term | Definition | Related question(s) |
|---|---|---|
| **Window scaling** | A TCP option negotiated during the handshake that extends the effective receive-window size beyond the 16-bit TCP window field's original range. It is important for high-bandwidth, high-RTT paths. | Q208, Q211 |

## X

| Term | Definition | Related question(s) |
|---|---|---|
| **XLINK [verify]** | The plan names XLINK as an example of QoE-driven multipath QUIC work for large-scale video services. Its exact system design, publication and distinction from the IETF multipath QUIC draft must be checked against the primary paper. | Q295, Q296 - verify |

## Y

The original plan contains no Y term. Add a useful term if the team identifies one that is important to the project and is not already covered.

Suggested candidate: **YANG** - a data-modelling language used to describe configuration and operational state in network-management systems. Only include it if the team discusses network configuration or management; it is not currently a core term in the supplied plan.

## Z

| Term | Definition | Related question(s) |
|---|---|---|
| **Zero-length connection ID** | A QUIC connection ID of length zero. In this case, packets do not carry a connection ID value for connection demultiplexing, which limits the ability to identify a connection independently of its network address tuple. | Q221, Q299 |

---

# Q323 - Gap and Verification Register

The following entries need explicit checking before the glossary is treated as fully verified.

| Term | What needs checking | Action |
|---|---|---|
| ATSSS | Exact 3GPP steering, switching and splitting modes; relationship to MPTCP and other transports | Check the relevant 3GPP specification and Q315 |
| ECF | The plan does not define this abbreviation | Ask the team which source introduced it; do not invent an expansion |
| `initial_max_path_id` | Exact meaning and use in the selected multipath QUIC draft | Check the exact draft revision |
| PATH_ACK | Exact frame semantics in the selected draft | Check the draft's frame definitions |
| XLINK | Exact paper, architecture and QoE objective | Read the primary paper referenced by Q295 |
| BALIA | Exact algorithm behaviour and design goals | Check its original publication |
| BLEST | Exact scheduling decision and blocking-estimation method | Check its original publication |
| Infinite mapping | Exact conditions and fallback behaviour | Check RFC 8684 |
| MPTCP token | Exact derivation and use in connection identification and MP_JOIN | Check RFC 8684 |
| DSS checksum | Negotiation, use and failure behaviour | Check RFC 8684 |
| MP_FAIL | Exact signalling and recovery behaviour | Check RFC 8684 |
| MP_FASTCLOSE | Exact close semantics and authentication-related details | Check RFC 8684 |
| PATH_ABANDON | Exact frame behaviour and path-state transition | Check selected multipath QUIC draft |
| Packet number space | Whether the selected multipath QUIC revision uses per-path packet-number spaces and how ACKs are scoped | Check selected draft revision |

## Suggested team additions

The plan says a term that cannot be defined or is not covered by an existing question should become a new question. These are candidates, not automatically approved additions:

- **Q401 - ECF:** What does ECF stand for in our project material, what problem does it solve, and where is it specified?
- **Q402 - XLINK:** What is XLINK's architecture, what QoE problem does it target, and how does it differ from the IETF multipath QUIC design?
- **Q403 - Path-management identifiers:** What does `initial_max_path_id` mean in the selected multipath QUIC draft, and how does it relate to path IDs and path validation?

Confirm with the team that these are genuine gaps and are not already covered before assigning owners or adding them to the official question list.

---

# Final Self-Test

Try to answer these without looking at the definitions:

1. What is the difference between a TCP sequence number and an MPTCP Data Sequence Number?
2. What is the difference between a QUIC packet number and a QUIC stream offset?
3. Why are a congestion window and receive window not interchangeable?
4. Why can a second path increase throughput but also increase head-of-line blocking?
5. What is the difference between aggregation, failover and handover?
6. Why are MPTCP subflows separate TCP connections but not separate application connections?
7. Why does QUIC use connection IDs?
8. What is the difference between loss recovery and flow control?
9. Why is a shared bottleneck important when evaluating multipath?
10. Why is a QUIC DATAGRAM frame not equivalent to a reliable QUIC stream?

**Completion criterion:** Every term can be explained in one or two sentences, the related question can be identified, and every unresolved term is recorded for verification or team discussion.

## Part 21 status

(Draft prepared) The A-Z glossary is drafted, including the verification register and possible team additions. The terms marked **$$verify$$**, especially ECF, ATSSS, XLINK and the multipath QUIC path-management fields, should remain open until checked against their primary sources.

**Next deliverable: the separate cross-training file containing the 30 questions from Krina, Kaushal and Pratik.** I'll organise it into three sections of ten questions, with answers and a quick revision format.

## Prompt:
11/3/2026, 4:42:56 PM

done next

## Response:
11/3/2026, 4:42:04 PM · gpt-6

> **Reviewed file context and retrieved missing questionnaire questions**
>
> 
>
> Worked for 9s

The next deliverable is your **30-question cross-training file**\: 10 questions from Krina’s MPTCP section, 10 from Kaushal’s QUIC section, and 10 from Pratik’s methods and end-to-end sections. These are the questions *you need to prepare from the other three members’ areas*\.

I checked the question wording against the uploaded project plan. Here is the paste-ready file.

**document: **

# Cross-Training: 30 Questions from Other Members

**Project:** MPTCP vs MP-QUIC  
**Purpose:** Questions Swamini must prepare from the areas led by Krina, Kaushal and Pratik.  
**Answer format:** What it is → Why it is needed → Cost or caveat → How to verify it.

---

## Section 1 - Krina: MPTCP (10 Questions)

### Q29. What application-compatibility and network-compatibility goals did MPTCP set itself, and which design choices follow from each?

**What:** MPTCP aims to provide multiple-path communication while remaining compatible with existing TCP applications and as much of the existing Internet infrastructure as possible.

**Why:** Applications should continue to use a familiar TCP socket and byte stream. Networks should be able to carry MPTCP traffic without requiring a completely new transport protocol.

**Cost or caveat:** MPTCP extends TCP using options, which can be stripped or modified by middleboxes. Compatibility therefore cannot be guaranteed on every network.

**How to check:** Examine RFC 8684's design and handshake. Test whether an MPTCP connection succeeds or falls back to ordinary TCP when options are not supported.

### Q30. Why does MPTCP look like one ordinary TCP socket to the application? What does the application see, and what is hidden from it?

**What:** MPTCP presents one reliable, ordered byte stream through a socket-like interface.

**Why:** Existing TCP applications can use multipath without being rewritten to manage individual paths or combine data themselves.

**Cost or caveat:** The application does not directly control which subflow carries each piece of data. Scheduling, reordering and reinjection are handled below the application interface.

**How to check:** Trace an application's socket operations and inspect the connection using Linux MPTCP tools. Compare the application's single connection with the multiple subflows visible at the transport layer.

### Q33. Walk through the MP_CAPABLE handshake. What is sent in the SYN, SYN/ACK and ACK, what are the keys for, and why does MPTCP v1 send both keys again in the third ACK?

**What:** MP_CAPABLE negotiates MPTCP during the initial TCP handshake. The peers exchange keys that establish the identity and initial sequence-space information for the MPTCP connection.

**Why:** The keys allow the endpoints to derive connection-related values and establish that both sides support MPTCP.

**Cost or caveat:** The handshake must fit within TCP's limited option space and remain compatible with ordinary TCP behaviour. The third-ACK design also helps the server avoid retaining unnecessary state before the client confirms the exchange.

**How to check:** Follow the MP_CAPABLE option across SYN, SYN/ACK and ACK in RFC 8684 and in a Wireshark capture. Distinguish the MPTCP connection handshake from the handshakes of later subflows.

### Q35. Walk through MP_JOIN. What do the token, nonces and HMAC protect against, and what attack is the join handshake meant to stop?

**What:** MP_JOIN authenticates a new TCP subflow as belonging to an existing MPTCP connection. The token identifies the connection, while nonces and HMAC values contribute to authentication.

**Why:** A new path must not be allowed to join a connection merely because an attacker knows or guesses its network addresses.

**Cost or caveat:** Authentication adds handshake fields and processing. It does not make MPTCP immune to every on-path or denial-of-service attack.

**How to check:** Trace the MP_JOIN SYN, SYN/ACK and ACK exchanges in RFC 8684. Identify where the token, nonces and HMAC values are used.

### Q40. Explain the subflow sequence number and the data sequence number. Why can one level not do both jobs?

**What:** A subflow sequence number tracks bytes within an individual TCP subflow. A data sequence number (DSN) tracks the byte stream across the entire MPTCP connection.

**Why:** Different subflows can carry different portions of one application byte stream. The receiver needs a connection-level sequence space to reconstruct the correct overall order.

**Cost or caveat:** Maintaining two sequence spaces and their mappings increases protocol complexity and receiver bookkeeping.

**How to check:** Inspect DSS mappings in RFC 8684 or a packet capture. Follow one data range from its DSN to the corresponding subflow sequence numbers.

### Q42. Why is a Data ACK needed on top of subflow ACKs? What goes wrong if MPTCP relies on subflow ACKs alone?

**What:** A subflow ACK acknowledges TCP bytes received on one subflow. A Data ACK acknowledges progress in the connection-level MPTCP data sequence space.

**Why:** Receiving a TCP segment on one subflow does not by itself establish that the corresponding application data has been received in the correct connection-level sequence.

**Cost or caveat:** A second acknowledgement level adds protocol overhead and state. The two ACK types must not be confused when interpreting captures.

**How to check:** Compare subflow ACKs and Data ACKs in the DSS option. Trace a data range sent over one subflow and identify when connection-level progress is acknowledged.

### Q46. Where does connection-level reordering happen at the receiver, and how large must the receive buffer be relative to the path delays?

**What:** MPTCP reassembles data at the connection level using DSNs. Data arriving over faster subflows may have to wait until missing earlier data arrives over a slower subflow.

**Why:** The receiver must preserve the original ordered byte stream expected by the application.

**Cost or caveat:** Reordering can occupy receive-buffer space and delay application delivery. The required buffer depends on path rates, delay differences and the amount of data in flight; there is no single universal buffer formula.

**How to check:** Draw a timeline with a fast and a slow path. Compare arrival order with DSN order and observe how much out-of-order data accumulates before the missing bytes arrive.

### Q52. How does coupled congestion control (LIA) work, what is its goal, and what does it give up compared with running CUBIC independently on each subflow?

**What:** Linked Increase Algorithm (LIA) couples congestion-window growth across MPTCP subflows rather than treating every subflow as an entirely independent TCP connection.

**Why:** Its design aims to use available paths while avoiding unfairly taking excessive capacity from competing single-path TCP flows, particularly at shared bottlenecks.

**Cost or caveat:** Coupling can limit the throughput that independently running congestion controllers might achieve. LIA's behaviour also depends on the subflows' RTTs and congestion windows.

**How to check:** Read RFC 6356 and inspect the congestion-control configuration of the actual Linux kernel. Do not assume every MPTCP implementation uses LIA by default.

### Q72. Give each evidence-backed reason adoption stayed limited (middleboxes, OS and application support, little gain for short flows, scheduler complexity, QUIC). Name the evidence and one counter-argument for each.

**What:** MPTCP adoption faces several practical barriers: middlebox compatibility, limited operating-system and application support, small benefits for short transfers, scheduling complexity and competition from QUIC.

**Why:** A protocol's technical ability to use multiple paths does not automatically make it easy or worthwhile to deploy across the Internet.

**Cost or caveat:** These are context-dependent barriers, not proof that MPTCP is unsuccessful everywhere. Controlled deployments, such as environments where one operator controls both endpoints, can avoid many compatibility problems.

**How to check:** Use deployment studies, RFC 8041 and documented deployments. For each claim, identify the study's measurement method and a counterexample or limitation.

### Q74. Why might someone still choose MPTCP over MP-QUIC for a legacy TCP application, and what would they give up?

**What:** MPTCP can support an existing TCP application through a compatible socket interface without requiring the application to implement QUIC.

**Why:** This can make MPTCP attractive when legacy applications need multipath and the operating system and network support it.

**Cost or caveat:** MPTCP depends on TCP-option compatibility and kernel support. Choosing it may also mean giving up QUIC's user-space deployment flexibility and stream multiplexing model.

**How to check:** Compare the application-facing interfaces and deployment requirements of Linux MPTCP and the chosen QUIC implementation. Verify whether the application can use MPTCP without source-code changes.

---

## Section 2 - Kaushal: QUIC and Multipath QUIC (10 Questions)

### Q75. Why was QUIC created? Which problems of TCP with TLS and HTTP/2 does it address: handshake latency, head-of-line blocking, ossification, slow evolution?

**What:** QUIC is a secure transport protocol built over UDP. It integrates TLS 1.3, supports multiple streams and implements transport behaviour in user space.

**Why:** It was designed to reduce connection-establishment delays, avoid TCP-level connection-wide stream blocking, and allow transport evolution without requiring changes to the operating-system TCP stack.

**Cost or caveat:** User-space processing and encryption can introduce CPU overhead. QUIC still has ordering and flow-control constraints within individual streams.

**How to check:** Read RFC 9000, RFC 9001 and RFC 9002. Compare the TCP-plus-TLS handshake with QUIC's integrated handshake and stream model.

### Q79. What is a QUIC stream, and why multiplex several inside one connection? How does a stream ID show who opened it and whether it is bidirectional?

**What:** A QUIC stream is an independently ordered byte stream within a QUIC connection. Multiple streams can carry application data concurrently.

**Why:** If data on one stream is lost, other streams can continue delivering data, provided connection-level congestion and flow control allow it.

**Cost or caveat:** Data within an individual stream must still be delivered in order. A single large stream can therefore experience stream-level head-of-line blocking.

**How to check:** Read RFC 9000's stream-ID definition. Inspect the stream ID bits to identify initiator and direction, and examine STREAM frames in a QUIC trace.

### Q81. Packet numbers never repeat. How does that remove retransmission ambiguity, and how is lost stream data recovered when the packet number is not reused?

**What:** QUIC assigns a new packet number to every transmitted packet. If a packet containing stream data is lost, the data can be sent again in a new packet with a new packet number.

**Why:** The sender can distinguish a newly transmitted packet from a retransmission of previously sent information. This avoids TCP's retransmission ambiguity in packet-number-based RTT measurement.

**Cost or caveat:** Packet numbers identify transmissions, not application data. The sender must track which frames or data ranges still need delivery.

**How to check:** Read RFC 9000 and RFC 9002. In a trace, compare the packet numbers of the original and recovered transmissions and check whether the stream offset is repeated.

### Q87. How does connection migration work, and how do PATH_CHALLENGE and PATH_RESPONSE validate a new path? Why validate before using it fully?

**What:** QUIC can maintain a connection when an endpoint's network address changes. Path validation uses PATH_CHALLENGE and PATH_RESPONSE frames to test whether the peer can receive and respond on the new path.

**Why:** This supports mobility and NAT rebinding without necessarily requiring a completely new connection.

**Cost or caveat:** Migration changes the path used by a connection; it is not the same as simultaneously splitting traffic across multiple paths. Validation also adds packets and delay.

**How to check:** Read RFC 9000's connection-migration and path-validation sections. Follow the challenge and matching response in a trace.

### Q90. Why does QUIC avoid TCP's connection-wide HOL blocking? Give the cases where data of one stream is still held back.

**What:** QUIC keeps stream ordering separate, so loss affecting one stream does not automatically prevent delivery of data from every other stream.

**Why:** This is useful for applications such as HTTP/3, where independent requests can use different streams.

**Cost or caveat:** A stream still waits for missing earlier data within that stream. Connection-level flow control, congestion control and application scheduling can also delay several streams. QPACK can introduce its own blocking dependencies.

**How to check:** Compare a lost STREAM frame on one stream with data arriving on another. Inspect stream offsets, flow-control limits and HTTP/3/QPACK dependencies.

### Q93. Connection migration already exists in QUIC, so why is a multipath extension needed? What does migration deliberately not allow?

**What:** Connection migration allows a QUIC connection to move from one network path to another. A multipath extension aims to allow one connection to use multiple paths concurrently.

**Why:** Migration supports continuity when an address changes, while multipath can potentially aggregate capacity, provide redundancy or distribute traffic across paths.

**Cost or caveat:** Multipath introduces additional complexity in path management, packet numbering, acknowledgements, congestion control and scheduling. Migration alone does not provide simultaneous multipath transmission.

**How to check:** Compare RFC 9000's migration model with the specific multipath QUIC draft revision being studied. Check which mechanisms the implementation actually supports.

### Q94. What is a "path" in the multipath draft? Why is it defined by a path ID rather than the 4-tuple, and why would two paths share one 4-tuple?

**What:** In the multipath draft, a path is identified by a path ID rather than being identified only by its network 4-tuple.

**Why:** Network addresses and ports can change due to NAT rebinding or migration. A path identifier provides a protocol-level identity that is not simply tied to one fixed address-and-port combination.

**Cost or caveat:** The path-ID mechanism requires additional state and coordination. Exact semantics must be checked against the draft revision being implemented.

**How to check:** Read the path definition and path-management sections of the chosen multipath QUIC draft. Do not infer the behaviour from an older research implementation.

### Q97. Why did the draft choose one packet number space per path instead of one shared space? What does each choice do to loss detection, ACKs and RTT estimation?

**What:** The draft design uses separate packet-number spaces for individual paths.

**Why:** Packet numbering and acknowledgement information can be interpreted in the context of the path that carried the packets, helping loss detection and RTT estimation remain path-specific.

**Cost or caveat:** Multiple packet-number spaces add state and complexity. ACK handling must account for the relationship between the path on which data was sent and the path on which an acknowledgement returns.

**How to check:** Read the packet-number and ACK sections of the exact draft revision. Trace packet numbers and ACK information separately for two paths.

### Q108. What is a PATH_ACK, and why can the ACK for path A's packets travel on path B?

**What:** PATH_ACK is an acknowledgement mechanism in the multipath QUIC draft for acknowledging packets associated with a particular path.

**Why:** The design can allow acknowledgement information to return over a different available path, which may remain usable when the original path is impaired.

**Cost or caveat:** The return path may have a different RTT. Therefore, the time between sending a packet and receiving its acknowledgement may not represent the forward path's RTT accurately.

**How to check:** Inspect the draft's PATH_ACK definition and trace the path identifier associated with the acknowledged packets separately from the path carrying the ACK.

### Q110. Why is congestion control state kept per path, and which single-path rule in RFC 9002 (reset on migration) no longer applies?

**What:** A multipath implementation needs congestion information such as RTT, congestion window and pacing state for individual paths.

**Why:** Different paths can have different capacities, delays and congestion conditions. Treating them as identical would make it difficult to control traffic appropriately.

**Cost or caveat:** Independent per-path controllers may be unfair when paths share a bottleneck. The multipath draft does not automatically provide a universal coupled congestion-control algorithm.

**How to check:** Compare RFC 9002's single-path migration behaviour with the congestion-control section of the selected multipath draft. Inspect the implementation's actual per-path state.

---

## Section 3 - Pratik: Methods, Tools and End-to-End Integration (10 Questions)

### Q135. What does Mininet do (namespaces, virtual Ethernet pairs, one shared kernel)? What does that mean for MPTCP, which needs kernel support, and for QUIC, which runs as user-space programs?

**What:** Mininet creates virtual network hosts using Linux network namespaces and connects them using virtual Ethernet pairs. These hosts share the machine's Linux kernel.

**Why:** It allows a controlled network topology to be emulated on one machine, making it useful for repeatable networking experiments.

**Cost or caveat:** Because hosts share one kernel, kernel-level features such as MPTCP must be supported by that kernel. QUIC applications can run as user-space programs, but CPU contention and virtualisation effects can distort measurements.

**How to check:** Inspect the Mininet topology, kernel version and MPTCP availability. Confirm that each QUIC endpoint runs the intended implementation and that the virtual interfaces are configured as expected.

### Q139. What does Wireshark show for MPTCP and for QUIC? Why is QUIC's payload invisible, and what do SSLKEYLOGFILE and qlog add?

**What:** Wireshark can decode visible MPTCP options and relevant TCP information. QUIC packet metadata and some headers are visible, but protected QUIC contents are encrypted.

**Why:** QUIC encrypts transport information to reduce middlebox interference and protocol ossification. Decryption secrets and structured logs can provide additional debugging visibility.

**Cost or caveat:** A packet capture alone may not reveal encrypted stream contents or all transport decisions. Key logs must be handled carefully because they can expose session data.

**How to check:** Inspect MPTCP options in a capture. For QUIC, use `SSLKEYLOGFILE` where supported for decryption and qlog for structured events such as packet transmission, acknowledgements and loss.

### Q140. List the limits of emulation: no real middleboxes, perfectly stable links, CPU contention on one machine, virtualisation jitter, a single shared kernel. Which of your conclusions survive them?

**What:** Emulation provides controlled network conditions but does not reproduce every property of a real Internet or mobile network.

**Why:** It is useful for isolating variables and repeating experiments under known conditions.

**Cost or caveat:** Results may not generalise to real middleboxes, wireless variability, independent machines or different kernel and CPU environments.

**How to check:** Document the topology, kernel, software versions, link settings and host load. Classify conclusions as directly observed in the emulation, supported by published evidence or only hypothesised for real networks.

### Q146. Which baselines do you need (single-path TCP, single-path QUIC, MPTCP with one subflow, best single path, sum of paths), and what does each one tell you?

**What:** Baselines provide reference measurements for interpreting multipath performance.

- **Single-path TCP:** Reference for ordinary TCP performance.
- **Single-path QUIC:** Reference for ordinary QUIC performance.
- **MPTCP with one subflow:** Helps isolate multipath-related overhead from the MPTCP implementation.
- **Best single path:** Shows the strongest individual path available.
- **Sum of path capacities:** Gives a theoretical capacity reference when considering aggregation.

**Why:** Without baselines, a higher throughput number does not establish that multipath aggregation caused the improvement.

**Cost or caveat:** The sum of path capacities is not necessarily achievable. Shared bottlenecks, protocol overhead, scheduling and congestion control can prevent it.

**How to check:** Run comparable workloads under each baseline with the same path conditions, application data size and measurement method.

### Q153. What is the difference between multipath enabled and multipath verified? List the evidence you capture for each protocol before trusting a number.

**What:** Multipath enabled means the operating system or implementation is configured to support multipath. Multipath verified means evidence shows that the tested connection actually established and used more than one path.

**Why:** A benchmark can appear to be a multipath result even when traffic travelled over only one path.

**Cost or caveat:** Configuration settings alone do not prove that a second path carried application data.

**How to check:**

- **MPTCP:** Inspect `ss -M`, `ip mptcp monitor`, interface counters and Wireshark subflow information.
- **MP-QUIC:** Use implementation logs or qlog and packet captures to establish that multiple paths were opened and carried data.

Save the evidence with the benchmark results.

### Q154. Two paths give the same throughput as one. In what order do you debug it?

**What:** Equal throughput may mean the second path was not used, or that using it did not increase useful application delivery.

**Why:** The cause must be identified before concluding that the protocol cannot aggregate bandwidth.

**Cost or caveat:** Throughput alone cannot distinguish a setup failure from a scheduling, congestion-control or application bottleneck.

**How to check:**

1. Verify that multipath is enabled.
2. Verify that a second path or subflow was established.
3. Confirm that the second path actually carries data.
4. Check routing, endpoint configuration and address reachability.
5. Inspect the scheduler and congestion-control configuration.
6. Check whether both paths share a bottleneck.
7. Check receive buffers, send buffers and application limits.
8. Repeat the measurement and compare against the single-path baselines.

### Q157. Sir asks you to set up MPTCP from scratch. List the commands in order and what you check after each.

**What:** A defensible setup requires kernel support, MPTCP configuration, endpoint configuration, correct routing and verification of actual subflows.

**Why:** Each stage can fail independently. Checking after every stage prevents a configuration error from being mistaken for a protocol-performance result.

**Cost or caveat:** Exact commands and defaults depend on the Linux distribution, kernel and path-manager configuration. The following is a conceptual order, not a universal copy-paste script.

**How to check:**

1. Check the kernel version and MPTCP support.
2. Check the MPTCP enable setting.
3. Configure and inspect the network interfaces and IP addresses.
4. Configure source-based routing for the intended paths.
5. Configure MPTCP endpoints and their flags.
6. Set or inspect subflow and address limits.
7. Start the server and client using an MPTCP-capable socket or suitable tool.
8. Inspect `ss -M` and `ip mptcp monitor`.
9. Check per-interface counters and packet captures.
10. Run a benchmark only after confirming that the second subflow carries data.

### Q158. Sir asks you to explain a benchmark result. How do you decide whether the cause is the protocol, the implementation or the setup?

**What:** A measured result can be affected by protocol design, implementation choices or experimental configuration.

**Why:** A comparison is only defensible when these possible causes are separated as far as possible.

**Cost or caveat:** It may not be possible to isolate every factor completely, especially when comparing a kernel implementation with a user-space implementation.

**How to check:**

- **Protocol:** Identify a mechanism specified by the protocol that could explain the result.
- **Implementation:** Check the scheduler, congestion control, buffering, pacing, CPU use and software version.
- **Setup:** Check topology, routing, bandwidth, delay, loss, MTU, queue discipline and whether multipath was verified.
- **Evidence:** Repeat runs, inspect captures and logs, compare baselines and document remaining uncertainty.

### Q298. Trace a 1 MB upload over MPTCP from the application's `write()` to the receiving application's `read()`. Name every buffer, every sequence number, every ACK and every timer on the way.

**What:** The application writes bytes to an MPTCP socket. The sender buffers and maps data into the connection-level data sequence space, then transmits it over one or more TCP subflows.

**Why:** MPTCP needs both connection-level ordering and per-subflow TCP reliability to deliver one ordered byte stream over multiple paths.

**Cost or caveat:** The trace must distinguish TCP subflow sequence numbers and ACKs from MPTCP data sequence numbers and Data ACKs. Exact buffer and recovery behaviour depends on the implementation.

**How to check:**

1. Application calls `write()`.
2. Data enters the sender's socket/send buffers.
3. MPTCP assigns data sequence numbers.
4. The scheduler selects a subflow.
5. DSS maps data sequence numbers to subflow sequence numbers.
6. TCP transmits segments through the IP and network layers.
7. The receiver's TCP subflow processes incoming segments and sends subflow ACKs.
8. MPTCP uses DSS mappings to reconstruct the connection-level data sequence.
9. Out-of-order data waits in receiver-side buffers until earlier bytes arrive.
10. The receiver sends Data ACK information for connection-level progress.
11. Loss may trigger TCP retransmission or MPTCP data reinjection, depending on the failure and implementation.
12. Ordered bytes are delivered to the receiving application's `read()`.

Relevant timers include TCP retransmission timers and other recovery mechanisms. Do not treat every timer as one universal MPTCP connection timer.

### Q299. Do the same for MP-QUIC, from a stream write to the receiving application's read.

**What:** The application writes data to a QUIC stream. QUIC frames the stream data, places frames into packets, protects the packets cryptographically and sends them over the selected path.

**Why:** QUIC combines reliable stream delivery, congestion control, encryption and connection management in a transport implemented over UDP.

**Cost or caveat:** The exact multipath behaviour depends on the draft revision and implementation. Packet numbers, stream offsets and path identifiers represent different kinds of state and must not be confused.

**How to check:**

1. Application writes bytes to a QUIC stream.
2. The QUIC library buffers the stream data and tracks its stream offset.
3. The library creates STREAM frames for the data.
4. Frames are placed into QUIC packets.
5. Packets receive packet numbers in the relevant packet-number space.
6. QUIC protects the packets and sends them through UDP and IP.
7. The receiver processes the packet, verifies protection and extracts frames.
8. ACK frames acknowledge received packets.
9. If stream data is lost, the sender can retransmit the data in a new packet with a new packet number and the relevant stream offset.
10. The receiver reassembles stream data in offset order.
11. Flow control and stream ordering determine when data can be delivered.
12. The receiving application reads the available ordered stream bytes.

For multipath, also trace which path carried each packet and how the selected draft handles per-path packet numbers, ACKs, congestion control and path failure.

---

## Final Revision Checklist

- [ ] I can explain all 10 MPTCP questions without notes.
- [ ] I can explain all 10 QUIC and MP-QUIC questions without notes.
- [ ] I can explain all 10 methods and integration questions without notes.
- [ ] I can draw the MPTCP handshake and its two sequence spaces.
- [ ] I can draw QUIC packet, frame and stream layering.
- [ ] I can distinguish connection migration from simultaneous multipath use.
- [ ] I can explain why multipath-enabled does not mean multipath-verified.
- [ ] I can trace one upload through both protocols.
- [ ] I can identify which claims require checking against a specific RFC, draft or implementation.

**Important:** For MP-QUIC questions, always name the draft revision or implementation being discussed. Do not present draft-specific behaviour as a universal property of every QUIC implementation.

**Next\:** Save this as `14_Cross_Training_Q29-299/Cross_Training_30_Questions.md`\.

After this, we should move to the **diagrams**, starting with the two Swamini-specific diagrams: the throughput-versus-RTT conceptual graph and the “second path hurts” timeline.



---
Powered by [ChatGPT Exporter](https://www.chatgptexporter.com)