# Network Traffic Capture & Analysis Report  
**Task 5: Capture and Analyze Network Traffic Using Wireshark**  

---

## 1. Objective  
The goal of this task was to get hands-on with Wireshark, capture some live network packets, and figure out which protocols were actually being used in real time while I was online. This wasn’t just about clicking “start” and “stop” — it was about watching the raw conversation happening between my computer and the rest of the internet.



---

## 2. What I Did  

### Step 1: Setting Things Up  
I downloaded Wireshark from the official site, installed it, and made sure the capture driver (Npcap on Windows / wireshark group on Linux) was ready. Without that, Wireshark can’t “listen” to live traffic.

### Step 2: Starting the Capture  
Once Wireshark was open, I chose my active network interface — the one where the little graph was moving — and hit **Start**.  

### Step 3: Creating Some Traffic  
To make sure there was something interesting to capture:
- I opened my browser and visited a couple of websites.
- I ran a quick `ping 8.8.8.8` in the terminal to see some ICMP packets.  
This gave me a mix of browsing and test traffic.

### Step 4: Stopping and Saving  
After about a minute, I hit **Stop**, then saved the file as `wireshark_capture.pcap` so I could dig into it.

---

## 3. What I Found  

### Main Protocols in the Capture  
Using Statistics → Protocol Hierarchy, I identified several protocols in use: ARP, DNS, TCP, HTTP, and ICMP

### Example Packets I Looked At  
- **DNS Query:** My computer asked Google’s DNS server for the IP address of a website.  
- **ARP Request:** A “Who has 192.168.1.1?” broadcast to find the gateway on my local network.  
- **HTTP GET Request:** A plain text web request from my browser to a server (seen only because I visited a non-HTTPS site).  
- **ICMP Echo Request:** My ping command sending a packet to `8.8.8.8`.

---

## 4. Takeaways  
This short capture actually shows a lot of what’s going on under the hood when we do simple things online.  
- ARP works silently to help devices talk on the local network.  
- DNS makes browsing possible without having to memorize IP addresses.  
- TCP keeps things reliable, while HTTP (or HTTPS) carries the actual content.  
- Even something as basic as `ping` gives us its own special protocol — ICMP.

---
