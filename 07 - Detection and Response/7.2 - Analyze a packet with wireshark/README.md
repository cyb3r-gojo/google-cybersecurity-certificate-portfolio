# Analyze your first packet with Wireshark
As a security analyst, you’ll need to analyze network traffic in order to learn what type of traffic is being sent to and from systems on the networks you’ll be working with.

You’ll use Wireshark to inspect packet data and apply filters to sort through packet information efficiently.

## Scenario
In this scenario, you’re a security analyst investigating traffic to a website.

You’ll analyze a network packet capture file that contains traffic data related to a user connecting to an internet site. The ability to filter network traffic using packet sniffers to gather relevant information is an essential skill as a security analyst.

You must filter the data in order to:

- Identify the source and destination IP addresses involved in this web browsing session,
- Examine the protocols that are used when the user makes the connection to the website, and
- Analyze some of the data packets to identify the type of information sent and received by the systems that connect to each other when the network data is captured.

## Task 1.  Explore data with Wireshark
In this task, you must open a network packet capture file that contains data captured from a system that made web requests to a site. You need to open this data with Wireshark to get an overview of how the data is presented in the application.

1. To open the packet capture file, double-click the sample file on the Windows desktop. This will start Wireshark.

<img width="609" height="609" alt="Screenshot 2026-01-28 at 11 41 01 PM" src="https://github.com/user-attachments/assets/c1e4411b-588c-418c-831f-f30654ede5cc" />

The packet capture file has the Wireshark packet capture file icon, which shows a shark's fin swimming above three rows of binary digits. The packet capture file has a ```.pcap``` file extension that is hidden by default by Windows Explorer and on the desktop view.

2. Double-click the Wireshark title bar next to the sample.pcap filename to maximize the Wireshark application window.

<img width="1440" height="784" alt="Screenshot 2026-01-28 at 11 43 36 PM" src="https://github.com/user-attachments/assets/58d736e6-c70b-4f2a-8e81-21831b647a92" />

A lot of network packet traffic is listed, which is why you’ll apply filters to find the information needed in an upcoming step.

For now, here is an overview of the key property columns listed for each packet:

- **No.:** The index number of the packet in this packet capture file
- **Time:** The timestamp of the packet
- **Source:** The source IP address
- **Destination:** The destination IP address
- **Protocol:** The protocol contained in the packet
- **Length:** The total length of the packet
- **Info:** Some infomation about the data in the packet (the payload) as interpreted by Wireshark

Not all the data packets are the same color. Coloring rules are used to provide high-level visual cues to help you quickly classify the different types of data. Since network packet capture files can contain large amounts of data, you can use coloring rules to quickly identify the data that is relevant to you. The example packet lists a group of light blue packets that all contain DNS traffic, followed by green packets that contain a mixture of TCP and HTTP protocol traffic.

3. Scroll down the packet list until a packet is listed where the info column starts with the words ```'Echo (ping) request'```.


```What is the protocol of the first packet in the list where the info column starts with the words 'Echo (ping) request'?```

```Answer: ICMP is the protocol type listed for the first (and all) packets that contain 'Echo (ping) request' in the info column.```

## Task 2. Apply a basic Wireshark filter and inspect a packet

In this task, you’ll open a packet in Wireshark for more detailed exploration and filter the data to inspect the network layers and protocols contained in the packet.

1. Enter the following filter for traffic associated with a specific IP address. Enter this into the **Apply a display filter... **text box immediately above the list of packets:

```
ip.addr == 142.250.1.139
```

2. Press **ENTER** or click the **Apply display filter** icon in the filter text box.

The list of packets displayed is now significantly reduced and contains only packets where either the source or the destination IP address matches the address you entered. Now only two packet colors are used: ```**light pink**``` for ```**ICMP**``` protocol packets and ```**light green**``` for ```**TCP**``` (and ```HTTP```, which is a subset of ```TCP```) packets.

3. Double-click the first packet that lists ```TCP``` as the protocol.

This opens a packet details pane window:

<img width="756" height="592" alt="Screenshot 2026-01-28 at 11 54 19 PM" src="https://github.com/user-attachments/assets/6d86c0c9-e143-46ff-bcd1-5579dbec81f4" />

The upper section of this window contains subtrees where Wireshark will provide you with an analysis of the various parts of the network packet. The lower section of the window contains the raw packet data displayed in hexadecimal and ASCII text. There is also placeholder text for fields where the character data does not apply, as indicated by the dot (“.”).

**Note:** _The details pane is located at the bottom portion of the main Wireshark window. It can also be accessed in a new window by double clicking a packet._

4. Double-click the first subtree in the upper section. This starts with the word ```Frame```.

This provides you with details about the overall network packet, or frame, including the frame length and the arrival time of the packet. At this level, you’re viewing information about the entire packet of data.

5. Double-click ```Frame``` again to collapse the subtree and then double-click the ```Ethernet II``` subtree.

This item contains details about the packet at the Ethernet level, including the source and destination MAC addresses and the type of internal protocol that the Ethernet packet contains.

6. Double-click ```Ethernet II``` again to collapse that subtree and then double-click the ```Internet Protocol Version 4``` subtree.

This provides packet data about the Internet Protocol (IP) data contained in the Ethernet packet. It contains information such as the source and destination IP addresses and the Internal Protocol (for example, TCP or UDP), which is carried inside the IP packet.

**Note:** _The Internet Protocol Version 4 subtree is Internet Protocol Version 4 (IPv4). The third subtree label reflects the protocol._

The source and destination IP addresses shown here match the source and destination IP addresses in the summary display for this packet in the main Wireshark window.

7. Double-click ```Internet Protocol Version 4``` again to collapse that subtree and then double-click the ```Transmission Control Protocol``` subtree.

This provides detailed information about the TCP packet, including the source and destination TCP ports, the TCP sequence numbers, and the TCP flags.

The source port and destination port listed here match the source and destination ports in the info column of the summary display for this packet in the list of all of the packets in the main Wireshark window.

```What is the TCP destination port of this TCP packet?```

```Answer: Port 80 is the TCP destination port for this packet. It contains the initial web request to an HTTP website that will typically be listening on TCP port 80.```

8. In the ```Transmission Control Protocol``` subtree, scroll down and double-click ```Flags```.

This provides a detailed view of the TCP flags set in this packet.

9. Click the ```X``` icon to close the detailed packet inspection window.

10. Click the ```X Clear display filter``` icon in the Wireshark filter bar to clear the IP address filter.

<img width="757" height="150" alt="Screenshot 2026-01-29 at 12 00 48 AM" src="https://github.com/user-attachments/assets/bc2de5fe-15df-448c-8f45-f9fb7654be71" />

All the packets have returned to the display.

If you ever accidentally close the Wireshark application, you can reopen it by double-clicking the sample file on the desktop.

## Task 3. Use filters to select packets
In this task, you’ll use filters to analyze specific network packets based on where the packets came from or where they were sent to. You’ll explore how to select packets using either their physical Ethernet Media Access Control (MAC) address or their Internet Protocol (IP) address.

1. Enter the following filter to select traffic for a specific source IP address only. Enter this into the ```Apply a display filter...``` text box immediately above the list of packets:

```
ip.src == 142.250.1.139
```

2. Press ```ENTER``` or click the ```Apply display filter``` icon in the filter text box.

A filtered list is returned with fewer entries than before. It contains only packets that came from ```142.250.1.139```.

3. Click the ```X Clear display filter``` icon in the Wireshark filter bar to clear the IP address filter.

4. Enter the following filter to select traffic for a specific destination IP address only:

```
ip.dst == 142.250.1.139
```

5. Press ```ENTER``` or click the ```Apply display filter``` icon in the filter text box.

A filtered list is returned that contains only packets that were sent to ```142.250.1.139```.

6. Click the ```X Clear display filter``` icon in the Wireshark filter bar to clear the IP address filter.

7. Enter the following filter to select traffic to or from a specific Ethernet MAC address. This filters traffic related to one MAC address, regardless of the other protocols involved:

```
eth.addr == 42:01:ac:15:e0:02

```
8. Press ```ENTER``` or click the ```Apply display filter``` icon in the filter text box.

9. Double-click the first packet in the list. You may need to scroll back to display the first packet in the filtered list.

10. Double-click the ```Ethernet II``` subtree if it is not already open.

The MAC address you specified in the filter is listed as either the source or destination address in the expanded Ethernet II subtree.

11. Double-click the ```Ethernet II``` subtree to close it.

12. Double-click the Internet Protocol Version 4 subtree to expand it and scroll down until the ```Time to Live``` and ```Protocol``` fields appear.

The ```Protocol``` field in the ```Internet Protocol Version 4``` subtree indicates which IP internal protocol is contained in the packet.

```What is the protocol contained in the Internet Protocol Version 4 subtree from the first packet related to MAC address 42:01:ac:15:e0:02?```

```**Answer:** TCP is the internal protocol contained in the first packet from MAC address 42:01:ac:15:e0:02.```

13. Click the ```X``` icon to close the detailed packet inspection window.

14. Click the ```X Clear display filter``` icon in the Wireshark filter bar to clear the MAC address filter.

## Task 4. Use filters to explore DNS packets
In this task, you’ll use filters to select and examine DNS traffic. Once you‘ve selected sample DNS traffic, you’ll drill down into the protocol to examine how the DNS packet data contains both queries (names of internet sites that are being looked up) and answers (IP addresses that are being sent back by a DNS server when a name is successfully resolved).

1. Enter the following filter to select UDP port ```53``` traffic. DNS traffic uses UDP port ```53```, so this will list traffic related to DNS queries and responses only. Enter this into the ```Apply a display filter...``` text box immediately above the list of packets:

```
udp.port == 53
```

2. Press ```ENTER``` or click the ```Apply display filter``` icon in the filter text box.

3. Double-click the first packet in the list to open the detailed packet window.

4. Scroll down and double-click the ```Domain Name System (query)``` subtree to expand it.

5. Scroll down and double-click ```Queries```.

You’ll notice that the name of the website that was queried is ```opensource.google.com```.

6. Click the ```X``` icon to close the detailed packet inspection window.

7. Double-click the fourth packet in the list to open the detailed packet window.

8. Scroll down and double-click the ```Domain Name System (query)``` subtree to expand it.

9. Scroll down and double-click ```Answers```, which is in the ```Domain Name System (query)``` subtree.

The Answers data includes the name that was queried **(```opensource.google.com```)** and the addresses that are associated with that name.

```Which of these IP addresses is displayed in the expanded Answers section for the DNS query for opensource.google.com?```

```**Answer:** The IP address 142.250.1.139 is displayed in the expanded Answers section for the DNS query for **opensource.google.com.**```

10. Click the ```X``` icon to close the detailed packet inspection window.

11. Click the ```X Clear display filter``` icon in the Wireshark filter bar to clear the filter.

## Task 5. Use filters to explore TCP packets
In this task, you’ll use additional filters to select and examine TCP packets. You’ll learn how to search for text that is present in payload data contained inside network packets. This will locate packets based on something such as a name or some other text that is of interest to you.

1. Enter the following filter to select TCP port ```80``` traffic. TCP port ```80``` is the default port that is associated with web traffic:
```
tcp.port == 80
```
2. Press ```ENTER``` or click the ```Apply display filter``` icon in the filter text box.

Quite a few packets were created when the user accessed the web page ```http://opensource.google.com```.

3. Double-click the first packet in the list. The ```Destination IP``` address of this packet is ```169.254.169.254```.

```What is the Time to Live value of the packet as specified in the Internet Protocol Version 4 subtree?```

```**Answer:** The Time to Live value is 64. This property is contained in the Internet Protocol Version 4 subtree, which is the third subtree listed in the detailed packet inspection window.```

```What is the Frame Length of the packet as specified in the Frame subtree?```

```**Answer:** The Frame Length is 54 bytes. This property is contained in the Frame subtree, which is the first subtree listed in the detailed packet inspection window.```

```What is the Header Length of the packet as specified in the Internet Protocol Version 4 subtree?```

```**Answer:** The Header Length is 20 bytes. This property is defined in the Internet Protocol Version 4 subtree, which is the fourth subtree listed in the detailed packet inspection window.```

```What is the Destination Address as specified in the Internet Protocol Version 4 subtree?```

```**Answer:** The Destination Address is 169.254.169.254. This property is defined in the Internet Protocol Version 4 subtree, which is the third subtree listed in the detailed packet inspection window.```

4. Click the ```X``` icon to close the detailed packet inspection window.

5. Click the ```X Clear display filter``` icon in the Wireshark filter bar to clear the filter.

6. Enter the following filter to select TCP packet data that contains specific text data.
```
tcp contains "curl"
```
7. Press ```ENTER``` or click the ```Apply display filter``` icon in the filter text box.

This filters to packets containing web requests made with the curl command in this sample packet capture file.

## Conclusion

You now have practical experience using Wireshark to

- open saved packet capture files,

- view high-level packet data, and

- use filters to inspect detailed packet data.
