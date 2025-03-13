1. It is allowed to have two DHCP servers in the same subnet. O
-> 동일 서브넷에서 두 개의 DHCP 서버를 운영하는 것은 가능하지만, 충돌을 방지하기 위해 DHCP 범위가 겹치지 않도록 구성해야 합니다. 
2. In NAT(Network Address Translation), each host in the private network must use a unique (private) IP address. O
-> NAT는 내부 네트워크에서 고유한 사설 IP를 사용하여 외부와 통신을 가능하게 합니다.
3. The best effort service is the default network layer service of Internet. O
-> 인터넷은 데이터그램 전송에 대해 품질 보장을 하지 않는 "best-effort" 서비스를 기본으로 제공합니다.
4. In the router, packet drops usually occur in the output port queue. O
-> 출력 포트 큐에서 패킷 전송률이 초과되면 혼잡으로 인해 패킷 드롭이 발생할 수 있습니다.
5. Only hosts generate ICMP messages and routers do not generate ICMP messages. X
-> 둘 다 함
6. QUIC runs on top of HTTP X
-> 둘 다 Application layer http3가 quic위 
7. In IPv6 packet header, the source address is 64bit long. X
-> 128 bit임 IPv4는 32bit
8.  ‘Tail drop’ is the most popular packet discard policy of the today’s Internet routers. O
-> 널리쓰인다고함.
9. If the router buffer size is sufficiently large, large queuing delay does not occur. X
-> 버퍼 커지면 손실이 없지만 지연은 오히려 커진다.
10. Even if WFQ(Weighted Fair Queuing) is used, router buffer overflow cannot be prevented. O
-> 이거는 순서관리하는거지 buffer overflow를 관리해주는건 아님.
11. In IPv4, IP packet fragmentation/reassembly may occur at the intermediate routers. X
-> IPv4에서는 경로의 라우터에서 패킷을 분할하지만 조립은 마지막에서만 한다. 
 12. The forwarding table of a router may contain multiple entries corresponding to the same destination IP subnet. O
 -> 라우터의 포워딩 테이블은 동일한 목적지 서브넷에 대해 여러 항목을 가질 수 있으며, 가장 긴 접두사 매칭이 사용됩니다.
 13. In IP-in-IP encapsulation, the destination addresses of the two IP headers (i.e., inside and outside header) must be different. O
 -> 달라야한다.
 14. The destination address of the DHCP ‘offer’ message is always set to ‘255.255.255.255’. O
->그렇대요 
15. The routing table may contain multiple entries corresponding (i.e., matched) to the same destination IP address. O
-> 라우팅 테이블은 같은 목적지 IP 주소에 대해 여러 항목을 포함할 수 있습니다. "Longest Prefix Matching" 규칙에 따라 가장 구체적인 항목이 선택됩니다.
16. 'Poisoned reverse’ cannot prevent all possible loops in distance-vector routing. X
-> 다 막지는 못한다
17. In OSPF protocol, ‘route oscillation’ is possible. O
-> 진동 발생할 수 있다.
18. ‘Counting-to-infinity’ problem may occur in the BGP routing. X
-> BGP는 path-vector protocol이다. counting to infinity는 distance-vector에서 발생한다.
19. SNMP protocol and NETCONF protocol are used for network management. O
-> 네트워크 모니터링에서 SNMP, NETCONF 사용된다.
20. Both intra-AS and inter-AS routing protocols insert the routing entries into the routing table of the (AS) interior routers. O
-> ,,당연한거아닌가?
21. ‘Openflow’ is a routing protocol used by SDN routers. X
-> 라우팅 프로토콜이 아니다. 포워딩 테이블을 관리하는 프로토콜.
22. The BGP protocol finds a shortest path between two hosts which belong to different ASs. X
-> 이건 짧은 길을 찾는 프로토콜이 아니다.
23. The SDN controller must be implemented as a single physical server. X
-> 분산서버도 가능
24. The ‘traceroute’ program utilizes ICMP messages. O
-> ICMP를 이용하여 목적지까지의 경로를 확인한다.
25. From BGP we cannot obtain the hop count of a path (i.e., number of routers on a path) between two nodes belonging to two different ASs. O
-> BGP는 그런거 몰라요. AS-path정보만 제공한다.
26. 20. Slotted ALOHA is more efficient (i.e., higher average link utilization rate) than CSMA/CD. X
-> CSMA/CD는 충돌을 줄이고 채널 이용 효율을 높이기 위한 메커니즘(충돌 감지 및 재전송 알고리즘)을 포함하므로 Slotted ALOHA보다 효율적입니다. Slotted ALOHA의 최대 효율은 약 37%인 반면, CSMA/CD는 더 높은 효율을 제공한다. 보통 뒤에 나온게 더 효율적이다. 
27. Ethernet switch builds (via self-learning) a switching table by learning the IP addresses of exchanged Ethernet frames. X
-> 이더넷 스위치는 MAC 주소를 학습한다.
28. In the Ethernet switch, the received MAC frame is decapsulated and a new MAC frame is created to send. O
-> 이더넷 스위치는 수신된 MAC 프레임을 캡슐화 해제하고(디캡슐화), 목적지에 맞는 새 프레임을 생성하여 송신합니다. 이는 스위칭의 핵심 동작입니다.
29. Slotted ALOHA does not perform carrier sensing before starting transmission. O
-> Slotted ALOHA는 슬롯 기반 전송 방식으로 carrier sensing을 수행하지 않습니다. 노드들은 슬롯이 시작되면 충돌 가능성을 고려하지 않고 전송을 시작합니다.
30. With DSL (Digital Subscriber Line), you can access Internet and use telephone at the same time. O
-> DSL은 전화선의 주파수 대역을 분리하여 인터넷 데이터와 음성 통신을 동시에 사용할 수 있도록 합니다.
31. Ethernet switch builds a forwarding table via learning the IP addresses of exchanged packets. X
-> MAC 주소 학습
32. When a collision occurs in Ethernet, the lost packet is automatically retransmitted. X
-> 이더넷은 충돌이 발생하면 해당 프레임은 폐기되고, 재전송은 상위 계층(예: TCP)에서 처리됩니다.
33. At each MPLS link, the labels of the different MPLS flows must be different. O
-> MPLS 네트워크에서는 동일 링크 상에서 **라벨 값**이 중복되지 않도록 보장해야 각 패킷을 올바르게 처리할 수 있습니다.
34. In MPLS network, non-shortest path routing may be allowed. O
-> MPLS는 트래픽 엔지니어링을 지원하며, 짧지 않은 경로를 선택하여 대역폭 사용을 최적화할 수 있습니다.
36. The MPLS switch should not change the MPLS header of packets which is received from the previous MPLS switch. X
-> MPLS 스위치는 각 링크에서 **라벨 스위칭**을 수행하며, 필요하면 패킷의 라벨을 변경합니다.
37. Hidden terminal problem may cause collisions. O
-> 당연
38. A TCP sender never sends any segment outside its congestion window. O
-> TCP 송신자는 절대 CWND 범위를 초과하여 세그먼트를 전송하지 않습니다.
39. When RTS frames collide in IEEE 802.11 network, stations conduct random backoff. O
-> 그렇다네요
40. In wireless communication, ‘path loss’ means the decrease of the radio signal strength as the signal propagates. O
-> 경로 손실(Path Loss)은 무선 통신에서 신호가 전파되면서 거리에 따라 신호 강도가 **감소**하는 현상을 나타냅니다.
41. In WiFi, collision detection is more difficult than in Ethernet. O
-> 어렵기 때문에 회피를 사용한다. CMSA/CA
42. In WiFi networks, RTS frames may collide with each other. O
-> 걍 당연히 충돌할 수 있음.
43. In the Ethernet switch, the received MAC frame is decapsulated and a new MAC frame is created to send. O
-> 이더넷 스위치는 수신된 MAC 프레임을 캡슐화 해제하고(디캡슐화), 목적지에 맞는 새 프레임을 생성하여 송신합니다. 이는 스위칭의 핵심 동작입니다.
44. In CSMA/CD, T_trans should be larger than (2T_prop), where T_prop = max propagation delay between two nodes and T_trans = the time to transmit a max-size frame. O
-> 충돌 검출(Collision Detection)을 보장하기 위해, 전송 시간(T_trans)은 신호가 네트워크에서 왕복하는 데 걸리는 최대 전파 지연 시간(2T_prop)보다 길어야 합니다.

---------------------------------------------------
- LAN 링크 계층 네트워크에서는 IP주소를 사용하지 않고 링크 계층 주소(MAC 주소)를 사용한다.
- MAC 주소는 end system host router가 아니라 adapter이다. 
- Datagram을 전송할 때에는 ip주소와 mac주소를 모두 알아야 한다.
- wifi는 csma/ca사용, 2.4/5 GHz대역, mimo안테나 사용.
- ARP는 IP 주소에 대응되는 MAC 주소를 돌려준다.
- 이더넷은 핸드셰이킹 하지 않고, 비연결형이며 비신뢰적이다.
- 이더넷은 데이터그램이 손실되었는지 UDP 를 사용하면 알 수 없고 TCP를 사용하면 알 수 있다.
- 이더넷은 데이터그램이 재전송인지 새로운지 알 수 없다.
- 스위치 기반 이더넷 LAN에는 충돌이 없다. 
- 라우터는 네트워크 레이어, 스위치는 링크 레이어, 저장 후 전달 패킷 스위치.
- 라우터는 플러그앤 플레이 아니며 스위치는 플러그앤 플레이.
- MPLS 헤더는 MPLS 가능 라우터들 사이에서 전송된다. 패킷의 IP 헤더를 보지 않고, 건드리지 않고 동작한다.
- ssthresh값은 1/2 of cwnd. just before loss event
- congestion window가 ssthresh값을 달성할 때, switch
- fast retransmit일 때, ssthresh는 1/2 cwnd
- 802.11 수동적/능동적 스캐닝
- collision 감지가 아니라 회피한다.
- mac을 주고받는거는 apa인가 apr인가 그거 dns랑 비슷하다.
- rts랑 cts도 ack주고받는거랑 비슷하다.

-----------------------------------------------------
1.  (6 points) The (instant) ‘throughput’ of a TCP connection is determined by ‘CWND(congestion window size)’ and ‘RTT(round trip time)’ at that moment. Write a simple equation between these three values (throughput, CWND, RTT).
-> throughput = cwnd / rtt
2. Give a case when the ‘ss-thresh’ increases in TCP reno.
-> when the network conditions improve after a timeout or packet loss. connection stabilizes and congestion window cwnd grows, ss-thresh is rest to a higher value.
3. (5 points) Does the ‘ss-thresh’ always decrease? If not, when would it increase?
-> In TCP Reno, when congestion is detected ss-thresh typically decreases. upper problem. 
4. Explain how ARP(Address Resolution Protocol) is used for a computer to send an IP packet to its subnet router
-> 컴퓨터는 목적지의 IP 주소가 다른 서브넷에 있다는 걸 확인하고 packet을 서브넷 게이트웨이로 보내야한다. 컴퓨터는 arp 캐시에서 기본 게이트웨이의 mac주소를 확인하고 전송한다. 만약에 arp 캐시에 mac 주소가 없으면 arp 요청을 브로드캐스팅한다. 이 요청에는 기본 게이트웨이의 ip주소가 포함된다. 기본 게이트웨이는 자신의 ip 주소와 일치하는 arp요청을 받고, arp 응답으로 자신의 mac주소를 컴퓨터에게 보낸다. 컴퓨터는 mac주소를 사용하여 ip 패킷을 mac 주소로 캡슐화 한 후 전송한다. arp는 기본 게이트웨이의 ip 주소를 mac주소로 변환한다. 
5. (6 points) Suppose that a host (H1) sends to an IP packet to a host (H2) which locates in a different subnet from H1. Which is used as the destination MAC address to encapsulate the IP packet at the H1: (i) the MAC address of H2, (ii) the MAC address of the default gateway of H1, or (iii) the MAC address of the default gateway of H2? 
-> (ii) the MAC address of the default gateway of H1
6. (6 points) Suppose that a router has the following routing table. What is the range of destination host addresses associated to the link interface 2? 200.23.24.0/21 (11001000 00010111 00011*** ~)
-> 200.23.24.0 ~ 200.23.31.255
-> 200.23.24.0 ~ 200.23.24.255 뭐 이런식으로도됨
7. (6 points) The following graph shows the relationship between SNR and BER for different encoding schemes in wireless link. By using this graph, explain what happens when a mobile host approaches to the base station when the encoding scheme is fixed (e.g., QAM16).
-> SNR 신호강도는 강해진다. BER은 감소한다.
8. (6 points) In wireless networks such as WiFi, ‘dynamic rate adaptation’ is common. By using the above SNRBER graph, how transmission data rate is reduced as a mobile host moves away from the base station. (In this question, the encoding scheme is not fixed unlike the Question 29.)
-> SNR 신호강도 감소한다. BER 증가한다. BER 유지하려면 encoding scheme을 변경해야한다. 복잡도가 낮은 인코딩 방식으로 바꾸면 더 낮은 데이터 전송 속도를 제공하지만 잡음에 더 강하게 작동하여 BER을 줄일 수 있다.
9. Explain why it is not desirable to always use the highest speed encoding scheme (QAM256 in this example)
-> 자원의 비효율적 사용 때문에. 굳이 빡센거를 쓸 필요가 없다. 잡음이 많은 환경에서 오류율이 증가하기 때문이다.  highest speed encoding scheme는 SNR이 높을 때만 효율적이다. 무선 네트워크에서는 SNR이 변화하기 쉽기 때문에 이러한 조건 변화에 잘 적응해야한다.
10. (6 points) Briefly explain how ‘traffic engineering’ can be supported by using ‘generalized forwarding’
-> 트래픽 엔지니어링은 네트워크의 데이터를 최적화하여 성능을 개선하고 부하를 분산하며 자원을 효율적으로 사용하는 것을 목표로 한다. generalized forwarding은 control plane과 data plane을 분리한다. 그리고 policy based forwarding을 사용한다. 그리고 mpls같은 label 기반 포워딩을 활용한다. 
11. (6 points) Briefly explain the key characteristics of ‘data center networks’
-> high bandwidth, low latency, scalability, reliability, multi-tenancy
12. (5 points) Explain why CSMA/CD results higher throughput than Slotted Aloha.
-> 충돌 최소화하고 충돌을 감지하며 전송을 중단하고 재전송한다. 그리고 random backoff를 사용하여 충돌 가능성을 줄인다. 충돌과 대기 시간을 줄여 채널을 더 효율적으로 사용한다. 
13. (5 points) Explain what would happen if a computer has two network interfaces and the same IP address is assigned to both interfaces
-> 헷갈리겠지 병신아 local communication fail, gateway access fail, internet access fail, ARP request fail, network collision occurs.
14. (5 points) Explain why the entries of the router forwarding table are (typically) for network address range not for individual host IP address as shown in the previous question.
-> 메모리 효율성, 확장성, 빠른 경로 검색을 위해.
 15. (5 points) Explain ‘hot potato routing’ in BGP
 -> 라우터가 트래픽을 가능한 빨리, 가장 가까운 출구를 통해 외부 네트워크로 전달하려는 전략을 의미한다. 내부 자원 사용을 최소화 하고, 트래픽 지연을 줄인다. 최단 igp 비용을 기준으로 데이터 전송한다. 아무튼 최단 경로로 가장 가까운 출구로 보내려고.
16. Consider a three node network that uses distance vector routing as in the following figure. Briefly explain what will happen if the cost of the link between x and y changes from 4 to 60
-> 변한 부분 노드의 distance vector table 라우팅 테이블을 업데이트한다. 그리고 주변 노드에 업데이트를 전파한다. 