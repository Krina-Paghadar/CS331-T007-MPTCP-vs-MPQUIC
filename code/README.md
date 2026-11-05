# Implementation and Code Notice

## 1. Explicit Statement on Repository Code

**No custom protocol code, scripts, or implementations are included in this repository.**

This project is strictly an in-depth **theoretical, architectural, and literature-based comparative study**. In accordance with academic integrity and the project guidelines:
- We did **not** write or modify any kernel modules or user-space transport stacks.
- We did **not** run an emulated or physical testbed (e.g., Mininet, NetEm, or physical multi-interface testbeds).
- We did **not** collect live empirical measurements or generate synthetic benchmark numbers.

---

## 2. Technical Reasons Why Code / Experiments Were Not Pursued

The team originally planned to deploy and evaluate an empirical testbed using Mininet on local Linux development environments. However, the team encountered foundational platform blockers that prevented reliable multipath execution:

1. **WSL2 (Windows Subsystem for Linux) Kernel Limitations:**
   The primary development machines run Microsoft Windows. The default Microsoft-provided Linux kernel for WSL2 does not enable Multipath TCP support (`CONFIG_MPTCP=y` is disabled in the stock kernel image). MPTCP v1 requires kernel-level socket layer integration, routing rules (`ip rule`), and `ip mptcp` netlink support. Rebuilding a custom WSL2 kernel with MPTCP enabled, custom virtual interfaces, and source routing policies introduces complex hypervisor bridging artifacts that distort latency and bandwidth measurements.

2. **Multipass Virtual Machine Failure:**
   To bypass WSL2 kernel limitations, the team attempted to launch Ubuntu virtual machines with modern upstream kernels (Linux 5.15+) using Canonical Multipass. However, the Multipass hypervisor driver failed to launch and initialize the virtual machine instances on the host system due to Hyper-V / virtual networking configuration conflicts.

3. **Academic Decision and Re-scoping:**
   Faced with these system-level virtualization blockers, and recognizing that troubleshooting Windows hypervisor drivers does not advance networking research objectives, the team made an intentional, principled decision: rather than investing scarce project time into debugging virtualization software or presenting fragile, unreproducible toy experiments, we re-scoped the project into a comprehensive, rigorous **first-principles comparative study of MPTCP v1 (RFC 8684) and MP-QUIC (draft-ietf-quic-multipath-21)**.

---

## 3. What We Did Instead

Rather than collecting flawed or trivial measurements, the team performed a deep, rigorous analytical study:

1. **Specification Analysis:**
   - Deconstructed **RFC 8684 (MPTCP v1)**: Handshake state machines (`MP_CAPABLE`, `MP_JOIN`), two-level sequence mapping (Data Sequence Numbers vs. Subflow Sequence Numbers), Data Sequence Signal (DSS) option formatting, subflow management (`ADD_ADDR`, `REMOVE_ADDR`, `MP_PRIO`), and fallback mechanisms (`MP_FAIL`, infinite mapping).
   - Deconstructed **draft-ietf-quic-multipath-21 (MP-QUIC)**: Multi-path negotiation parameters (`initial_max_path_id`), independent per-path Packet Number (PN) spaces, path state management (`PATH_CHALLENGE`, `PATH_RESPONSE`, `PATH_STATUS`, `PATH_ABANDON`), and `PATH_ACK` cross-path feedback semantics.

2. **Theoretical and Algorithmic Analysis:**
   - Evaluated Coupled Congestion Control algorithms (**RFC 6356 / LIA**, OLIA, BALIA) to understand how multipath achieves resource pooling without harming single-path TCP flows at shared bottlenecks.
   - Analyzed packet scheduling algorithms (Lowest-RTT-First / MinRTT, BLEST, ECF, Redundant) to understand Head-of-Line (HOL) blocking and receive-window collapse under path delay heterogeneity.

3. **Published Empirical Literature Review:**
   - Synthesized peer-reviewed measurements from **CoNEXT 2017** (*Multipath QUIC: Design and Evaluation*) and **MultipathTester (MNM 2019)** (*Comparing MPTCP and MPQUIC in Mobile Environments*), evaluating their testbed topologies, workloads, and findings under their documented experimental conditions.
   - Evaluated real-world Internet adoption studies (e.g., arXiv:2106.07351) documenting middlebox interference rates, TCP option stripping, and mobile deployment architectures (e.g., Apple Siri / Private Relay, 3GPP ATSSS).

4. **Structured Cross-Training:**
   - Formulated a 323-question foundational curriculum covering transport fundamentals, MPTCP design, QUIC mechanics, MP-QUIC draft-21, congestion control theory, and application Quality of Experience (QoE).
   - Executed structured teach-backs and cross-examination drills to ensure every team member can defend every architectural mechanism from first principles.

