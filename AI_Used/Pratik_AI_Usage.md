# Conversation Transcript: MPTCP vs MPQUIC and RFC 6356

> This file contains the user prompts and assistant responses visible in this conversation, in chronological order. Tool-internal calls and redacted tool outputs are not user prompts or assistant responses and are not included. Rich UI elements are represented in Markdown where necessary.

---

## 1. User

i am working on my computer networks project, the project is to analyze MPTCP-vs-MPQUIC, first i want to understand what mptcp is and how mptcp works and what was the origin, i don't want you to explain anything now, give me the source from where to read and i'll ask you if some explanation is needed about anythin

## 1. Assistant

For your Computer Networks project on **MPTCP vs MPQUIC**, I recommend starting with the following sources in this order. I've prioritised official IETF documents, research papers, and Linux documentation.

## 1. Origin and motivation of MPTCP

Start here to understand why MPTCP was developed and the problems it intended to solve.

**Source 1: RFC 6182 – Architectural Guidelines for Multipath TCP Development**

- <badge color="success">Start here</badge> <badge>Essential</badge>
- <Link ref="turn536652search1" title="Read RFC 6182 (Official IETF RFC)"/>
- Focus on:
  - Section 1 – Introduction
  - Section 2 – Functional Goals
  - Section 3 – Architectural Basis
  - Section 4 – Functional Decomposition
  - Section 5 – Key Design Decisions

**Source 2: Original MPTCP research – NSDI 2011**

- <Link ref="turn536652search4" title="Design, Implementation and Evaluation of Congestion Control for Multipath TCP"/>
- Authors: Damon Wischik, Costin Raiciu, Adam Greenhalgh, Mark Handley.
- Read this for the early research and implementation perspective.

## 2. How MPTCP works

**Source 3: RFC 8684 – TCP Extensions for Multipath Operation with Multiple Addresses**

- <badge color="success">Most important</badge> <badge>Essential</badge>
- <Link ref="turn478918search1" title="Read RFC 8684 (Official MPTCP Specification)"/>
- This is the current MPTCP v1 specification.
- Focus on:
  - Section 1 – Introduction
  - Section 1.2 – MPTCP in the Networking Stack
  - Section 1.3 – Terminology
  - Section 1.4 – MPTCP Concept
  - Section 3 – MPTCP Operations
  - Section 4 – Semantics of Regular TCP
  - Section 5 – Security Considerations

**Source 4: Linux Kernel MPTCP Documentation**

- <Link ref="turn478918search0" title="Linux Kernel – Multipath TCP Documentation"/>
- Particularly useful for understanding the practical implementation.
- Focus on:
  - Concepts
  - Use cases
  - Path manager
  - Packet scheduler

## 3. Historical specification

**Source 5: RFC 6824 – Original MPTCP Specification (2013)**

- <Link ref="turn478918search3" title="Read RFC 6824"/>
- This is the earlier MPTCP v0 specification.
- Read it after RFC 6182 and before RFC 8684 if you want to understand the protocol's evolution.

Note: RFC 8684 supersedes RFC 6824.

---

## Recommended reading order

| Order | Resource | Priority |
|---|---|---|
| 1 | RFC 6182 | Essential |
| 2 | RFC 8684 | Essential |
| 3 | Linux Kernel Documentation | Essential |
| 4 | RFC 6824 | Optional |
| 5 | NSDI 2011 Research Paper | Recommended |

**My suggestion:** Start with RFC 6182, then move to RFC 8684. Don't try to read every section in one sitting.

I'll keep the explanations for later. As you read, send me any paragraph, diagram, terminology, or section you find confusing, and we'll go through it in detail.

---

## 2. User

okay this is fine i got it but for my specific part in my project i also need to learn about the congestion control algorithm mentioned in this paper the coupled congestion control algorithm, rfc 6356, help me go through ti

## 2. Assistant

Absolutely. Since your specific responsibility in the project is understanding the **Coupled Congestion Control Algorithm (RFC 6356)**, let's study it in a structured way, going from the motivation to the mathematics and eventually its implementation.

I suggest we treat this almost like a small research study. I'll help you understand the concepts, but we'll also work through the equations and numerical examples so that you can explain the algorithm confidently during your project presentation.

## 1. First, get the original RFC

<row align=center gap={2}>
  <badge color="success">Primary source</badge>
  <badge>October 2011</badge>
</row>

**RFC 6356 – Coupled Congestion Control for Multipath Transport Protocols**

Authors: C. Raiciu, M. Handley, D. Wischik.

- <Link ref="turn916715search2" title="Read the complete RFC (HTML)"/>
- <Link ref="turn916715search0" title="RFC Editor official page"/>
- <Link ref="turn916715search22" title="Download PDF"/>

This RFC introduces the **Linked Increases algorithm**, which is the coupled congestion control algorithm used as the classic MPTCP congestion-control design.

## 2. How we will study it

Here is the sequence I recommend:

1. **Understanding the problem**

   Why regular TCP congestion control is insufficient when multiple subflows belong to the same connection.

2. **Three design goals**

   - Improve throughput
   - Do no harm
   - Balance congestion

3. **Understanding Linked Increases**

   How congestion windows of multiple subflows are coupled.

4. **Mathematical formulation**

   Understand Equation (1), the role of alpha, and Equation (2).

5. **Numerical examples**

   Calculate congestion-window increments for two or more subflows.

6. **Implementation**

   How the algorithm operates on ACKs and how it relates to normal TCP congestion avoidance.

7. **Limitations and evaluation**

   Resource pooling, fairness, RTT differences, and the trade-offs of Linked Increases.

## 3. What you should read first

For our first session, read only:

**RFC 6356 — Section 1: Introduction (pages 3–5).**

Pay particular attention to these questions:

1. Why is running independent TCP congestion control on every MPTCP subflow problematic?
2. What happens when two subflows share the same network bottleneck?
3. Why does this create a fairness problem for other TCP connections?
4. What are the three goals of multipath congestion control?
5. Why does the RFC couple the congestion-control loops?

Don't worry about understanding the equations yet.

**Let's follow this approach:** Read Section 1 and send me your understanding or the first paragraph you find confusing. We'll discuss it before moving to Section 3, where the actual algorithm is introduced.

One important thing: keep Section 3 open when we reach the mathematical part. That's where most of your project-specific work will be.

---

## 3. User

yeah lets get to the mathematical part, explain it in detail i can't understand fully

## 3. Assistant

Let's go through the mathematics from the ground up. I won't assume that you already understand the congestion-control equations.

Our reference is **RFC 6356, Section 3: Coupled Congestion Control Algorithm**, followed by Section 4 for implementation details.

# Part 1: Understand the variables before the equations

First, imagine an MPTCP connection using two paths:

- **One MPTCP connection**
- **Subflow 1 — Path A (Wi-Fi):** `cwnd₁ = 10 MSS`
- **Subflow 2 — Path B (Mobile network):** `cwnd₂ = 20 MSS`
- **Receiver:** Reassembles data into one MPTCP connection.

Each subflow has its own congestion window, but the congestion controller needs to consider the entire MPTCP connection.

Here are the variables used in RFC 6356:

| Variable | Meaning |
|---|---|
| \(cwnd_i\) | Congestion window of subflow \(i\) |
| \(cwnd_{total}\) | Sum of congestion windows across all subflows |
| \(MSS_i\) | Maximum Segment Size of subflow \(i\) |
| \(RTT_i\) | Smoothed Round-Trip Time of subflow \(i\) |
| \(p_i\) | Packet loss rate on subflow \(i\) |
| \(bytes\_acked\) | Newly acknowledged bytes |
| \(\alpha\) | Coupling/aggressiveness parameter |

For our example:

\[
cwnd_1=10MSS,\quad cwnd_2=20MSS
\]

Assuming equal MSS:

\[
cwnd_{total}=10+20=30MSS
\]

**Important:** `cwnd_total` is a connection-level quantity, whereas `cwnd_i` is maintained separately for each subflow.

# Part 2: Equation (1) — The actual Linked Increases algorithm

This is the most important equation in RFC 6356.

The RFC says that whenever an ACK is received on subflow \(i\), increase its congestion window by:

\[
\boxed{
\Delta cwnd_i =
\min\left(
\frac{\alpha \cdot bytes\_acked \cdot MSS_i}
{cwnd_{total}},
\frac{bytes\_acked \cdot MSS_i}
{cwnd_i}
\right)
}
\]

Let's understand why this equation has two terms.

## 2.1 First term: Multipath increase

\[
I_1 =
\frac{\alpha \cdot bytes\_acked \cdot MSS_i}
{cwnd_{total}}
\]

This is the coupled part.

Notice that it uses:

- \(\alpha\): controls the aggressiveness of the entire MPTCP connection.
- \(cwnd_{total}\): considers all subflows, not just the current one.
- \(MSS_i\): accounts for the segment size of the current subflow.

The important observation is that **the increase of one subflow depends on the congestion windows of all subflows.**

## 2.2 Second term: Normal TCP increase

\[
I_2 =
\frac{bytes\_acked \cdot MSS_i}{cwnd_i}
\]

This is essentially the standard TCP congestion avoidance increase.

For a simple example, suppose:

- \(cwnd_i=10 MSS\)
- One MSS worth of data is acknowledged.
- \(bytes\_acked=MSS\).

Then:

\[
I_2=\frac{MSS\times MSS}{10MSS}
\]

\[
I_2=0.1MSS
\]

This is the normal TCP additive increase, expressed in bytes.

## 2.3 Why does the algorithm take MINIMUM?

This is extremely important.

\[
\Delta cwnd_i=\min(I_1,I_2)
\]

The algorithm selects whichever increase is smaller.

Why?

Because MPTCP should not become more aggressive on an individual path than a normal TCP connection operating under comparable conditions.

This is called the **Do No Harm** property.

For example:

- Normal TCP would increase the window by 0.1 MSS.
- The coupled algorithm calculates an increase of 0.05 MSS.

The actual increase is:

\[
\min(0.05,0.1)=0.05MSS
\]

It takes the smaller value.

---

# Part 3: Let's calculate Equation (1) with actual numbers

Consider an MPTCP connection with two subflows.

Assume:

| Parameter | Subflow 1 | Subflow 2 |
|---|---:|---:|
| cwnd | 10 MSS | 20 MSS |
| MSS | 1000 bytes | 1000 bytes |
| RTT | 100 ms | 200 ms |

Therefore:

\[
cwnd_{total}=10000+20000=30000\text{ bytes}
\]

For this example, assume:

\[
\alpha=1.2
\]

And one MSS worth of data is acknowledged:

\[
bytes\_acked=1000
\]

### Calculation for Subflow 1

First term:

\[
I_1=\frac{1.2\times1000\times1000}{30000}
\]

\[
I_1=40\text{ bytes}
\]

Second term:

\[
I_2=\frac{1000\times1000}{10000}
\]

\[
I_2=100\text{ bytes}
\]

Therefore:

\[
\Delta cwnd_1=\min(40,100)
\]

\[
\boxed{\Delta cwnd_1=40\text{ bytes}}
\]

### Calculation for Subflow 2

First term:

\[
I_1=\frac{1.2\times1000\times1000}{30000}
=40\text{ bytes}
\]

Second term:

\[
I_2=\frac{1000\times1000}{20000}
=50\text{ bytes}
\]

Therefore:

\[
\Delta cwnd_2=\min(40,50)
\]

\[
\boxed{\Delta cwnd_2=40\text{ bytes}}
\]

For these particular values, both subflows receive the same window increase per acknowledged MSS.

But this is not always the case. The minimum operation can cause different increases on different subflows.

Also, these are per-ACK increases, not per-RTT increases.

# Part 4: Equation (2) — Where does alpha come from?

Now we come to the second important equation.

You might be wondering:

**Who decides the value of alpha? Is it fixed? Does the sender choose it randomly?**

Neither. The algorithm calculates alpha dynamically based on the congestion windows and RTTs of all subflows.

RFC 6356 gives:

\[
\boxed{
\alpha =
cwnd_{total}
\frac{
\displaystyle\max_i\left(\frac{cwnd_i}{RTT_i^2}\right)
}{
\displaystyle\left(\sum_i\frac{cwnd_i}{RTT_i}\right)^2
}
}
\]

Let's break this down.

## 4.1 Understanding the numerator

\[
\max_i\left(\frac{cwnd_i}{RTT_i^2}\right)
\]

For every subflow, calculate:

\[
\frac{cwnd_i}{RTT_i^2}
\]

Then take the maximum.

The algorithm uses this to represent the strongest reference path in the mathematical model.

A path with a larger congestion window and smaller RTT can generally support a higher sending rate.

## 4.2 Understanding the denominator

\[
\left(\sum_i\frac{cwnd_i}{RTT_i}\right)^2
\]

For every subflow:

1. Divide its congestion window by its RTT.
2. Add the results for all subflows.
3. Square the resulting sum.

Notice that:

\[
\frac{cwnd_i}{RTT_i}
\]

is approximately the sending rate of subflow \(i\), assuming the congestion window is fully utilized.

Therefore, the denominator accounts for the aggregate sending rate of the multipath connection.

## 4.3 Understanding the complete equation

The complete equation combines:

- Total congestion window.
- Performance of the best individual path.
- Aggregate sending rate of all paths.

The result is alpha, which controls how aggressively the coupled algorithm increases the windows.

A larger alpha generally means a more aggressive increase, while a smaller alpha means a more conservative increase.

However, remember that Equation (1) also contains the minimum operation. So alpha alone does not determine the actual increase.

---

# Part 5: Calculate alpha using our previous example

Let's reuse our two subflows.

| Parameter | Subflow 1 | Subflow 2 |
|---|---:|---:|
| cwnd | 10,000 bytes | 20,000 bytes |
| RTT | 100 ms | 200 ms |
| MSS | 1,000 bytes | 1,000 bytes |

Therefore:

\[
cwnd_{total}=30000
\]

Convert RTT into seconds:

\[
RTT_1=0.1,\qquad RTT_2=0.2
\]

**Step 1: Calculate the numerator.**

For subflow 1:

\[
\frac{10000}{0.1^2}=1,000,000
\]

For subflow 2:

\[
\frac{20000}{0.2^2}=500,000
\]

Take the maximum:

\[
\max(1000000,500000)=1000000
\]

**Step 2: Calculate the denominator.**

\[
\sum_i\frac{cwnd_i}{RTT_i}
\]

\[
=\frac{10000}{0.1}+\frac{20000}{0.2}
\]

\[
=100000+100000
\]

\[
=200000
\]

Square it:

\[
(200000)^2=40000000000
\]

**Step 3: Calculate alpha.**

\[
\alpha=30000\times
\frac{1000000}{40000000000}
\]

\[
\boxed{\alpha=0.75}
\]

One correction to our earlier numerical illustration: we used 1.2 as a hypothetical alpha. For the actual windows and RTTs in that example, Equation (2) gives 0.75. We should use 0.75 when combining the two equations.

## 5.1 Now put alpha back into Equation (1)

For both subflows, we had:

\[
bytes\_acked=1000
\]

\[
MSS=1000
\]

\[
cwnd_{total}=30000
\]

First term:

\[
I_1=\frac{0.75\times1000\times1000}{30000}
\]

\[
I_1=25\text{ bytes}
\]

For subflow 1, the normal TCP increase is 100 bytes.

\[
\Delta cwnd_1=\min(25,100)=25
\]

For subflow 2, the normal TCP increase is 50 bytes.

\[
\Delta cwnd_2=\min(25,50)=25
\]

Thus, for this ACK:

| Subflow | Coupled increase | TCP increase | Actual increase |
|---|---:|---:|---:|
| 1 | 25 bytes | 100 bytes | 25 bytes |
| 2 | 25 bytes | 50 bytes | 25 bytes |

This demonstrates how the two equations work together:

- Equation (2) calculates alpha.
- Equation (1) uses alpha to calculate the actual congestion-window increase.

# Part 6: Why does the algorithm use RTT?

Consider:

- Subflow 1 has RTT = 50 ms.
- Subflow 2 has RTT = 200 ms.

Even if both have the same congestion window, Subflow 1 can complete more round trips in the same amount of time.

Since congestion-window growth happens as ACKs arrive, the RTT influences how quickly the window grows over time.

This is why RTT appears in Equation (2).

**An important distinction:** The variable \(p_i\), the packet loss rate, is defined in RFC 6356, but it does not appear explicitly in Equation (2). Loss affects congestion-window behaviour through the TCP congestion-control process, while alpha is calculated from the current congestion windows and RTTs.

# Part 7: What happens when packet loss occurs?

So far, we've only discussed increasing congestion windows.

What happens when a packet is lost?

RFC 6356 makes an important design decision.

It modifies the TCP additive-increase mechanism but retains standard TCP behaviour for:

- Slow start
- Fast retransmit
- Fast recovery
- Multiplicative decrease

In other words:

| Event | Behaviour |
|---|---|
| ACK received during congestion avoidance | Coupled increase |
| Packet loss detected | Standard TCP loss response |
| Fast retransmit | Standard TCP |
| Fast recovery | Standard TCP |
| Slow start | Standard TCP |

This means Linked Increases couples the increase of the subflows, but does not fully couple their decrease.

This is also why the algorithm is not perfect resource pooling. The RFC discusses this limitation in Section 5.

# Part 8: How does the complete algorithm execute?

1. Receive an ACK on subflow `i`.
2. Check the congestion-control state.
3. During congestion avoidance, calculate the increase using Equation (1) and alpha.
4. Update the congestion window.
5. If packet loss is detected, use the standard TCP loss response.
6. Continue transmission.

One implementation detail: RFC 6356 recommends that alpha be maintained as a connection-level variable, rather than recalculated on every ACK. It can be recalculated on loss and approximately once per RTT. See Section 4.1.

# Part 9: Test your understanding

[Practice quiz omitted from this transcript as requested.]

---

## 4. User

yes, first about alpha, where does this alpha comes from and what is the significance of this in actual real world

## 4. Assistant

This is probably the most important conceptual question in RFC 6356. Once you understand **where alpha comes from and why it exists**, Equation (2) will stop looking like an arbitrary mathematical formula.

Let's approach it from the real-world networking problem first, and then derive the equation.

# 1. Why do we need alpha in the first place?

Imagine you're downloading a large file using MPTCP.

Your laptop has two network connections:

- Wi-Fi: 50 Mbps
- Mobile data: 20 Mbps

MPTCP creates two TCP subflows and can transmit data through both.

Now imagine that both connections are available and neither has a shared bottleneck.

Ideally, you would like to use both connections and achieve approximately:

\[
50+20=70\text{ Mbps}
\]

But there's a problem.

**How aggressively should MPTCP increase its congestion windows?**

Consider two extreme situations.

### Situation A: Too aggressive

Suppose MPTCP increases both congestion windows exactly as if they were independent TCP connections.

If both paths share a common bottleneck, your one application could occupy the bandwidth of two TCP connections, while another application using ordinary TCP gets only one TCP share.

This is unfair to other users.

### Situation B: Too conservative

Suppose MPTCP behaves like just one ordinary TCP connection, even when it has two independent paths.

Then it might fail to use the additional capacity available through the second path.

You're wasting network resources.

So we need something between these two extremes.

**The balancing problem**

- **Independent TCP behaviour — Too aggressive:** Can take more than a fair share when paths share a bottleneck.
- **Single TCP-like behaviour — Potentially conservative:** May fail to exploit additional independent path capacity.
- **Coupled congestion control — Desired behaviour:** Uses multiple paths while maintaining TCP fairness.

This is exactly the problem RFC 6356 addresses.

# 2. What exactly is alpha?

Alpha is a dynamically calculated parameter that controls how aggressively the MPTCP connection increases its congestion windows.

Think of alpha as a **throttle for the aggregate congestion-window growth**.

- Higher alpha → potentially faster growth.
- Lower alpha → slower growth.
- Alpha is recalculated using the observed congestion windows and RTTs of the available paths.

But there is an important distinction:

Alpha is not a bandwidth measurement, not a packet-loss probability, and not a fixed configuration value.

It is a control parameter calculated to achieve a particular throughput objective.

## 3. What is the actual objective of alpha?

This is the key sentence in RFC 6356:

The aggregate throughput of an MPTCP connection should be equal to the throughput that a regular TCP connection would achieve on the best available path.

In mathematical terms:

\[
\boxed{R_{MPTCP}=R_{TCP,best}}
\]

This is the target used to derive alpha.

Why the best path?

Because this achieves the RFC's first design goal: **Improve Throughput**.

MPTCP should not perform worse than using just the best available path.

And because the increase equation also has the minimum operation, it protects the second goal: **Do No Harm**.

There is an interesting nuance here: this is the RFC's target under its congestion-control model, not a promise that every real-world transfer will always achieve exactly that throughput.

# 4. Where does the mathematical formula come from?

Now let's derive the intuition behind Equation (2).

We know the desired condition:

\[
R_{MPTCP}=R_{TCP,best}
\]

First, understand how we estimate throughput.

For subflow \(i\), its approximate sending rate is:

\[
R_i=\frac{cwnd_i}{RTT_i}
\]

Therefore, aggregate MPTCP sending rate is approximately:

\[
\boxed{
R_{MPTCP}=\sum_i\frac{cwnd_i}{RTT_i}
}
\]

For a regular TCP connection, the best available path is the one that provides the highest TCP throughput under its congestion conditions.

The RFC's derivation uses the congestion-window growth and loss behaviour of TCP to establish the equivalent aggressiveness of MPTCP.

The resulting expression is:

\[
\boxed{
\alpha =
cwnd_{total}
\frac{
\max_i\left(\frac{cwnd_i}{RTT_i^2}\right)
}{
\left(\sum_i\frac{cwnd_i}{RTT_i}\right)^2
}
}
\]

The RFC explicitly states that this is obtained by equalizing the multipath flow's rate with the rate of TCP on the best path, then solving for alpha.

Let's understand what each part is doing.

### A. The term inside the maximum

\[
\max_i\left(\frac{cwnd_i}{RTT_i^2}\right)
\]

For every path, calculate its congestion window divided by its RTT squared.

The square of RTT matters because congestion-window growth and throughput are affected by how frequently the path completes round trips.

The maximum selects the strongest reference path in the RFC's mathematical model.

### B. The summation

\[
\sum_i\frac{cwnd_i}{RTT_i}
\]

This is the sum of the estimated sending rates of all subflows.

It represents the aggregate rate that MPTCP is currently attempting to achieve.

### C. The square

\[
\left(\sum_i\frac{cwnd_i}{RTT_i}\right)^2
\]

The square is part of the mathematical relationship between aggregate sending rate and congestion-window growth.

### D. The total congestion window

\[
cwnd_{total}=\sum_i cwnd_i
\]

This brings the individual congestion windows together into one connection-level quantity.

The final result adjusts the aggregate aggressiveness according to the current characteristics of all the paths.

# 5. Let's understand alpha using a real-world example

Suppose you are downloading a 1 GB file on your laptop.

You have two connections:

- **Wi-Fi:** 100 Mbps, RTT = 20 ms.
- **Mobile data:** 30 Mbps, RTT = 80 ms.

These are illustrative network conditions, not measured values.

There are two possible situations.

**Situation 1: Both connections use independent network bottlenecks.**

Wi-Fi traffic and mobile traffic can use separate available capacity.

MPTCP can exploit both paths and potentially get close to their combined throughput.

**Situation 2: Both subflows share a bottleneck.**

For example, imagine both routes eventually pass through the same constrained network link.

If MPTCP behaves like two independent TCP connections, it could take an unfairly large share of that link.

This is where coupled congestion control matters.

Alpha adjusts the increase of the congestion windows to control the aggregate aggressiveness.

The actual network will determine the resulting throughput through its capacity, RTTs, packet losses, and competing traffic.

# 6. What happens to alpha when network conditions change?

This is particularly important in a mobile environment, where Wi-Fi and cellular conditions can change continuously.

| Network change | Possible effect on alpha |
|---|---|
| One subflow's congestion window increases | Alpha is recalculated based on the new windows |
| One path's RTT increases | Its contribution to the RTT-dependent terms changes |
| One path becomes much faster | Its contribution to the best-path term may increase |
| A subflow experiences loss | Its congestion window changes, affecting alpha |
| A new subflow is established | Alpha calculation includes the new subflow |

Notice that these are not universal directions of change. The actual effect depends on all the terms in Equation (2).

**The important real-world significance:** MPTCP does not need to assume beforehand that Wi-Fi is always better than cellular or vice versa. It adapts its congestion-control aggressiveness based on observed path conditions.

# 7. A very useful mathematical observation

Let's take the simplest possible case: two identical subflows.

Assume:

\[
cwnd_1=cwnd_2=W
\]

\[
RTT_1=RTT_2=R
\]

Then:

\[
cwnd_{total}=2W
\]

The numerator becomes:

\[
\max\left(\frac{W}{R^2},\frac{W}{R^2}\right)
=\frac{W}{R^2}
\]

The denominator becomes:

\[
\left(\frac{W}{R}+\frac{W}{R}\right)^2
=\frac{4W^2}{R^2}
\]

Substituting:

\[
\alpha=2W\times
\frac{W/R^2}{4W^2/R^2}
\]

Therefore:

\[
\boxed{\alpha=\frac{1}{2}}
\]

For two identical subflows, alpha is 0.5.

For \(n\) identical subflows, the same reasoning gives:

\[
\boxed{\alpha=\frac{1}{n}}
\]

This is a particularly useful result for understanding the algorithm.

It shows that when you add identical subflows, the algorithm reduces the per-subflow coupled aggressiveness so that the aggregate increase remains comparable to one TCP flow under equivalent congestion conditions.

# 8. What should you remember for your project?

I would summarise the significance of alpha in four points:

1. **Fairness:** Prevents an MPTCP connection from being unnecessarily aggressive compared with a regular TCP connection.
2. **Throughput:** Helps MPTCP achieve at least the throughput target of TCP on its best available path.
3. **Adaptability:** Changes according to the congestion windows and RTTs of the available paths.
4. **Coupling:** Connects the congestion-control behaviour of multiple subflows into one coordinated mechanism.

One more important implementation detail: RFC 6356 Section 4.1 discusses fixed-point/integer arithmetic for computing alpha efficiently, since floating-point operations can be expensive or unavailable in kernel networking code.

# 9. Check whether you've understood the concept

[Practice question omitted from this transcript as requested.]

**My recommendation for the next step:** Let's derive Equation (2) more rigorously from the TCP congestion-window growth and packet-loss model. That will help you understand where the equation comes from rather than just memorising the formula.

---

## 5. User

i understood on the surface level what is alpha and why it is needed, but how do we actually get alpha, like how are we calculating it, is there some derivation or something for it or some pre-defined implementation, what is it

## 5. Assistant

Now we can answer your question directly, using the actual RFC rather than just interpreting alpha conceptually.

**Alpha is not predefined, manually configured, or randomly selected. It is calculated mathematically from the current network measurements.**

RFC 6356 explicitly says that a fixed alpha cannot achieve the desired throughput under every possible combination of paths. Therefore, alpha must be calculated from the observed properties of the paths.

There are two things to understand:

1. How the researchers derived the formula.
2. How an actual implementation calculates alpha.

Let's separate them.

# 1. Where did the formula originate?

The researchers started with the requirements of multipath congestion control.

In particular, they wanted the following:

\[
\text{MPTCP throughput}
=
\text{TCP throughput on best path}
\]

They already had the Linked Increases algorithm, which uses alpha to control congestion-window growth.

They then asked:

**What value of alpha would make the aggregate throughput of this algorithm equal to the throughput of a normal TCP connection on the best path?**

They mathematically solved this condition and obtained Equation (2).

So alpha is a derived parameter, not an arbitrary constant.

# 2. How is alpha actually calculated?

Suppose your MPTCP connection has three subflows.

The sender maintains information about each subflow:

| Parameter | Subflow 1 | Subflow 2 | Subflow 3 |
|---|---:|---:|---:|
| Congestion window | 10000 B | 15000 B | 8000 B |
| RTT | 20 ms | 40 ms | 80 ms |

The sender has to calculate three things:

- Total congestion window.
- Maximum value of \(cwnd_i/RTT_i^2\).
- Sum of \(cwnd_i/RTT_i\).

Then it substitutes them into Equation (2).

The actual computation is:

\[
cwnd_{total}=\sum_i cwnd_i
\]

\[
A=\max_i\left(\frac{cwnd_i}{RTT_i^2}\right)
\]

\[
B=\sum_i\left(\frac{cwnd_i}{RTT_i}\right)
\]

Finally:

\[
\boxed{\alpha=\frac{cwnd_{total}\times A}{B^2}}
\]

That's it. There is no separate machine-learning model, no optimization solver running continuously, and no external server telling MPTCP what alpha should be.

It is an arithmetic calculation using measurements already maintained by the TCP subflows.

# 3. Let's actually calculate alpha

Using the three-subflow example:

| Parameter | Subflow 1 | Subflow 2 | Subflow 3 |
|---|---:|---:|---:|
| cwnd | 10,000 B | 15,000 B | 8,000 B |
| RTT | 20 ms | 40 ms | 80 ms |

**Step 1: Total congestion window**

\[
cwnd_{total}=10000+15000+8000
\]

\[
\boxed{cwnd_{total}=33000}
\]

**Step 2: Calculate each subflow's contribution to the maximum**

\[
\frac{cwnd_1}{RTT_1^2}
=\frac{10000}{20^2}=25
\]

\[
\frac{cwnd_2}{RTT_2^2}
=\frac{15000}{40^2}=9.375
\]

\[
\frac{cwnd_3}{RTT_3^2}
=\frac{8000}{80^2}=1.25
\]

Therefore:

\[
A=\max(25,9.375,1.25)=25
\]

**Step 3: Calculate the aggregate rate term**

\[
B=\frac{10000}{20}+\frac{15000}{40}+\frac{8000}{80}
\]

\[
B=500+375+100
\]

\[
\boxed{B=975}
\]

**Step 4: Calculate alpha**

\[
\alpha=\frac{33000\times25}{975^2}
\]

\[
\alpha=\frac{825000}{950625}
\]

\[
\boxed{\alpha\approx0.8678}
\]

This is how the sender obtains alpha: it takes the current state of all the subflows, performs these calculations, and stores the resulting value.

Notice that we didn't need to know the actual link bandwidths of Wi-Fi, cellular, or Ethernet. The calculation uses the congestion-control state and RTT estimates.

# 4. Is this calculation performed continuously?

No. This is another important distinction between the mathematical algorithm and its implementation.

If the sender recalculated alpha every time an ACK arrived, that would create unnecessary computational overhead.

RFC 6356 Section 4.1 recommends:

- Maintain alpha as a per-connection variable.
- Recalculate it when a packet loss occurs.
- Otherwise, recalculate approximately once per RTT.
- Maintain the total congestion window rather than summing every subflow's window on every ACK, if desired.

# 5. Is there a predefined implementation?

Yes. RFC 6356 doesn't just provide the mathematical formula; it also explains how to implement it efficiently.

This is Section 4.1, *Computing alpha in Practice*.

The problem is that operating-system kernels generally avoid floating-point arithmetic in networking code because of performance and kernel-state constraints.

So the authors propose an integer-based approximation.

### The alpha_scale parameter

They introduce:

\[
\alpha_{scale}=512
\]

as a recommended precision parameter.

Instead of directly computing alpha with floating-point operations, the implementation scales the calculation and adjusts the congestion-window increase accordingly.

The resulting increase formula becomes:

\[
\Delta cwnd_i =
\min\left(
\frac{\alpha \cdot bytes\_acked \cdot MSS_i}
{\alpha_{scale}\cdot cwnd_{total}},
\frac{bytes\_acked\cdot MSS_i}{cwnd_i}
\right)
\]

The important distinction is that alpha_scale is an implementation precision parameter. It is not the actual alpha.

The RFC also recommends maintaining alpha as a connection-level variable and updating it approximately once per RTT or following a loss event.

# 6. Where can you find the actual derivation?

There are two documents:

**RFC 6356 — Section 3 and Section 4.1**

- <Link ref="turn337605search1" title="Official RFC 6356"/>
- Gives the final formula and practical implementation.

**NSDI 2011 Research Paper — Section 2.5: Compensating for RTT mismatch**

- <Link ref="turn555565search0" title="Design, Implementation and Evaluation of Congestion Control for Multipath TCP"/>
- This is the research paper behind the algorithm. It explains the fairness constraints, equilibrium equations, and how the authors arrive at the alpha expression.

One interesting detail: the research paper uses equilibrium congestion windows (denoted by \(\hat{w}\)) to derive the parameter. RFC 6356 then uses the current measured congestion windows as a practical approximation.

# 7. The complete picture

1. **Network observations:** `cwnd`, RTT and loss events for each subflow.
2. **Mathematical calculation:**

   \[
   \alpha=cwnd_{total}\frac{\max_i(cwnd_i/RTT_i^2)}{(\sum_i cwnd_i/RTT_i)^2}
   \]

3. **Store alpha:** Connection-level variable, updated periodically.
4. **Linked Increases:** Uses alpha to calculate each subflow's congestion-window increase.

The next step is to derive alpha from the original NSDI paper's equilibrium equations (Section 2.5), rather than simply deriving it from the final RFC formula.

That is where you will see how the TCP loss probability, additive increase, multiplicative decrease, RTT and fairness constraints lead to the final expression.

---

## 6. User

can you walk me through a numerical example of how the congestion window changes over ACKs and RTTs including different path conditions

## 6. Assistant

Yes. This is where the algorithm starts becoming interesting, because we will see how **two subflows evolve independently in time but remain mathematically coupled through alpha**.

We'll simulate an MPTCP connection with two paths, process ACKs, advance time according to their RTTs, and then introduce packet loss.

We'll use the actual Linked Increases equation from RFC 6356.

# 1. Set up our network

Imagine a laptop downloading a file using Wi-Fi and mobile data.

- **Subflow 1 — Wi-Fi**
  - RTT = 100 ms
  - Initial cwnd = 10 MSS = 10,000 bytes
- **Subflow 2 — Mobile data**
  - RTT = 200 ms
  - Initial cwnd = 20 MSS = 20,000 bytes
- MSS on both paths = 1000 bytes
- Initial total cwnd = 30,000 bytes

We will assume:

- Both subflows are already in congestion avoidance, not slow start.
- Both paths are fully utilized.
- Each ACK acknowledges one new MSS of data.
- There are no delayed ACKs or retransmissions during the initial part.
- RTTs remain constant during the simulation.

Our starting state is:

\[
cwnd_1=10000
\]

\[
cwnd_2=20000
\]

\[
cwnd_{total}=30000
\]

# 2. Calculate the initial alpha

Recall:

\[
\alpha =
cwnd_{total}
\frac{\max_i(cwnd_i/RTT_i^2)}
{(\sum_i cwnd_i/RTT_i)^2}
\]

Using RTTs in seconds:

\[
RTT_1=0.1,\qquad RTT_2=0.2
\]

Numerator:

\[
\max\left(
\frac{10000}{0.1^2},
\frac{20000}{0.2^2}
\right)
\]

\[
=\max(1000000,500000)
\]

\[
=1000000
\]

Denominator:

\[
\left(
\frac{10000}{0.1}+
\frac{20000}{0.2}
\right)^2
\]

\[
=(100000+100000)^2
\]

\[
=40000000000
\]

Therefore:

\[
\alpha=
30000\times\frac{1000000}{40000000000}
\]

\[
\boxed{\alpha=0.75}
\]

We'll initially use this alpha value.

# 3. Process the first ACK

Suppose an ACK arrives on Subflow 1.

The ACK acknowledges 1000 bytes:

\[
bytes\_acked=1000
\]

Equation (1):

\[
\Delta cwnd_i =
\min\left(
\frac{\alpha\times bytes\_acked\times MSS_i}
{cwnd_{total}},
\frac{bytes\_acked\times MSS_i}{cwnd_i}
\right)
\]

Substitute the values for Subflow 1.

**First term — Coupled increase**

\[
I_1=\frac{0.75\times1000\times1000}{30000}
\]

\[
I_1=25\text{ bytes}
\]

**Second term — Normal TCP increase**

\[
I_2=\frac{1000\times1000}{10000}
\]

\[
I_2=100\text{ bytes}
\]

Take the minimum:

\[
\Delta cwnd_1=\min(25,100)
\]

\[
\boxed{\Delta cwnd_1=25\text{ bytes}}
\]

So the new congestion window is:

\[
cwnd_1=10000+25
\]

\[
\boxed{cwnd_1=10025\text{ bytes}}
\]

# 4. What happens when ACKs keep arriving?

Remember:

- Subflow 1 has RTT = 100 ms.
- Subflow 2 has RTT = 200 ms.

Assuming the windows are fully utilized, approximately:

\[
ACKs\ per\ RTT \approx \frac{cwnd}{MSS}
\]

Therefore:

| Subflow | ACKs per RTT | Time for one RTT |
|---|---:|---:|
| Subflow 1 | 10 | 100 ms |
| Subflow 2 | 20 | 200 ms |

Subflow 1 receives ACKs twice as frequently in wall-clock time.

However, Subflow 2 has twice the initial congestion window, so it has approximately twice as many ACKs per RTT.

For a transparent hand calculation, we'll freeze alpha and the total-window denominator at their initial values during this short interval. This is a simplified approximation; a real implementation updates the window state as ACKs arrive and periodically refreshes alpha.

At the initial state, both subflows have a coupled increase of:

\[
25\text{ bytes per ACK}
\]

## 4.1 First 100 milliseconds

In 100 ms:

- Subflow 1 completes approximately one RTT and receives 10 ACKs.
- Subflow 2 completes approximately half an RTT and receives 10 ACKs.

Each ACK contributes approximately 25 bytes in our simplified calculation.

For Subflow 1:

\[
\Delta cwnd_1=10\times25=250
\]

For Subflow 2:

\[
\Delta cwnd_2=10\times25=250
\]

Our state becomes:

| Parameter | Subflow 1 | Subflow 2 |
|---|---:|---:|
| Initial cwnd | 10,000 | 20,000 |
| ACKs received | 10 | 10 |
| Total increase | +250 | +250 |
| New cwnd | **10,250** | **20,250** |

## 4.2 Next 100 milliseconds

Now consider the interval from 100 ms to 200 ms.

- Subflow 1 completes another RTT and receives another 10 ACKs.
- Subflow 2 completes its first full RTT and receives another 10 ACKs.

Therefore:

\[
\Delta cwnd_1=250
\]

\[
\Delta cwnd_2=250
\]

The resulting state:

| Parameter | Subflow 1 | Subflow 2 |
|---|---:|---:|
| cwnd at 100 ms | 10,250 | 20,250 |
| Additional ACKs | 10 | 10 |
| Additional increase | +250 | +250 |
| cwnd at 200 ms | **10,500** | **20,500** |

At 200 ms:

\[
cwnd_{total}=10500+20500
\]

\[
\boxed{cwnd_{total}=31000}
\]

This is the result of our simplified hand calculation, not an exact packet-level trace.

# 5. Now introduce packet loss on Subflow 2

Suppose that at 200 ms, the mobile network experiences congestion and a packet is lost.

Subflow 1 (Wi-Fi) does not experience any loss.

For our example, assume a Reno-style multiplicative decrease, where the congestion window is halved.

For Subflow 2:

\[
cwnd_2^{new}=\frac{20500}{2}
\]

\[
\boxed{cwnd_2^{new}=10250\text{ bytes}}
\]

Subflow 1 remains at:

\[
cwnd_1=10500
\]

The new total is:

\[
cwnd_{total}=10500+10250
\]

\[
\boxed{cwnd_{total}=20750}
\]

Our state now looks like this:

| Parameter | Subflow 1 | Subflow 2 |
|---|---:|---:|
| RTT | 100 ms | 200 ms |
| cwnd before loss | 10,500 | 20,500 |
| Loss detected? | No | Yes |
| cwnd after loss | **10,500** | **10,250** |

# 6. What happens to alpha after the loss?

Since Subflow 2's congestion window has been reduced, alpha must be recalculated.

We now have:

\[
cwnd_1=10500
\]

\[
cwnd_2=10250
\]

\[
RTT_1=0.1,\qquad RTT_2=0.2
\]

**Step 1: Numerator maximum**

\[
\max\left(
\frac{10500}{0.1^2},
\frac{10250}{0.2^2}
\right)
\]

\[
=\max(1050000,256250)
\]

\[
=1050000
\]

**Step 2: Denominator**

\[
\left(
\frac{10500}{0.1}+
\frac{10250}{0.2}
\right)^2
\]

\[
=(105000+51250)^2
\]

\[
=156250^2
\]

\[
=24414062500
\]

**Step 3: Calculate alpha**

\[
\alpha=
20750\times
\frac{1050000}{24414062500}
\]

\[
\boxed{\alpha\approx0.8923}
\]

Alpha changed after packet loss. The increase in alpha is specific to these example values; it does not mean packet loss always increases alpha.

# 7. Process the next ACK after the loss

Now alpha has changed:

\[
\alpha=0.8923
\]

Let's see how this affects the next ACK on each subflow.

For simplicity, use the same updated state snapshot for calculating one ACK on each path.

### ACK on Subflow 1

Coupled increase:

\[
I_1=\frac{0.8923\times1000\times1000}{20750}
\]

\[
I_1\approx43.00\text{ bytes}
\]

Normal TCP increase:

\[
I_2=\frac{1000\times1000}{10500}
\]

\[
I_2\approx95.24\text{ bytes}
\]

Therefore:

\[
\Delta cwnd_1=\min(43,95.24)
\]

\[
\boxed{\Delta cwnd_1\approx43\text{ bytes}}
\]

### ACK on Subflow 2

Coupled increase:

\[
I_1\approx43\text{ bytes}
\]

Normal TCP increase:

\[
I_2=\frac{1000\times1000}{10250}
\]

\[
I_2\approx97.56\text{ bytes}
\]

Therefore:

\[
\boxed{\Delta cwnd_2\approx43\text{ bytes}}
\]

Both subflows now receive approximately 43 bytes of increase per ACK, rather than the previous 25 bytes.

This illustrates how a change in one subflow's congestion window affects the increase behaviour of the entire MPTCP connection.

# 8. Summary of the complete simulation

All congestion-window values are in bytes. The growth figures are illustrative approximations.

| Event | Subflow 1 | Subflow 2 | Alpha |
|---|---:|---:|---:|
| Initial state | 10,000 | 20,000 | 0.7500 |
| After 100 ms | 10,250 | 20,250 | Held |
| After 200 ms | 10,500 | 20,500 | 0.7500* |
| Subflow 2 loses packet | 10,500 | 10,250 | 0.8923 |
| Next ACK on each path | 10,543 | 10,293 | Held |

*Alpha is shown as held at its initial value during the simplified growth calculation. In an actual implementation, alpha can be refreshed approximately once per RTT and following loss, as described in RFC 6356 Section 4.1.*

# 9. What you should understand from this example

There are four important takeaways.

1. **ACKs drive congestion-window growth.** Each newly acknowledged segment can trigger an increase in its subflow's congestion window.
2. **RTTs determine ACK frequency.** A faster path completes more round trips in the same amount of time.
3. **Alpha couples the paths.** A change in one subflow's congestion window can change the increase applied to other subflows.
4. **Loss affects the individual subflow and subsequently the coupled system.** The loss response reduces that subflow's window, which changes the calculation of alpha.

One technical qualification: our 25-byte and 43-byte increases were hand-calculation approximations using a frozen state snapshot. A real implementation updates `cwnd_total` as windows change, uses integer arithmetic, and periodically recomputes alpha. Small increases can also be accumulated until a full segment can be added. See RFC 6356, Sections 3 and 4.

**What I'd like to cover next:** We can turn this exact example into a small Python simulator that implements RFC 6356's Linked Increases algorithm, tracks ACKs, updates both congestion windows, handles different RTTs and simulates packet loss. That would also give you something concrete to use in your project analysis.

---


## 7. User

Export this entire conversation into an MD file. Include every user prompt and every assistant response verbatim. Do not summarize, shorten, or omit anything. Preserve code blocks, equations, tables, and headings.

