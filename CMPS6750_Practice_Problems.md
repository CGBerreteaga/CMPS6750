# Midterm Practice Problems (Modified)

---

## Problem 1: Circuit Switching

Consider a circuit-switched network with four switches (**W, X, Y, Z**) connected in a circular topology. Each link between switches has **3 circuits**. You want to simultaneously establish **3 connections** from **W to Y** and **3 connections** from **X to Z**.

**Question:**  
Is it possible to route all six connections simultaneously without exceeding the available circuits?

---

## Problem 2: Caravan Analogy

A caravan of **8 cars** travels through **three tollbooths**. Each tollbooth is **150 km** apart, the cars travel at **100 km/hr**, and each tollbooth can service **one car every 10 seconds**. The caravan waits at each tollbooth until all cars have arrived.

**Question:**  
Calculate the total end-to-end delay for the caravan.

---

## Problem 3: Packet Segmentation & Delay

A file of size **F bits** must be transmitted from Host A to Host B, passing through two intermediate switches (3 total links). Each link has a transmission rate of **R bps**. The file is segmented into **S-bit** chunks, with **100-bit headers** added to form packets.

**a.** Compute the total transmission delay.  
**b.** Derive the optimal segment size **S** that minimizes the delay.

*(Ignore propagation and processing delays.)*

---

## Problem 4: Statistical Multiplexing

A communication link with bandwidth **15 Mbps** is shared by **300 sources**, each independently active with probability **0.3**. Active sources transmit at **60 Kbps** each.

**a.** What's the expected number of active sources?  
**b.** Provide an expression for the overflow probability.  
**c.** Approximate overflow probability using the Chernoff bound.

---

## Problem 5: Data Center Reliability (DTMC)

A data center transitions daily among three states:

- **State 0:** Operational  
- **State 1:** Down due to power outage  
- **State 2:** Down due to network issues

**Transition probabilities:**

| Current State | Next Day Probabilities                           |
|---------------|---------------------------------------------------|
| Operational   | Power outage: 1/8, Network issue: 1/6, Operational: 17/24 |
| Power outage  | Operational: 1                                   |
| Network issue | Operational: 3/4, Network issue: 1/4             |

**a.** Draw the DTMC and provide the transition matrix.  
**b.** If on Day 0, state probabilities are Operational (0.6), Power outage (0.2), Network issues (0.2), what's the probability it is operational on Day 1?  
**c.** Show why this DTMC is irreducible and aperiodic.

---

## Problem 6: Geo/D/1 Queue

A **Geo/D/1 queue** processes exactly one packet every **4 time slots**. Packets arrive independently each slot with probability **λ**.

**a.** Explain if this DTMC is irreducible and aperiodic.  
**b.** What's the condition for the DTMC to have a stationary distribution?  
**c.** Express the average queue length at steady state.

---

## Problem 7: HTTP Connection Performance

A web page has **4 embedded objects** (each **200,000 bits**) plus a base HTML file of the same size. Control packets are **100 bits** each. The link bandwidth is **500 bits/sec**, link length **50 m**, and propagation speed **3 × 10⁸ m/s**.

Compute total download times for:

**a.** Non-persistent HTTP (4 parallel connections)  
**b.** Persistent HTTP

---

## Problem 8: BitTorrent Free-Riding

Alice joins a BitTorrent swarm but decides not to upload any data (**free-ride**).

**a.** Can Alice still obtain a full copy of the file? Explain.  
**b.** How might Alice use multiple computers with distinct IP addresses to improve her download efficiency?

---

## Problem 9: Client-Server vs. P2P File Sharing

Consider a network with four nodes, where Node 1 has a file (**12 Mbits**) to share. Nodes have the following capacities:

| Node           | 1 | 2 | 3 | 4 |
|----------------|---|---|---|---|
| Upload (Mbps)  | 2 | 4 | 3 | 1 |
| Download (Mbps)| 3 | 5 | 2 | 4 |

**a.** Compute distribution time using the client-server approach.  
**b.** Compute distribution time using the P2P approach.

---

## Problem 10: rdt 3.0 Protocol and Message Reordering

Illustrate clearly (with a timeline of sender/receiver actions) how the **rdt 3.0 protocol** fails when two packets arrive out of order. Show sequence numbers and ACK messages.

---

## Problem 11: Go-Back-N Protocol

In **Go-Back-N protocol** with sender window size **N**, if the receiver currently expects sequence number **k**, what are all possible ACK sequence numbers currently propagating back to the sender? Explain your reasoning.

---

## Problem 12: Window Size in GBN and SR Protocols

For **Go-Back-N (GBN)** and **Selective Repeat (SR)** protocols, given a sequence number space size of **M**, determine the maximum allowable sender window size for each protocol to avoid ambiguity. Briefly explain.

---

# **Answer Key**

**1. Circuit Switching**  
**Answer:** No, circuit capacity insufficient.

**2. Caravan Analogy**  
**Answer:** Delay per booth = 70 sec; total = 140 sec.

**3. Packet Segmentation & Delay**  
- **a.** Delay = $3 \times \frac{F + (F/S) \times 100}{R}$  
- **b.** Optimal $S \to \inf $, practically large.

**4. Statistical Multiplexing**  
- **a.** Active sources = 90  
- **b.** Overflow: $P(X > 250)$ (binomial)  
- **c.** Approximate using Chernoff bound.

**5. Data Center Reliability**  
- **a.** Transition matrix clearly indicated  
- **b.** Day-1 operational probability via transition matrix multiplication  
- **c.** Irreducible (states reachable), Aperiodic (no cycles)

**6. Geo/D/1 Queue**  
- **a.** Irreducible, aperiodic (continuous transitions)  
- **b.** Stationary if $λ < \frac{1}{4}$  
- **c.** Average queue length computed from stationary probabilities

**7. HTTP Connection Performance**  
- Persistent HTTP significantly faster due to fewer TCP setups.

**8. BitTorrent Free-Riding**  
- **a.** Possible but slow.  
- **b.** Multiple IP addresses simulate multiple peers.

**9. Client-Server vs. P2P**  
- **a.** Client-server: $12/2 = 6 s$ (upload limit node 1)  
- **b.** P2P: Faster due to combined upload capacity.

**10. rdt 3.0 Protocol Reordering**  
- Reordering causes incorrect ACK interpretations, leading to unnecessary retransmissions.

**11. Go-Back-N Protocol ACKs**  
- Possible ACKs: $k-1, k-2, \dots, k-N$ due to cumulative acknowledgments.

**12. Window Size in GBN/SR Protocols**  
- GBN: Max window = $M - 1$  
- SR: Max window = $M/2$


