# **CMPS 6750 Computer Networks - Review**

## **Module 0: Introduction to Computer Networking and the Internet**

### **Overview**
Module 0 introduces the study of computer networking and the Internet. Please watch the welcome video, introduce yourself to the class, and acquaint yourself with the course mechanics. In this module, we give a high-level overview of the Internet, where we cover basic hardware and software components of a computer network, briefly introduce common access technologies that allow end users to be connected to the Internet, and the main functionalities provided by the Internet core. We conclude this module by introducing two architectural principles of the Internet, **protocol layering** and **service models**, which allow us to design and study Internet protocols in an organized way.

### **Objectives & Answers**

1. **Explain the basic hardware and software components that make up a network.**
   - A network consists of **hosts (end devices)**, such as computers and smartphones, which communicate over a **network infrastructure** made up of **links (wired or wireless)** and **routers** that forward data. Software components include **protocols**, which define how data is transmitted, and **applications**, which use the network to exchange information.

2. **Explain the pros and cons of circuit switching and packet switching.**
   - **Circuit switching** reserves a dedicated communication path between two nodes for the entire session, ensuring reliable data transmission but leading to inefficient resource use when idle.  
   - **Packet switching** divides messages into smaller packets sent independently over a shared network, maximizing efficiency but introducing potential delays and packet loss.
   - **Example:** If four circuits are available per link in a circuit-switched network, only a limited number of connections can be established at once. In contrast, packet-switched networks can dynamically allocate bandwidth across multiple users.

3. **Explain what protocol layering is and why it helps to organize a network architecture in layers.**
   - **Protocol layering** is a design principle that divides network functions into layers, where each layer has a specific role and communicates only with adjacent layers. This modular approach simplifies network design, troubleshooting, and interoperability between different hardware and software implementations.

4. **Explain the concept of network delay using the caravan analogy.**
   - The **caravan analogy** models network delays using cars moving through toll booths. The delay depends on processing speed (toll booth service rate) and propagation speed (road distance). If a caravan has multiple cars and each tollbooth services one car every 12 seconds, the total end-to-end delay includes both **transmission delay** (time to process each car) and **propagation delay** (time to travel between tollbooths).

5. **Explain how to calculate transmission delay when sending data across multiple links.**
   - **Formula:**
     
     $\text{Total Transmission Delay} = \frac{F}{R} + \sum \left( \frac{L}{R} \right)$
     
     where F is the total file size, L is the packet size, and R is the transmission rate.
   - **Minimizing delay:** To minimize transmission delay, an optimal packet size S must be chosen such that the transmission time is reduced while minimizing header overhead.

### **Key Terms and Definitions**

- **Host:** A device (computer, smartphone, etc.) connected to a network.  
- **Client:** A host that requests services from a server.  
- **Server:** A host that provides services to clients.  
- **Protocol:** A set of rules governing communication between network devices.  
- **Service:** The functionality provided by a network protocol or system.  
- **Network Core:** The central part of a network that connects multiple sub-networks and handles data routing.  
- **Network Edge:** The part of a network where end devices (hosts) are connected.  
- **Access Network:** The network that connects end users to the Internet. Examples: Wi-Fi, Ethernet, 4G/5G.  
- **Bandwidth:** The maximum data transfer rate of a network link.  
- **Link:** A communication channel that connects two network devices.  
- **Packet:** A small unit of data transmitted over a network.  
- **Packet Switching:** A method of data transmission where messages are divided into packets sent independently.  
- **Store-and-Forward:** A technique in which a switch/router stores a packet before forwarding it to ensure reliability.  
- **Circuit Switching:** A networking method that establishes a dedicated communication path before data transmission.  
- **Internet Service Provider (ISP):** A company that provides users access to the Internet.  
- **Protocol Stack:** A hierarchical structure of protocols that work together to enable network communication.  
- **Encapsulation:** The process of wrapping data with protocol headers as it moves through network layers.
- **Transmission Delay:** The time required to push all bits of a packet into the network.
- **Propagation Delay:** The time required for a signal to travel from sender to receiver.
- **Queuing Delay:** The time a packet spends waiting in a buffer before being processed.
- **Processing Delay:** The time taken by a router to analyze a packet’s header and make a forwarding decision.

### **Review Questions (Multiple Choice)**

1. **What is the primary function of a router in a network?**  
   - A) Forwarding data packets between different networks.  
   - B) Connecting end devices.  
   - C) Converting analog signals to digital.  
   - D) Encrypting data.  
   - **Answer:** A

2. **Which network component connects multiple devices within the same local area network (LAN)?**  
   - A) Router  
   - B) Hub  
   - C) Switch  
   - D) Repeater  
   - **Answer:** C

3. **What is the main difference between TCP and UDP?**  
   - A) TCP is faster than UDP.  
   - B) TCP provides reliable, connection-oriented communication, while UDP is connectionless and does not guarantee delivery.  
   - C) UDP uses encryption while TCP does not.  
   - D) TCP is only used for video streaming.  
   - **Answer:** B

4. **How many layers are there in the OSI model?**  
   - A) 4  
   - B) 5  
   - C) 6  
   - D) 7  
   - **Answer:** D

5. **Which layer of the OSI model is responsible for end-to-end communication?**  
   - A) Physical  
   - B) Network  
   - C) Transport  
   - D) Data Link  
   - **Answer:** C

## **Module 1: Network Performance Analysis**

### **Overview**
Module 1 introduces the basics of performance analysis for network systems. This includes measuring packet delay, packet loss, and throughput. Additionally, it introduces **statistical multiplexing**, which allows efficient bandwidth sharing, and the **Chernoff bound**, which helps analyze probability distributions in network traffic.

### **Objectives & Answers**

1. **Define four sources of packet delay in packet-switched networks.**
   - **Processing Delay:** Time taken by a router to examine a packet's header and determine where to forward it.
   - **Queuing Delay:** Time a packet spends waiting in a queue before being transmitted.
   - **Transmission Delay:** Time required to push all bits of a packet onto the link.
   - **Propagation Delay:** Time required for a signal to travel from sender to receiver.

2. **Explain the proof of the Chernoff bound and apply it in statistical multiplexing.**
   - The **Chernoff bound** provides an upper bound on the probability of large deviations of a sum of independent random variables from its expected value. In statistical multiplexing, it helps estimate the overflow probability when multiple sources share a link.
   - **Example:** Given a link of 10 Mbps shared by 500 sources, where each source is active with probability 0.2 and transmits at 50 Kbps, we use Chernoff bound to estimate the probability that the total demand exceeds available bandwidth.

3. **Evaluate packet delay, loss, and throughput, and analyze the performance gain of statistical multiplexing.**
   - **Packet delay** is the total time taken for a packet to reach its destination, including processing, queuing, transmission, and propagation delays.
   - **Packet loss** occurs when network congestion forces routers to drop packets.
   - **Throughput** is the actual data transfer rate achieved over a network.
   - **Statistical multiplexing** improves performance by dynamically sharing bandwidth among users, maximizing utilization while reducing congestion.

### **Key Terms and Definitions**

- **Queue:** A buffer where packets wait before being processed.
- **Queuing Delay:** The time a packet waits in a queue before transmission.
- **Nodal Processing Delay:** Time taken by a node (e.g., router) to process a packet.
- **Transmission Delay:** Time to push a packet’s bits onto the transmission link.
- **Propagation Delay:** Time for a signal to travel through a medium.
- **Packet Loss:** Packets that are dropped due to network congestion or errors.
- **Throughput:** The actual rate at which data is successfully transmitted.
- **Statistical Multiplexing:** Sharing of a network resource among multiple users dynamically.

### **Quiz (Multiple Choice)**

1. **Which of the following is NOT a source of packet delay?**
   - A) Processing delay  
   - B) Queuing delay  
   - C) Acknowledgment delay  
   - D) Transmission delay  
   - **Answer: C**  

2. **What happens to queuing delay as traffic intensity increases?**
   - A) It decreases  
   - B) It remains constant  
   - C) It increases  
   - D) It becomes zero  
   - **Answer: C**  

3. **What does the Chernoff bound estimate in statistical multiplexing?**
   - A) The average transmission delay  
   - B) The probability of exceeding available bandwidth  
   - C) The minimum queuing delay  
   - D) The efficiency of circuit switching  
   - **Answer: B**  

4. **Which factor primarily determines propagation delay?**
   - A) Packet size  
   - B) Transmission rate  
   - C) Distance and signal speed  
   - D) Queue length  
   - **Answer: C**  

5. **In statistical multiplexing, bandwidth is shared among users:**
   - A) Equally at all times  
   - B) Dynamically based on demand  
   - C) Only during congestion  
   - D) Using a dedicated path per user  
   - **Answer: B**

# Module 2: Markov Chains and Queueing Theory

## Overview

Module 2 introduces **Discrete-Time Markov Chains (DTMCs)** as a mathematical tool to study dynamic systems in networking. This module explores how DTMCs model **packet loss, delay, and network reliability**. Additionally, queueing theory is introduced with the **Geo/Geo/1 queue** model, which helps analyze network performance using probabilistic methods.

## Objectives & Answers

### 1. Write down the state space and transition probability matrix of a small DTMC.

- A **Discrete-Time Markov Chain (DTMC)** consists of a set of states and a transition probability matrix **P**, where each entry **P(i, j)** represents the probability of transitioning from state **i** to state **j**.
- **Example:** In a simple data center model, the states might be:
  - `0`: Working
  - `1`: Down due to a backhoe issue
  - `2`: Down due to a software bug
- The transition probability matrix for this system would reflect the likelihood of transitioning between these states.

### 2. Explain if a small DTMC is irreducible and aperiodic, and derive its stationary distribution using balance equations.

- A **DTMC is irreducible** if it is possible to reach any state from any other state.
- A **DTMC is aperiodic** if it does not get stuck in cyclic behavior.
- The **stationary distribution** is found by solving the **global balance equations**, ensuring the long-term probability of being in each state remains constant.
- **Example Calculation:** In a data center model, we solve the system of equations $\pi P = \pi$ to determine the fraction of time the data center is working.

### 3. Derive properties of Geo/Geo/1 and Geo/Geo/1/B queues and apply Little’s Law.

- The **Geo/Geo/1 queue** is a single-server queue where arrivals and service times follow a geometric distribution.
- The **Geo/Geo/1/B queue** has a finite buffer of size **B**, meaning excess arrivals are lost.
- **Little’s Law**:
$L = \lambda W $
  - L: Average number of packets in the system
  - $\lambda$: Arrival rate
  - W: Average time a packet spends in the system$

## Key Terms and Definitions

- **Aperiodic Markov Chain:** A Markov Chain where states do not have periodic cycles.
- **Discrete-Time Markov Chain (DTMC):** A probabilistic model where future states depend only on the present state.
- **Geo/Geo/1 Queue:** A single-server queue where arrivals and service times follow a geometric distribution.
- **Geo/Geo/1/B Queue:** A Geo/Geo/1 queue with a finite buffer.
- **Global Balance Equations:** Equations used to determine the steady-state probabilities of a Markov Chain.
- **Irreducible Markov Chain:** A chain where every state is reachable from any other state.
- **Limiting Distributions:** The long-run probabilities of being in each state.
- **Local Balance Equations:** Equations that help solve for stationary distributions.
- **Markov Property:** The principle that the next state depends only on the current state.
- **Stationary Distribution:** The probability distribution that remains unchanged over time.
- **Stochastic Process:** A system that evolves probabilistically over time.
- **Transition Probabilities:** The likelihood of moving between states in a Markov Chain.
- **Little’s Law:** A formula linking the average number of items in a system, arrival rate, and waiting time.

## Quiz (Multiple Choice)

**1. What defines an irreducible Markov Chain?**  
- A) It is deterministic  
- B) Every state is reachable from any other state  
- C) It has exactly two states  
- D) It follows a periodic pattern  
**Answer: B**

**2. What does the stationary distribution of a DTMC represent?**  
- A) The most frequently visited state  
- B) The long-run probabilities of each state  
- C) The probability of transitioning to another state  
- D) The periodicity of the Markov Chain  
**Answer: B**

**3. Which queueing model includes a finite buffer?**  
- A) Geo/Geo/1  
- B) Geo/Geo/1/B  
- C) M/M/1  
- D) FIFO Queue  
**Answer: B**

**4. Which of the following best describes Little’s Law?**  
- A) A formula for computing bandwidth efficiency  
- B) A relationship between delay, queue length, and arrival rate  
- C) A method for reducing transmission errors  
- D) A principle for analyzing TCP congestion control  
**Answer: B**

**5. What is the Markov Property?**  
- A) The future state depends only on the present state  
- B) The probability of all states is equal  
- C) The process has periodic cycles  
- D) The transition matrix remains constant  
**Answer: A**

# Module 3: Internet Protocol Stack and Application Layer

## Overview
Module 3 initiates our exploration of the **Internet protocol stack** using a top-down approach, beginning with the **application layer**. This module introduces the **key principles of network applications**, examines two major application-layer protocols (**HTTP** and **SMTP**), and covers the fundamentals of **socket programming** for both **TCP and UDP**. Additionally, students will implement and analyze a basic **web server and client** in Python.

## Objectives & Answers

### 1. Explain the key principles of network applications.
- Network applications rely on protocols that enable communication between **clients** and **servers**.
- Applications use different transport protocols such as **TCP** (reliable, connection-oriented) and **UDP** (unreliable, connectionless).
- Examples include **web browsing (HTTP), email (SMTP), and file sharing (BitTorrent, P2P networks)**.

### 2. Describe the key elements and design choices of HTTP and SMTP protocols.
- **HTTP (Hypertext Transfer Protocol)**: A stateless, request-response protocol used for retrieving web pages.
  - **Non-persistent HTTP**: Opens a new TCP connection for each object request, increasing latency.
  - **Persistent HTTP**: Uses a single TCP connection for multiple object requests, reducing overhead.
- **SMTP (Simple Mail Transfer Protocol)**: A push-based protocol used for sending emails between servers.
  - Uses the **store-and-forward** model, where messages are temporarily stored before reaching the recipient.
  - Works closely with **POP3/IMAP** for email retrieval.

### 3. Analyze the performance of non-persistent and persistent HTTP connections.
- **Non-persistent HTTP** introduces additional delay since each request requires a new TCP connection.
- **Persistent HTTP** is more efficient because it reduces connection overhead.
- **Example Calculation:**
  - **Link length:** 10 meters  
    **Transmission rate:** 150 bits/sec  
    **Packet sizes:**  
      - Data packet: 100,000 bits  
      - Control packet: 200 bits  
    **Number of objects:** 10  
    **Propagation speed:** $3 \times 10^8$ m/sec

  **Transmission delays:**
  - Data packet: $100,000 / 150 = 666.67$ sec  
  - Control packet: $200 / 150 = 1.33$ sec

  **Propagation delay:**
  - $10 / 3 \times 10^8 \approx 0$ sec (negligible)

  **Total download time comparison:**
  - **Non-persistent HTTP** (5 parallel connections):  
    Effective rate per connection: $\frac{150}{5} = 30$ bits/sec  
    Per object delay: $\frac{100,000}{30} = 3,333.33$ sec  
    Total for 10 objects: $10 \times 3,333.33 = 33,333.3$ sec
  - **Persistent HTTP** (single connection):  
    Per object delay: $\frac{100,000}{150} = 666.67$ sec  
    Total for 10 objects: $10 \times 666.67 = 6,666.7$ sec

  **Conclusion:** Persistent HTTP significantly reduces total download time.

### 4. Implement network applications using TCP and UDP sockets.
- **TCP Sockets**: Reliable, connection-oriented communication used for web and email applications.
- **UDP Sockets**: Fast, connectionless communication used for real-time applications (video streaming, VoIP).
- **Example:** Implementing a basic web server that handles one HTTP request at a time and responds with requested files or a 404 error message.

## Key Terms and Definitions
- **Client-Server Model:** Clients request services from centralized servers.
- **Peer-to-Peer (P2P):** Decentralized model where peers share resources directly.
- **HTTP (Hypertext Transfer Protocol):** Protocol for retrieving web pages.
- **SMTP (Simple Mail Transfer Protocol):** Protocol for sending emails.
- **Non-Persistent HTTP:** Requires a new TCP connection per request.
- **Persistent HTTP:** Reuses one TCP connection for multiple requests.
- **Sockets:** Endpoints for network communication in programming.
- **Web Caching:** Stores frequently accessed web content closer to users.
- **BitTorrent:** P2P protocol for file sharing.
- **Port Number:** Identifies specific network services on a device.
- **IP Address:** Unique identifier assigned to networked devices.
- **TCP Sockets:** Reliable, stream-based communication.
- **UDP Sockets:** Connectionless, faster but less reliable communication.

## Quiz (Multiple Choice)

**1. What is the main advantage of persistent HTTP over non-persistent HTTP?**  
- A) Requires multiple TCP connections  
- B) Reduces latency by reusing a single connection  
- C) Uses UDP instead of TCP  
- D) Only works for email services  
**Answer: B**

**2. Which of the following protocols is used for sending email?**  
- A) HTTP  
- B) FTP  
- C) SMTP  
- D) TCP  
**Answer: C**

**3. What is the main purpose of web caching?**  
- A) To encrypt HTTP requests  
- B) To store frequently accessed content closer to users  
- C) To increase the security of email transmissions  
- D) To replace TCP with UDP  
**Answer: B**

**4. What does a port number represent in networking?**  
- A) The physical address of a device  
- B) A unique identifier for a network service on a host  
- C) The network delay of a connection  
- D) The encryption key used in secure communications  
**Answer: B**

# Module 4: DNS, P2P File Sharing, and Video Streaming

## Overview
This module covers three key topics related to the **Internet’s application layer**: **Domain Name System (DNS), Peer-to-Peer (P2P) file distribution, and video streaming services**.

- **DNS**: A distributed database implemented as an application-layer protocol that provides a directory service for other applications.
- **P2P File Distribution**: A file-sharing architecture allowing nodes to efficiently download and distribute files, providing greater scalability than traditional client-server models.
- **Video Streaming and Content Distribution Networks (CDNs)**: Techniques optimizing the delivery of video content across the Internet, including **Dynamic Adaptive Streaming Over HTTP (DASH)**.

## Objectives & Answers

### 1. Explain typical name resolution processes and define the four types of DNS records.
- DNS resolves domain names into IP addresses using **recursive and iterative queries**.
- **Four Types of DNS Records:**
  - **A Record**: Maps a hostname to an IPv4 address.
  - **AAAA Record**: Maps a hostname to an IPv6 address.
  - **CNAME (Canonical Name) Record**: Maps an alias to the true (canonical) hostname.
  - **MX (Mail Exchange) Record**: Specifies the mail server responsible for handling email.

### 2. Compare client-server architectures and P2P architectures and derive the minimum file distribution times.
- **Client-Server Model**:
  - A central server sends the file to each requesting client.
  - **Total Distribution Time** (Server upload rate $u$, client download rate $d$, file size $F$, $N$ clients):
  $
  T_{CS} = \max\left(\frac{F}{u}, \frac{N F}{d}\right)
  $

- **P2P Model**:
  - Each peer downloading a piece can upload it to others.
  - **Total Distribution Time**:
  $
  T_{P2P} = \max\left(\frac{F}{u}, \frac{F}{d}, \frac{N F}{u + d}\right)
  $

### 3. Explain how popular video streaming services are implemented.
- **Video Streaming Approaches**:
  - **Progressive Download**: Downloads the entire video before playback.
  - **Streaming (DASH)**: Breaks videos into chunks; quality dynamically adjusts based on bandwidth availability.
  - **Content Distribution Networks (CDNs)**: Geographically distributed servers cache video content to reduce latency and bandwidth use.

## Key Terms and Definitions
- **Alias Hostname**: Alternative name for a website, mapped using a CNAME record.
- **Authoritative DNS Server**: DNS server responsible for a specific domain.
- **Canonical Hostname**: The true, official hostname for a website.
- **Content Distribution Networks (CDNs)**: System of distributed servers efficiently delivering content.
- **DNS Registrar**: Company managing domain name registrations.
- **Domain Name System (DNS)**: Distributed system mapping domain names to IP addresses.
- **Dynamic Adaptive Streaming Over HTTP (DASH)**: Video streaming adapting quality to available bandwidth.
- **Peer-to-Peer (P2P)**: Network where peers directly share resources without central servers.
- **Root DNS Server**: Top-level DNS server assisting domain name resolutions.
- **Top-Level DNS (TLD) Server**: Handles specific top-level domains (.com, .org, .edu).

## Quiz (Multiple Choice)

**1. What is the main function of DNS?**  
- A) Encrypt network traffic  
- B) Resolve domain names into IP addresses  
- C) Provide email forwarding services  
- D) Speed up video streaming  
**Answer: B**

**2. Which of the following is NOT a type of DNS record?**  
- A) A Record  
- B) MX Record  
- C) HTML Record  
- D) CNAME Record  
**Answer: C**

**3. Why is P2P file distribution more scalable than client-server?**  
- A) It reduces total upload bandwidth for the server  
- B) It requires all peers to have a fixed IP address  
- C) It limits the number of concurrent downloads  
- D) It prevents data loss  
**Answer: A**

**4. Which technology is used to reduce video streaming latency?**  
- A) SMTP  
- B) DASH  
- C) ICMP  
- D) ARP  
**Answer: B**

**5. What is the function of a Content Distribution Network (CDN)?**  
- A) To store and serve content from distributed locations  
- B) To secure websites from DDoS attacks  
- C) To assign IP addresses to domain names  
- D) To compress large files before sending them  
**Answer: A**

**6. Which of the following DNS records is used to map a domain name to an IPv6 address?**  
- A) A Record  
- B) CNAME Record  
- C) AAAA Record  
- D) MX Record  
**Answer: C**

**7. What happens when a DNS lookup request fails?**  
- A) The request is redirected to another server  
- B) The client receives an error message  
- C) The website loads with a default IP address  
- D) The ISP assigns an arbitrary IP address  
**Answer: B**

**8. Which of the following best describes DASH video streaming?**  
- A) Uses a fixed bitrate for all users  
- B) Allows quality to change dynamically based on bandwidth availability  
- C) Requires a dedicated connection for each video segment  
- D) Uses UDP instead of TCP for faster streaming  
**Answer: B**

**9. What is the purpose of a TLD (Top-Level Domain) DNS server?**  
- A) To map domain names to IP addresses for all websites  
- B) To handle domain registrations and direct requests to authoritative DNS servers  
- C) To store website content for faster access  
- D) To manage email forwarding services  
**Answer: B**

**10. Which of the following is an advantage of CDNs?**  
- A) Reduces latency for users  
- B) Increases data storage costs  
- C) Requires users to download entire videos before watching  
- D) Limits access to high-definition content  
**Answer: A**

# Module 5: Transport Layer and Reliable Data Transfer

## Overview
Module 5 explores the **Transport Layer** and mechanisms for ensuring **reliable data transfer**. It covers key concepts such as the roles of **UDP and TCP**, mechanisms like **rdt 3.0**, **Go-Back-N (GBN)**, and **Selective Repeat (SR)** protocols, as well as **multiplexing** and **demultiplexing**.

## Objectives & Answers

### 1. Explain the key principles of the transport and application layers.
- The **transport layer** ensures end-to-end delivery between applications using protocols such as **TCP** (reliable) or **UDP** (unreliable).
- Key services include **multiplexing** (combining streams from multiple applications) and **demultiplexing** (routing incoming segments to the correct application).

### 2. Describe the principles of reliable data transfer.
- Reliable transfer handles issues like **packet loss**, **corruption**, and **out-of-order delivery**.
- Essential components include acknowledgments (**ACKs**), sequence numbers, checksums, timers, and retransmission mechanisms.
- Common protocols include **rdt 3.0 (stop-and-wait)**, **Go-Back-N (GBN)**, and **Selective Repeat (SR)**.

### 3. Implement and analyze simplified reliable data transfer protocols.
- **Stop-and-Wait Protocol**: Sends one packet at a time, waits for ACK before sending the next, simple but inefficient.
- **Go-Back-N**: Sends multiple packets at once but retransmits all subsequent packets after a loss.
- **Selective Repeat**: Efficiently retransmits only missing packets, improving throughput.

## Key Terms and Definitions
- **Multiplexing**: Combining multiple application data streams over a single transport-layer connection.
- **Demultiplexing**: Directing incoming segments to the correct application.
- **Reliable Data Transfer (rdt)**: Techniques to ensure accurate data transmission over unreliable networks.
- **Stop-and-Wait Protocol**: Sends one packet at a time, awaiting an acknowledgment before proceeding.
- **Go-Back-N (GBN)**: Sender sends multiple packets but retransmits all packets after a lost packet.
- **Selective Repeat (SR)**: Sender retransmits only lost or corrupted packets, improving efficiency.
- **Checksum**: Detects packet corruption in transmission.
- **Sliding Window Protocols**: Efficiently manages multiple in-flight packets and retransmissions.
- **Sequence Numbers**: Numbers packets to ensure correct ordering and detect duplicates.
- **Cumulative ACKs**: Acknowledgments covering multiple sequentially received packets.

## Example Problem: Analyzing rdt 3.0 Protocol Behavior
**Problem:** Consider the scenario when packet reordering occurs in the **rdt 3.0 protocol**:

## Step-by-Step Solution

**Scenario:** Packets arrive out of order, causing confusion.

### Timeline Example

| Time | Sender Action                 | Receiver Action                     | Explanation                                   |
|------|-------------------------------|-------------------------------------|-----------------------------------------------|
| t₀   | Sends Packet #0               |                                     | Sender initiates by sending Packet #0.        |
| t₁   | Sends Packet #1 prematurely   |                                     | Sender transmits Packet #1 (Packet #0 delayed). |
| t₂   |                               | Receives Packet #1, discards it     | Receiver expects Packet #0 first; discards out-of-order packet. |
| t₃   | Timeout waiting for ACK #0    |                                     | Sender receives no ACK; assumes Packet #0 was lost. |
| t₄   | Retransmits Packet #0         |                                     | Sender retransmits Packet #0 after timeout.   |
| t₅   |                               | Receives Packet #0, sends ACK #0    | Receiver successfully receives Packet #0 and acknowledges. |
| t₆   | Receives ACK #0, proceeds     |                                     | Sender receives ACK and continues transmission. |

### Explanation of Scenario

This clearly illustrates packet reordering and how protocols manage retransmission and acknowledgments when packets arrive out of sequence.
|                                      |

- **Issue**: Reordering causes unnecessary retransmissions.
- **Improvement**: Use sequence numbers and buffering (**Selective Repeat**) to handle reordering effectively.

## Quiz (Multiple Choice)

**1. What is multiplexing in the transport layer?**  
- A) Assigning IP addresses to packets  
- B) Combining multiple application data streams into one network connection  
- C) Encrypting data  
- D) Splitting data into multiple paths  
**Answer: B**

**2. A transport-layer checksum primarily detects:**  
- A) Network delays  
- B) Packet corruption  
- C) Congestion level  
- D) IP address mismatches  
**Answer: B**

**3. Which protocol retransmits only lost packets?**  
- A) Go-Back-N  
- B) Selective Repeat  
- C) Stop-and-Wait  
- D) UDP  
**Answer: B**

**4. In rdt 3.0, what triggers packet retransmission?**  
- A) Duplicate ACKs  
- B) Checksum verification failure  
- C) Timeout expiration without ACK  
- D) Immediate ACK from receiver  
**Answer: B**

**5. Go-Back-N retransmits:**  
- A) Only the corrupted packet  
- B) Only the next packet  
- C) All packets after a lost packet  
- D) No packets  
**Answer: C**

**5. A cumulative acknowledgment (ACK) means:**  
- A) ACKs are sent individually for each packet  
- B) ACK covers multiple sequential packets  
- C) ACK is sent only after packet loss  
- D) ACK is always encrypted  
**Answer: B**

**6. A drawback of the stop-and-wait protocol is:**  
- A) High latency due to waiting for each ACK  
- B) It requires no sequence numbers  
- C) It handles multiple simultaneous packets  
- D) It is unreliable  
**Answer: B**

**7. TCP ensures reliable data transfer primarily by:**  
- A) Randomly resending packets  
- B) Using checksums and retransmissions  
- C) Increasing packet size  
- D) Avoiding sequence numbers  
**Answer: B**

**8. What does transport-layer demultiplexing achieve?**  
- A) Encrypts incoming segments  
- B) Directs incoming segments to the correct application  
- C) Splits data into smaller segments  
- D) Prevents packet collisions  
**Answer: B**

**9. The main disadvantage of Stop-and-Wait protocol is:**  
- A) Complexity in implementation  
- B) Inefficient bandwidth utilization  
- C) Fast packet loss detection  
- D) Use of large window size  
**Answer: B**

**10. What does Round-Trip Time (RTT) measure?**  
- A) Time to establish a connection  
- B) Time for a packet to travel to the receiver and back  
- C) Bandwidth used per second  
- D) Number of hops between sender and receiver  
**Answer: B**
