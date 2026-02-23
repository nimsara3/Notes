

## 1. What is Network Traffic?

Network traffic is the data moving between computers in a network.

When you:

* Open a website
* Download a file
* Ping another device
* Stream a video

You are generating network traffic.

In Linux, we can generate traffic manually using command-line tools. This is very useful for:

* Testing networks
* Learning packet capture (Wireshark, tcpdump)
* Checking firewall rules
* Simulating load

---

## 2. Where Traffic Works in the Network

Traffic can be generated at different layers:

* Application Layer → HTTP, FTP, DNS
* Transport Layer → TCP, UDP
* Network Layer → ICMP (Ping)

Common ports:

* HTTP → 80
* HTTPS → 443
* DNS → 53
* FTP → 21

---

## 3. Basic Tools to Generate Traffic in Linux

### Ping (ICMP Traffic)

Command:

```bash
ping google.com

```

What it does:

* Sends ICMP echo requests
* Generates continuous traffic
* Tests connectivity

What you see in capture:

* ICMP request
* ICMP reply

Stop with:
`Ctrl + C`

### Curl (HTTP/HTTPS Traffic)

Command:

```bash
curl http://example.com

```

What it does:

* Sends HTTP request
* Generates TCP traffic on port 80

For HTTPS:

```bash
curl https://google.com

```

What you see:

* DNS request
* TCP handshake
* HTTP request & response

### Wget (Download Traffic)

Command:

```bash
wget http://speedtest.tele2.net/1MB.zip

```

What it does:

* Downloads file
* Generates large TCP traffic

Useful for:

* Testing bandwidth
* Observing packet flow

### Netcat (TCP/UDP Traffic)

Netcat is a powerful traffic generator.

TCP traffic:
Terminal 1:

```bash
nc -l 5000

```

Terminal 2:

```bash
nc 127.0.0.1 5000

```

Now type something → traffic is generated.

UDP traffic:

```bash
nc -u 127.0.0.1 5000

```

### Iperf (High Traffic / Load Testing)

Install:

```bash
sudo apt install iperf3

```

Server:

```bash
iperf3 -s

```

Client:

```bash
iperf3 -c <server-ip>

```

This generates heavy TCP traffic.

You can also use UDP:

```bash
iperf3 -c <server-ip> -u

```

---

## 4. Step-by-Step Example: Generate and Capture Traffic

### Step 1: Start Packet Capture

```bash
sudo tcpdump -i eth0

```

### Step 2: Generate Traffic

```bash
ping google.com

```

### Step 3: Observe

You will see:

* ICMP packets
* Source IP
* Destination IP
* Sequence numbers

---

## 5. What You Can Observe in Traffic

When generating traffic, you can see:

* Source and destination IP
* Protocol (TCP, UDP, ICMP)
* Port numbers
* Packet size
* Sequence numbers
* Response time

---

## 6. Common Traffic Types You Can Generate

| Traffic Type | Command-line | Protocol |
| --- | --- | --- |
| Ping | `ping` | ICMP |
| Website | `curl` | TCP |
| Download | `wget` | TCP |
| Chat | `nc` | TCP/UDP |
| Load Test | `iperf3` | TCP/UDP |

---

## 7. What You Will Learn

By generating traffic in Linux CLI, you will learn:

* How packets travel
* How TCP handshake works
* Difference between TCP and UDP
* How ICMP works

---

