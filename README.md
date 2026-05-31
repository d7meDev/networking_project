# TCP/IP Packet Demultiplexer User Manual

## 1. Project Overview

This program is a simple TCP/IP Packet Demultiplexer written in Java using Pcap4J.

The program captures TCP packets from a selected network interface, extracts useful packet information, and stores the information in files inside an `output` folder.

The stored information includes:

- Timestamp
- Source IP address
- Source port
- Destination IP address
- Destination port
- Payload length

For privacy reasons, the program does not store the actual payload data.

---

## 2. Requirements

Before running the program, make sure you have the following installed:

### Java

Install Java JDK.

Recommended version:

```bash
Java 17 or newer
```

Check your Java version:

```bash
java -version
```

### Pcap4J

The program uses the Pcap4J library to capture packets.

### Packet Capture Driver

Depending on your operating system:

| Operating System | Required Driver |
|---|---|
| Windows | Npcap |
| Linux | libpcap |
| macOS | libpcap |

On Windows, install Npcap and run the program as Administrator.

---

## 3. How to Run the Program

Open the project in your Java IDE or terminal.

Run the `Main` class:

```bash
java com.d7me.Main
```

If you are using Maven, you can run it from your IDE or use the Maven run configuration.

On Windows, make sure to run the terminal or IDE as Administrator.

---

## 4. Choosing a Network Interface

When the program starts, it will show a list of available network interfaces.

Example:

```text
Available Interfaces:
1. \Device\NPF_{A1B2C3D4-1111-2222-3333-ABCDEF123456}
   Intel(R) Wi-Fi Adapter
2. \Device\NPF_{B2C3D4E5-2222-3333-4444-BCDEF1234567}
   Realtek Ethernet Controller

Choose interface number:
```

Enter the number of the interface you want to capture packets from.

Example:

```text
Choose interface number: 1
```

After choosing the interface, the program starts capturing TCP packets.

---

## 5. Capturing Packets

After selecting the interface, the program will display:

```text
Capturing TCP packets...
Press Ctrl + C to stop.
```

The program captures TCP packets only.

To generate traffic, you can open a website in your browser or use a command such as:

```bash
curl http://example.com
```

When a TCP packet is captured, the program saves it in a file.

Example:

```text
Packet saved: output/[1717073459123]192.168.1.5.51544-93.184.216.34.80
```

---

## 6. Output Files

The program creates an `output` folder automatically.

Each captured packet is stored in a separate file.

The filename format is:

```text
[timestamp]sourceip.sourceport-destip.destport
```

Example:

```text
[1717073459123]192.168.1.5.51544-93.184.216.34.80
```

This means:

| Part | Meaning |
|---|---|
| `1717073459123` | Timestamp in milliseconds |
| `192.168.1.5` | Source IP address |
| `51544` | Source port |
| `93.184.216.34` | Destination IP address |
| `80` | Destination port |

---

## 7. Example Output File

Example file content:

```text
Timestamp: 1717073459123
Source IP: 192.168.1.5
Source Port: 51544
Destination IP: 93.184.216.34
Destination Port: 80
Payload Length: 120 bytes
```

The payload content itself is not stored.

Only the payload length is stored.

This is done to avoid sharing private or sensitive data.

---

## 8. How to Stop the Program

The program keeps capturing packets until you stop it manually.

To stop the program, press:

```text
Ctrl + C
```

---

## 9. Troubleshooting

### No interfaces found

Possible reasons:

- Npcap/libpcap is not installed.
- The program does not have permission to capture packets.
- The IDE or terminal is not running as Administrator.

### No packets are captured

Try the following:

- Make sure you selected the correct network interface.
- Open a website to generate network traffic.
- Use `curl http://example.com` to generate TCP traffic.
- Make sure the interface is active.

### Capture error

Possible reasons:

- The selected interface is not available.
- The program does not have permission.
- The packet capture driver is not installed correctly.

---

## 10. Privacy Note

The program does not store the actual TCP payload data.

It only stores packet header information and payload length.

This makes the output files safer to share with others.
