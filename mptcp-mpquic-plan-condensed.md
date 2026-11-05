# MPTCP vs MP-QUIC: Condensed Understanding Plan

**Team:** Kaushal, Pratik, Krina, Swamini  
**Deadline:** 4 Nov 2026. Sessions run on whichever days we are free; 4 Nov is buffer.  
**Goal:** understand both protocols well enough to answer "why this, why not that" questions with confidence, not memorise answers just before submission.  
**Replaces:** the 13-day schedule in the original plan. The full question bank is unchanged and stays in the original file as reference.  

---

## 1. How this plan works

- **Four sessions, about 3–3.5 hours each.** Two are together, one is solo, one is a mock viva. Schedule them on whatever days suit everyone.
- **A 30-minute habit on days without a session.** Sir asked for at least half an hour of real understanding rather than cramming. This habit is where that happens.
- **Workload follows capacity.** From most to least available time: Kaushal, Pratik, Krina, Swamini. Blocks are sized to match. Everyone still owns something, teaches it, and answers the shared core.
- **The bank shrinks to a must-do list.** Anything not listed below is reference only. Use it if a gap points there.

## 2. Ground rules (kept from the original)

1. Every answer uses four beats: **what it is, which problem it solves, what it costs, how you would check it.**
2. Keep "what the specification says" apart from "what a particular build does". Say which one every time.
3. Every claim names its evidence: an RFC or draft section, a paper, or the honest words "not verified". The TA's earlier comment means Sir will probe exactly here.
4. Equal weight for MPTCP and MP-QUIC.
5. Never repeat a command, number or diagram you cannot explain line by line.

## 3. Facts to keep straight

- **MP-QUIC is not an RFC.** The current document is draft-ietf-quic-multipath-21 (17 Mar 2026). Ignore the "RFC 9443" blog claim.
- **Name the draft.** Older drafts used `enable_multipath` or `initial_max_paths`; draft-21 uses `initial_max_path_id`, `PATH_ACK`, `PATH_ABANDON`, and one packet number space per path.
- **Linux MPTCP** has been upstream since kernel 5.6 and speaks MPTCP v1 (RFC 8684) only. Most older papers used the out-of-tree fork (v0.96), so their numbers are not like-for-like.
- **The 2017 MPQUIC** was a research fork of quic-go on pre-IETF QUIC. Mainline quic-go had no multipath at the time of checking.
- **quiche multipath** is unconfirmed; picoquic tracks the evolving draft.
- **MPTCP adoption** is limited by middleboxes and by false positives in scans; Apple uses it for system services.

## 4. Who owns what

| Owner | Capacity | Blocks (must-do) | Read only this | Draw | Reviews |
| --- | --- | --- | --- | --- | --- |
| **Kaushal** | Highest | Q75–116 (QUIC and multipath QUIC), the QUIC side of Q117–134, and **leads the comparison** (Q133 table) | RFC 9000 (streams, connection IDs, migration, loss and ACKs), RFC 9002 overview, multipath draft-21 in full | MP-QUIC architecture: path IDs, connection IDs, packet number spaces; path-open and PATH_ABANDON timelines | Krina's cheat sheet |
| **Pratik** | High | Q135–140, Q146, Q153–158 (methods as theory); Q265–269, Q274, Q276 (congestion control, fairness, scheduling theory); **leads** Part 11 (Q191–205) and Q298–303 | Mininet and NetEm overviews, RFC 6356, then the other three cheat sheets | Side-by-side stacks (Q300) | Swamini's cheat sheet |
| **Krina** | Medium | Q29–56 (MPTCP design), Q71–74 (history and adoption), the MPTCP side of Q117–134 | RFC 8684 overview and protocol sections, RFC 6356 | MPTCP architecture with both sequence spaces; MP_CAPABLE and MP_JOIN | Kaushal's cheat sheet |
| **Swamini** | Lightest | Q159–163, Q167–168, Q171–172 (research findings); **leads** Part 10 (Q177–190) with Q281 | CoNEXT 2017 MPQUIC paper (abstract and results), MultipathTester abstract, a DASH and VoIP overview | The "second path hurts" timeline | Pratik's cheat sheet |

