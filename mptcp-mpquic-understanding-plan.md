# MPTCP vs MP-QUIC: Understanding Plan, 21 Oct – 2 Nov 2026

**Team:** Krina, Kaushal, Swamini, Pratik  
**Goal:** answer any "why this, why not that" question about both protocols from first principles, and know where your knowledge ends.  
**Real deadline:** 4 Nov. This plan ends on 2 Nov; 3 and 4 Nov are buffer with no new material.  

---

## 1. Scope for now

- **In scope:** understanding. Every mechanism, the reason it exists, what it costs, what the alternatives were, and what the research record says.
- **Parked:** running anything (Mininet, NetEm, iperf3, benchmarks, building QUIC stacks). The tool and experiment questions (Part 8) stay in the bank as theory, because Sir can still ask what a tool does or why a setup is valid. Hands-on work sits on the parked list at the end of this file; start it only if you finish early.
- **The questions are the test, not the syllabus.** Reading only the questions will leave holes. Section 7 lists what to read and which general concepts you must be comfortable with even though no question names them.
- **The bank is meant to be an autopsy.** It has 323 questions (Q1–Q205 from before, Q206–Q323 added) and a blank section at the end for your own additions, so you can show Sir which questions you added.

## 2. Ground rules

1. Every answer uses four beats: **what it is, which problem it exists to solve, what it costs, how you would check it.**
2. Keep "what the specification says" apart from "what a particular build does". Say which one every time.
3. A claim is finished only when you can name its evidence: an RFC or draft section, a paper, or the honest words "not verified".
4. MPTCP and MP-QUIC get equal time. The TA noted the earlier work leaned towards MP-QUIC.
5. Never repeat a command, number or diagram you cannot explain line by line.
6. Your own block is Tier 1 for you. The **cross-training set** in section 6 is Tier 1 for everyone.

## 3. Facts to keep straight

Carried over from the earlier version of this plan (checked 21 Oct 2026). Re-check each one before it goes into a report or an answer.

- **MP-QUIC is not an RFC.** The current document is draft-ietf-quic-multipath-21 (17 Mar 2026), in the RFC Editor queue at the time of checking. One blog says "RFC 9443"; the datatracker showed no number, so do not repeat it.
- **Drafts drift.** Early drafts used `enable_multipath` or `initial_max_paths`; the current one uses `initial_max_path_id`, `PATH_ACK`, `PATH_ABANDON` and one packet number space per path. Always say which draft you mean.
- **Linux MPTCP** has been upstream since v5.6 and speaks MPTCP v1 (RFC 8684) only. Older papers mostly used the out-of-tree fork (v0.96, kernel 5.4), so their numbers are not like-for-like with today's kernel.
- **The 2017 MPQUIC** was a research fork of quic-go on a pre-IETF QUIC version. At the time of checking, mainline quic-go had no multipath.
- **quiche** multipath support appeared only in a blog post; picoquic lists support for the evolving draft. Unconfirmed.
- **MPTCP adoption:** middleboxes mishandle TCP options, scans show false positives from hosts that echo options, and Apple uses MPTCP for system services with a small share of traffic.

## 4. Learning order

Each person studies their own block in parallel, but the order below is the order in which the team's understanding should build, and it is the order of the teach-backs.

| Step | Topic | Parts |
| --- | --- | --- |
| 1 | Why multipath exists and what it costs | 1 |
| 2 | TCP, loss recovery, congestion control, HOL blocking, plus the deeper transport foundations | 2, 12 |
| 3 | MPTCP from handshake to teardown, Linux implementation, adoption | 3, 4, 13 |
| 4 | QUIC fundamentals, then multipath QUIC. Learn MPTCP first: several MP-QUIC design choices are direct answers to MPTCP's problems | 5, 14, 6, 15 |
| 5 | Compare the two, and the congestion-control, fairness and scheduling theory underneath | 7, 16 |
| 6 | Research, applications and recommendations | 9, 17, 10, 18 |
| 7 | Methods and tools as theory, and end-to-end integration | 8, 19 |
| 8 | "Why not X" and viva curveballs | 11, 20, 21 |

