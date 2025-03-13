
# 1-1 Internet
인터넷
1. software & hardware 구성요소
2. application -> networking infrastructure aspect

Network of Network 
전 세계적으로 수십억개의 컴퓨팅 장치를 연결하는 컴퓨터 네트워크이다. 

## Host 와 end system
-> 컴퓨터 네트워크에 연결된 컴퓨팅 장치이다. 서버, 인터넷에 연결된 모든 사물들을 말한다. TV, 스마트폰, 스마트 워치 등 모든 것을 다 host, end system이라고 한다.
-> communication link와 packet switch의 network로 연결된다.

## communication link
-> 다양한 transmission rate와 bandwidth를 이용해 packet을 전송한다. 이때 packet은 data가 작게 나뉘어진 작은 단위를 말한다. 전송률의 단위는 bps(bits per second) 이다. 
**케이블, 구리선, 광케이블, 라디오 등 다양한 물리 매체**

## packet
-> 송신 종단 시스템에서 수신 종단 시스템으로 보내진다. (간단히 출발지에서 목적지로 보내진다는 말이다.) 보내고자 하는 데이터를 segment(세그멘트)로 나누고, 각 세그멘트에 header를 부착하여 목적지로 보내진다. 패킷은 나뉘어서 보내진 후에 목적지에서 원래 데이터로 다시 조립된다.

## packet switch
-> 통신 링크 중 하나이다. 도착하는 패킷을 받아서 출력 통신 링크의 하나로 그 패킷을 전달한다. 출발지에서 목적지까지 한방에 도착하는 것이 아니다. 중간 중간에 수많은 packet switch가 존재한다. 최종 목적지 '방향' 으로 packet을 전달하는 것이다.
- **router** -> network core에서 사용
- **link-layer switch** -> 보통 접속 네트워크에서 사용한다. 

## route, path
packet은 송신 종단 시스템 (end system) 에서 수신 종단 시스템(end system) 으로 가는 길에 많은 communication link와 packet switch를 거친다. 이것이 경로이다. packet은 computer network 를 통한 경로를 따른다. (path route)

## ISP(Internet Service Provider)
isp는 packet switch와 communication link로 이루어진 network이다. end system 들에게 다양한 네트워크 접속을 제공한다. (가정용 점속, 고속 lan, 무선 접속) 그리고 Content provider(웹사이트 나 application 을 만드는 제공자) 에게 인터넷 접속을 제공한다. 인터넷은 종단 시스템을 서로 연결하는 것이므로, 종단 시스템에 접속을 제공하는 isp들 끼리도 당연히 접속해야만한다.
상부 계층 isp는 국가나 국제단위의 isp들이고, 하위 계층 isp는 상부 계층 isp를 통해 서로 연결한다. 상부 계층 isp는 직접 서로 연결되어있다. isp network는 따로 관리되고, ip protocol 을 수행한다. 

## Protocol
통신 규약
그래서 프로토콜이 무엇인가?
end system끼리 packet을 주고받으며 통신을 하는 것은 사람의 대화와 비슷하게 볼 수 있다. 통신하는 둘 이상의 원격 개체가 포함된 인터넷에서의 모든 활동은 프로토콜이 제어한다. 
ex) congestion-control protocol / router protocol
한마디로 규칙이다. 
### TCP/IP
TCP = Transmission Control Protocol
IP = Internet Protocol (router와 end system 사이에서 송수신되는 패킷 포맷을 기술한다)

## Service aspect internet
-> 인터넷은 application 에 서비스를 제공하는 infrastructure 이다. application 은 서로 data를 주고받는 많은 end system을 포함하고 있기 때문에 distributed application 이라고 부른다. 인터넷 애플리케이션은 end system 에서 수행된다. network core 에 있는 packet switch에서 실행되지 않는다. packet switch는 data 교환에만 관여할 뿐 end system 에서 사용되는 application 에는 관심을 가지지 않는다.

+socket interface
한 end system 에서 실행되는 프로그램이 다른 end system에서 수행되는 프로그램으로 데이터를 전달하도록 어떻게 internet infrastructure에게 요구하는지를 명시하는 것.
-> 송신 프로그램이 따라야 하는 규칙의 집합

# 1-2 Acess Networks
## access network
end system을 다른 end system까지 경로상의 가장 첫 번째 라우터(edge router)에 연결하는 네트워크를 말한다.
->가정 접속 (dsl, 케이블, ftth, 5g)
-> 기업(가정) 접속 (이더넷, 와이파이)
-> 광역 무선 접속 (3g, lte, 4g, 5g)

DSL -> 지역 전화 회사 전화 인프라 이용
케이블 -> 케이블 TV 인프라 이용

## DSL(Digital Subscriber Line)
가정은 유선 로컬 전화 서비스를 제공하는 지역 전화 회사로부터 DSL 서비스를 받는다. (전화선을 이용한다는 말이다.)
기존 전화 회선을 통해 데이터를 교환하려고 한다. 가정의 DSL 모뎀은 수신한 디지털 데이터를 전화선을 통해 전송하기 위해(Central office로) 데이터를 고주파 신호로 변환한다. 이런 아날로그 신호는 DSLAM 에서 디지털 포맷으로 다시 변환된다. 

주파수 분할 다중화(Frequency Division Multiplexing FDM)를 이용한다. 전화 신호와 데이터를 동시에 전달하는데, 다른 주파수 대역에서 인코딩 된다. 주파수 분할 다중화를 통해 DSL링크가 분리된 링크인 것으로 보인다. 이를 통해 하나의 전화 회선과 인터넷 연결이 동시에 DSL 링크를 공유할 수 있게 된다. 

splitter는 가정 쪽에 존재하는데, 데이터와 전화 신호를 분리하고 데이터 신호를 DSL 모뎀으로 전송한다.

DSLAM은 데이터와 전화 신호를 분리하고 데이터를 인터넷으로 송신한다. 다운스트림이 많이 빠르고, 업스트림이 상대적으로 느리다. 전화 채널이 제일 느리다. 다운스트림과 업스트림의 속도가 다른 것을 비대칭이라고 한다.

## HFC(Hybird Fiber Coax)
가정은 케이블 tv 서비스를 제공하는 같은 회사로부터 인터넷 접속 서비스를 받는다. 
head-end는 유선 tv의 전파를 중계하는 것..? 각 데이터 국으로부터 수신된 신호를 가공 증폭 후 분배 하는 시설.

케이블 모뎀
케이블 인터넷 접속을 위한 모뎀이고 이더넷 포트를 통해 가정 pc에 연결된다. hfc네트워크를 다운스트림과 업스트림 채널 2개로 나눈다. 

CMTS(Cable Modem Termination System)
많은 다운스트림 가정에 있는 케이블 모뎀으로부터 송신된 아날로그 신호를 다시 디지털 포맷으로 변환하는 역할.(dslam 이랑 비슷한거.)

(여러 사용자가 다운스트림 채널에서 **다른** 비디오 파일을 동시에 수신하고 있다면,  각 사용자가 비디오 파일을 수신하는 실제 수신율은 **다운스트림 전송률보다 작아진다.** 몇 명만 접속 중이며 모두가 웹을 탐색 중이라면, 각 사용자는 **전체 다운스트림 전송률로** 웹 페이지를 수신할 수도 있다.)
->중요한 것 같은데 뭔소린지 모르겠어서 일단 넘어감

## FTTH(Fiber to the home)
지역 중앙국은 가정까지 직접 광섬유 경로를 제공한다.
direct fiber(말그대로)

AON(Active Optical Network)
PON(Passive Optical Network)

# 1-3 Network Core
## packet switching
end system 끼리는 message를 교환하는데 이때 교환하는 것을 packet이라고 하며, 작은 데이터 덩어리이다. communication linck와 packet switch를 거친다. packet은 링크의 최대 전송률과 같은 속도로 전송된다. R bps(bits per second) 그 패킷을 전송하는 데 걸리는 시간은 L/R초.

## Store and forward transmission
스위치가 패킷의 첫 비트를 출력 링크로 전송하기 전에 전체 패킷을 받아야한다. 패킷은 데이터 쪼가리로, 여러개로 나뉘어져서 보내지는데, 이때 전체 패킷이 도착해야만 그 다음 장소로 보낸다는 뜻이다. 패킷의 비트를 먼저 packet switch에서 buffer에 보관한다.

계산-> N개의 링크가 있다면, N-1개의 라우터가 존재한다는 뜻이다. end system간의 지연(걸리는 시간)은 N * L/R이 된다.

## Queuing delay, packet loss
packet switch는 접속된 여러 링크를 가지고 있다. 각 링크에 대한 output buffer를 가지고 있다. 이건 output queue라고도 불린다. 그 링크로 송신하려고 하는 packet을 저장하고 있다. 
내가 만약에 packet을 한 링크로 보내려고 했는데, 그 링크가 다른 패킷을 보내고 있다면, 도착하는 패킷은 output buffer에서 대기해야한다. 이게 바로 queuing delay이다. 이는 가변적이다. buffer의 크기는 유한하기 때문에 packet loss가 발생할 수도 있다. buffer가 꽉 차 있는 경우라면 도착하는 packet 또는 대기중인 packet을 폐기하게 된다. router는 수신한 packet을 15Mbps의 링크로 전달하고 있을 때, router에 도착하는 packet의 전송률이 15Mbps를 초과하게 된다면, output buffer에 packet들이 쌓이게 된다. 

## Forwarding table / routing protocol
라우터가 링크를 선택하는 결정 기준?
모든 end system은 ip 주소를 가지며 이 주소는 계층적인 구조를 갖는다. end system에서 end system으로 패킷을 보내고자 할 때, 출발지는 packet의 header에 목적지의 ip 주소를 포함시킨다. 
forwarding table은 목적지의 주소 - 라우터의 출력 링크 가 매핑 된 것을 말한다. packet이 router에 도착 -> 라우터가 packet의 ip 주소를 조사 -> ip 주소에 매핑 된 출력 링크를 forwarding table에서 검색 -> 그 packet을 출력 링크로 보낸다. 
routing protocol은 forwarding table을 설정한다. 각 라우터로부터 목적지까지 최단 경로를 설정하고 이 최단 경로의 결과를 이용하여 forwarding table을 설정한다.

## Circuit Switching
circuit switching network에서는 end system 간의 통신을 제공하기 위해 경로 상에서 필요한 자원은 통신 세션 동안에 확보 또는 예약된다. "예약"이 제일 중요하다. 
송신자가 정보를 보내기 전에 네트워크는 연결을 설정해야한다. 네트워크가 회선을 설정할 때, 그 연결이 이루어지는 동안 네트워크 링크에 일정한 전송률을 예약한다. 예약되면 보장된 전송률로 데이터를 보낼 수 있다. 연결이 미리 설정되어있어야 한다는 뜻이다. 이 연결을 circuit이라고 한다. 네트워크가 circuit을 설정할 때, 네트워크의 링크에서 일정한 전송 속도를 예약한다. 링크에 circuit이 4개라면, 그 circuit 하나의 전송 속도는 링크의 1/4가 되게 된다. 

## Multiplexing in circuit switching network
주파수 분할 다중화 (Frequency Division Multiplexing)
-> 각 circuit은 지속적으로 대역폭의 일부를 얻는다.
-> 링크를 통해 설정된 연결은 그 링크의 주파수 스펙트럼을 공유한다. 각 연결에 대해 주파수 대역을 고정 제공한다. 대역폭 = bandwidth
시분할 다중화 (Time-Division Multiplexing)
-> 각 회선은 주기적으로 전체 대역폭을 얻는다. 
-> TDM은 시간을 일정 주기의 프레임으로 구분하고, 각 프레임은 고정된 수의 시간 슬롯으로 나뉜다. 네트워크는 모든 프레임에서 시간 슬롯 1개를 연결에 할당한다. 전송률 = 한 슬롯안의 비트 수 * 프레임 전송률

## Packet switching VS Circuit switching
패킷 교환은 효율적이다 하지만 실시간의 서비스에 적당하지않다. 예약이라는 제도 자체가 자원을 점유한다는 것이기에 좋지 않다. 구현 비용이 적다. Circuit switching에선 사용되지 않는 네트워크 자원을 사용할 수 없다. 하지만 패킷 교환은 종단 지연 등 불규칙적이다.

하지만 걍 패킷 교환이 더 좋다. 우수하다. 

## Network of Networks
ISP(Internet Service Provider) packet switch와 communication link로 이루어져있다.

Access ISP
-> end system / content provider에게 접속을 제공한다.
-> end system들은 access isp를 통해 인터넷에 연결된다.
-> access isp는 다양한 접속 기술을 이용하여 유,무선 연결을 제공한다. 전화 회사나 케이블 회사일 필요 없다.
하지만 모든 사람이 같은 isp로 연결될 수 없고, 여러가지 access isp가 구동되며, 서로 연결되어야 하기 때문에 network of networks가 탄생하였다.

결국 모든 end system이 서로에게 packet을 보내야한다. 

구조 1
-> 모든 access isp 들을 하나의 global isp와 연결한다. 딱 하나. 당연히 빡세겠죠. global isp는 각각의 access isp에 과금을 부과한다. 비용이 많이 든다.
구조 2
-> global isp 가 여러개 생긴다. 그리고 걔네가 경쟁을 한다. 상위층에 global isp 가 존재하고, 하위층에 access isp가 존재한다. global isp들 끼리는 당연히 서로 연결되어야 한다.
구조 3
-> 다중 계층 구조 access isp -> regional isp -> tier-1 isp
구조 4
->pop(points of presence)  access isp 수준에는 존재하지 않는다. 고객 isp가 제공자 isp에 연결할 수 있는 제공자 네트워크 내의 한 장소에 위치한 하나 이상의 라우터 그룹을 의미한다..???? 뭔소리지
-> multi home 둘 이상의 provider isp에 연결할 수 있다. access isp 는 두 개의 regional isp 에 멀티홈을 하거나 뭐 아무튼 여러 isp에 연결 가능하다. 하나 고장 나도 계속 인터넷을 할 수 있다.
->peering 은 비용을 줄이기 위해 서로 상부상조 돈을 서로 안낸다는 것이다. 
-> ixp 는 다중의 isp들이 서로 피어링 할 수 있는 장소이다. 독자적으로 존재한다. 자체 switch가 있다. 
구조 5
-> 지금까지 있었던 거에다가 content provider network 가 추가된다. 구글은 공중 인터넷과 분리되어 있다. tcp/ip protocol을 따르며 전 세계를 연결하고 분리되어 있다. 구글 사설 네트워크는 구글 서버로 오가는 트래픽만 전달한다. 하위 isp들과 직접 peering함으로서 상위 계층을 bypass한다. 이렇게 함으로써 content provider는 상위 isp에게 지불하는 요금을 줄인다. 최종 사용자들에게 서비스 제공에 대한 통제권을 가질 수 있다. 

# 1-4 Delay, Loss, and Throughput in Packet-Switched Networks

total nodal delay
upstream(클라이언트->서버)
downstream(서버->클라이언트)
## processing delay
packet header를 조사하고, 어느 링크로 보낼 지 판단하는데 걸리는 시간. upstream node에서 packet의 bit level error 조사. router는 이 upstream node를 처리하고, router B에 이르는 링크로 보내는 buffer 에다가 저장한다. 
// 전체 노드 지연에서는 무시될 수 있다. 라우터가 패킷을 전달할 수 있는 최대 속도에는 상당한 영향을 준다.
## queuing delay
packet이 queue에서 link로 전송되기를 기다리는 시간. queue가 꽉 차 있거나 트래픽이 많으면 문제다. 이건 링크로 가기 전이다.
## transmission delay
packet이 모든 비트를 링크로 밀어내는 데 걸리는 시간. 쪼개져서 가는데, 전부다 가려면 시간 걸린다. L/R
//10Mbps이상 전송률일경우 무시가능, 저속 다이얼업 모뎀 링크에서 보내지는 인터넷 패킷은 수백 밀리초 가능
## propagation delay
router A 상에서의 링크에서 router B 까지의 전파에 필요한 시간. 전파 지연. link의 전파 속도로 전파된다. 물리 매체에 따라 다르게 된다. d/s
//작은거리는 무시가능, 위성으로 연결된거면 수백밀리초

queuing delay는 queue에서 이제 전송을 시작하는데 걸리는 시간을 말하는 것. transmission delay는 router 가 packet을 내보내는 데 걸리는 시간, propagation delay는 one router 에서 next router로 전파되는데 걸리는 시간.

전부 다 합치면 total node delay가 된다.

## Queueing delay(1.4.2계산)
다른 세가지 지연은 그렇지 않지만 queueing delay는 packet마다 다르다. queueing delay는 계산할 때 통계를 사용한다.queueing delay는 트래픽이 큐에 도착하는 비율, 링크의 전송률, 도착하는 트래픽의 특성에 따라 다르다.

패킷이 큐에 도착하는 평균율 a packet/s
전송률 R bit/s
패킷 크기 L bit
La/R bit/s (트래픽 강도(traffic intensity) = 비트가 큐에 도착하는 평균율)

La/R >1 이면 비트가 큐에 도착하는 평균율이 비트가 큐에서 전송되는 비율
La/R <= 1 이면 도착 트래픽의 특성이 큐잉 지연에 영향을 미친다. 하나의 패킷이 L/R 초마다 주기적으로 도착한다면 모든 패킷은 빈 큐에 도착 -> 큐잉 지연은 없을 것이다. 하지만 몰려서 도착한다면 존재한다. 

패킷은 random 하게 도착하게 된다. 트래픽 강도에 대한 평균 큐잉 지연의 질적 의존도를 그래프로 나타내면 지수함수 형태를 띄게 된다. 트래픽 강도가 0에 가까울 경우 평균 큐잉 지연은 0에 가까워진다. 1에 가까울 경우 패킷 도착이 전송용량을 초과하여 큐가 생성될 것이다.

## Packet loss
queue는 무한대 패킷을 가질 수 없다. 유한한 용량을 가지기 때문에 당연히 손실이 일어날 수 있다. 
손실 패킷의 비율은 트래픽 강도가 클수록 증가한다. 손실 패킷은 end system 간에 재전송 될 수 있다.

delaying rate
packet loss possibility

## End to End delay
n-1개의 라우터 / 큐잉 지연 무시 / 전송률 R bps / packet L bit

end to end delay = N(처리 지연 + 전송 지연 + 전파 지연)
d_dead-to-end = N * L/R

## Throughput(처리율)
file 전송하는 상황 생각 F bit
Host B가 모든 F bit를 수신하는데 T초가 걸린다면, instantaneous throughput 는 호스트 B가 파일을 수신하는 비율(bit/s) average throughput (F/T bit/s)
낮은 지연율과 순간적인 처리율이 지속적으로 어떤 threshold를 넘는 것이 바람직하다. (전화)
파일 전송을 포함하는 다른 어플리케이션의 경우 가능한 높은 처리율을 가져야한다. 

라우터를 여러개 거치면서 전송을 하려면 그중에 가장 속도가 낮은 전송률을 따라간다. 처리율 = min{R1, R2, … , RN} = 서버와 클라이언트 간 경로상에서의 **병목 링크(bottleneck link)의 전송률

Rs 서버 접속 링크가 가지는 속도
Rc 클라이언트 접속 링크가 가지는 속도
R 링크 R의 전송률

R이 크다면, 다운로드에 대한 처리율은 min{Rs, Rc}가 된다. 다만 비슷한 수준이라면, R/N(연결된 서버 수) 이 된다.

# 1-5 Protocol Layers and Their Service Models

계층구조에서 각 계층은 그 계층에서 어떤 동작을 취하고, 그 계층 바로 아래 계층 서비스를 이용함으로서 서비스를 제공한다. protocol stack
## Internet protocol stack
physical -> link -> network -> transport -> application
### application 계층
HTTP : 웹 문서 요청과 전송 제공
SMTP : 전자 메일 전송 제공
FTP : 두 end system 간의 파일 전송 제공
DNS : Domain name server
데이터를 주고받는 동안 연결을 유지하도록한다
### transport 계층
클라이언트와 서버간의 애플리케이션 계층 메시지를 전송하는 서비스를 제공한다. segment.
transport protocol 전송이 완전하고 순서대로 도착하게 보장하는 것이다. 
TCP 
-> 애플리케이션에게 연결 지향형 서비스를 제공한다. 메시지 전달 보장과 흐름 제어를 포함한다. 혼잡 제어 기능을 사용한다. 
UDP 
-> 비연결형 서비스를 제공한다. 다른걸 제공하지않는다.

### network 계층 (ip 계층)
한 호스트에서 다른 호스트로 데이터그램을 라우팅 하는 책임을 진다. (ip의 전송 단위)
end system 들 간 일련의 packet switch를 통해 datagram을 라우팅한다. 
출발지 host에서 internet transport layer protocol은 ip 계층에서 전달된다. 
data를 인터넷 상에서 어디로 보낼지 결정한다. 주로 ip를 이용하여 보내는 것이다. 

## link 계층
link layer packet = frame
경로상의 한 노드에서 다른 노드로 packet을 이동하기 위해 network layer는 link layer service에 의존해야한다.
network layer는 datagram을 아래 link layer로 보내고, link layer는 datagram을 다음 노드에 전달한다. 다음 노드에서 link layer는 datagram을 상위 network 계층으로 보낸다. 

## physical 계층
이 계층의 프로토콜들은 링크에 의존하고, 링크의 실제 전송 매체에 의존한다. 프레임 내부의 각 비트를 한 노드에서 다음 노드로 이동 시킨다. 

## router vs link layer switch
라우터는 1~3 계층이고, link layer switch는 1~2 계층이다. 인터넷 라우터들은 ip 프로토콜을 구현하지만 link layer switch는 불가능하다.
호스트는 1~5를 모두 구현한다.

## Capsulation
송신 호스트에서 application layer message는 transport layer로 간다. transport layer에서 사용할 정보인 transport 헤더 정보를 더한다. transport-layer segment 는 application layer message + transport layer head 이렇게. transport layer segment 는 application layer message를 캡슐화한다. transport layer header는 오류 검출 비트, 정보들이 포함되어있다. 그리고 이 세그먼트를 network layer로 보낸다. network layer는 출발지와 목적지 end system 주소와 동일한 헤더 정보를 추가하여 network-layer datagram을 만든다. datagram은 link layer로 전달되고, link layer도 자신의 헤더 정보를 추가하여 link-layer frame을 만든다. 그리고 수신된 후에는 재구성되어야한다. 

# 1-6 Networks Under Attack
malicious 한 놈들. malware. spyware.

## DoS(Denial-of-Service)
네트워크, 호스트 등 다른 요소들 사용하지 못하게 한다. 웹, email, dns 서버 등 공격 받을 가능성이 있다.
### 취약성 공격(vulnerability attack)
올바른 순서의 패킷을 공격받기 쉬운 애플리케이션 혹은 운영체제에 보내면, 서버가 다운되거나 동작을 멈출 수 있다.
### 대역폭 플러딩(bandwidth flooding)
access link 가 동작하지 못하도록 packet을 보내서 서버에 도달하지 못하도록 만든다.

DDoS 공격은 수천개의 호스트를 이용하여 한 곳에 보내는 것이다. 서버가 전송률이 R이라면 R 속도로 보내면된다.

### 연결 플러딩(connection flooding)
목표 호스트에 반열림 혹은 전열림된 TCP 연결을 설정한다. 호스트는 가짜 연결을 처리하느라 바빠서 정상적인 연결을 받아들이는 것을 중단하게 된다. 

## Packet 탐지(sniffing)
인터넷 접속은 보안 취약성이 존재한다. 무선 전송장치의 근처에 수동적인 수신자 즉, packet sniffer를 위치시킴으로서 수신자는 전송되고 있는 모든 패킷의 사본을 얻을 수 있다. sniffer는 무선 뿐만아니라 유선에도 배치될 수 있다. malicious 친구들은 가로챈 packet을 분석하여 개인정보를 채간다. sniffer는 channel 에 packet을 삽입하지 않기 때문에 이를 탐지하기 어렵다. packet sniffing을 방지하려면 암호화가 필요하다. 

## 그 외
ip spoofing
-> 가짜 출발지 주소를 가진 패킷을 인터넷으로 보내는 능력
end-point authentication
-> 종단 인증
인터넷은 원래 **‘투명한 네트워크에 연결된 상호 신뢰할 수 있는 사용자 그룹’** 모델,  
즉 **보안이 필요 없는 모델**에 기반을 둔 방식으로 설계되었다. 상호 신뢰를 바탕으로 하고있다. 

# 1-7 History of Computer Networking and the Internet

## 1961~1972 packet switching invention

우선 인터넷 이전에 통신 네트워크는 전화망이었다. 이때 circuit switching을 사용하였고 별로였다. traffic이 일정하지 않았다. 그래서 packet switching이라는 방법을 만들어냈다. end system과 end system을 연결하는 첫 번째 host간 프로토콜(NCP-network control protocol)이 완성되어, application 을 개발할 수 있게 되었고, 전자메일 프로그램이 최초로 등장하였다. ARPAnet 노드 수 15.

## 1972~1980 internetworking, new and proprietary nets
ethernet은 1976년. ARPAnet 노드 수 200. proprietary nets = 기업적, 상업적, 독점적 용도
## 1980~1990 new protocols, a proliferation of networks(증식)
1983년 TCP/IP. 1982년 SMTP e-mail protocol. 1983 DNS. 1985 ftp. 1988 TCP congestion control.
national networks 생김.
# 1990, 2000s commercialization, the web, new applications
ARPAnet decommissioned(폐기됨). NSF가 상업적 이용에 대한 제한을 풂. 1990년 초에 웹이 나오면서 하이퍼텍스트, HTML, HTTP 등이 나옴. 1990년 말에 Web의 상업화가 시작됨. killer app 들이 나오기 시작하고, security가 대두됨. 50million host, 100 million + users.
## 2005 ~ present more new applications
18B devices(2007). smartphones(2007). broadband access, high-speed sireless access. facebook 2.5 billion users. sns emergence. service providers create their own networks. enterprises run their services in cloud.
# 2-1 Principles of Network Applications

반대쪽 end system 에서 동작하지만 네트워크를 통해 서로 통신하는 프로그램을 작성해야한다. 웹 application 에는 server와 client가 존재한다. client(사용자 host에서 실행되는 browser program)
중요한 것은 우리가 **router나 link layer switch처럼 네트워크 코어 장비에서 실행되는 소프트웨어까지 작성할 필요는 없다**는 점이다. 

## network application structure
### client-server architecture
서버는 **항상** 동작한다. 클라이언트라는 다른 호스트들로부터 서비스 요청을 받는다. 클라이언트는 서로 직접적으로 통신하지 않는다. **서버를 거쳐서 통신한다**. 서버는 잘 알려진 고정 IP 주소를 갖는다. 서버가 클라이언트로부터 오는 모든 요청에 더 응답하는 것이 불가능할 때, 많은 수의 호스트를 갖춘 데이터 센터가 강력한 가상의 서버를 생성하는 역할로 사용된다. 서버 "10만개"

### P2P 구조
항상 켜져있는 infrastructure server에 최소로 의존한다.
(블록체인) 대신에 애플리케이션은 peer라는 간헐적으로 연결된 호스트 쌍이 **서로 직접 통신하게 한다**. peer는 흔히 알려진 client이다. 데이터 센터 등이 필요 없으므로 비용이 효율적이다. 

## client-server process
client -> 통신을 초기화(다른 프로세스와 세션을 시작하려고 접속을 초기화) 하는 프로세스
server -> 세션을 시작하기 위해 접속을 기다리는 프로세스
요청을 보내는 쪽의 process를 client라고 하고, 요청을 받는 쪽을 server라고 한다. p2p에서는 서로 둘다 될 수 있다. 

## The Interface Between the Process and the Computer Network
process 는 socket을 통해 네트워크로 메시지를 보내고 받는다. process 가 집이면, socket은 문이다. socket은 application layer와 transport layer간의 interface이다.
network application이 internet에 만든 programing interface이므로, application 과 network사이의 API라고도 한다. application 개발자는 socket의 application layer에 대한 모든 통제권을 갖지만 socket의 transport layer에 대한 통제권은 거의 갖지 못한다. 

## addressing processes
process가 다른 수행되고 있는 다른 packet으로 process를 보내기 위해선 수신 process가 address를 가지고 있어야한다. 수신 process를 식별하기 위해서는 두 가지 정보가 필요하다. ip address / port 번호 가 필요하다. 

## application transport  service
transport protocol
-> data integrity / throughput / timing / security
### data integrity(신뢰적 데이터 전송)
-> packet loss가 발생할 수 있는데, 만약 **프로토콜이 보장된 데이터 전송 서비스를 제공**한다면 신뢰적 데이터 전송이라고 한다. transport protocol 이 이 서비스를 제공할 때, 송신 프로세스는 데이터를 소켓으로 보내고, 데이터가 오류없이 수신 프로세스에 도착할 것이라는 확신을 갖는다. transport protocol이 서비스를 제공하지 않을 때, 송신 프로세스가 보낸 데이터는 전혀 도착하지 않을 수도 있다. 이런것을 손실 허용 application 이라고 한다.

### throughput 
transport protocol은 명시된 속도에서 보장된 처리율을 제공한다. bandwidth-sensitive applications / elastic applications

### timing
transport protocol은 시간 보장을 제공할 수 있다. 
송신자가 소켓으로 내보내는 모든 비트가 수신자의 소켓에 100ms 내에 도착하게 할 수 있다. 실시간 application 에 사용된다.

### security
송신 host에서 transport protocol은 모든 데이터를 암호화할 수 있고, 수신 호스트에서 transport protocol은 모두 해독할 수 있다. 

## Transport Services Provided by the Internet

## TCP service
연결 지향형 서비스
**application layer message를 전송하기 전에 TCP는 client와 server가 서로 전송 제어 정보를 교환하게 한다.** 이 handshaking은 이 클라이언트와 서버에 packet이 도달할테니 준비하라고 알려주는 역할을 한다. 이 handshaking과정 이후에 두 프로세스의 소켓 사이에 TCP 연결이 존재한다고 말한다. 이 연결은 두 process가 서로에게 동시에 메시지를 보낼 수 있기에 전이중 연결이라고 한다.

신뢰적인 데이터 전송 서비스
통신 프로세스는 **모든 데이터를 오류 없이 올바른 순서로 전달하기 위해** TCP에 의존한다. TCP는 애플리케이션의 한 쪽이 바이트 스트림을 소켓으로 전달하면, 손실되거나 중복되지 않게 수신 소켓으로 전달한다.

혼잡 제어 방식
**네트워크가 혼잡 상태에 이르면 속도를 낮춘다.**

### Securing TCP
Vanilla TCP & UDP sockets  VS TLS

## UDP service
최소의 서비스 모델을 가진 간단한 transprot protocol 이다. 비연결형으로 handshaking과정이 없다. 비신뢰적인 데이터 전송 서비스를 제공한다. 혼잡 제어 방식도 포함하지 않는다. -> 프로세스의 속도 저하가 없다. 

### 한계
UDP와 TCP모두 처리율, 시간 보장 서비스를 제공하지 않는다. 시간 민감 애플리케이션 같은 경우에는 이러한 상황에 잘 대처할 수 있도록 설계되어있다. 하지만 지연이 과도할 때에는 보장이 없기 때문에 한계가 있다. 


## Application layer protocol
애플리케이션의 프로세스가 서로 메시지를 보내는 방법을 정의한다.
교환 메시지의 타입, 메시지 타입의 문법, 정보의 의미, 응답에 대한 규칙 등을 결정한다. 
웹, 전자메일, 디렉토리, 비디오 스트리밍, p2p 어플

# 2-2 Web and HTTP
웹은 on-demand 방식으로 사용자가 원할 때 원하는 것을 수신한다. 

## web page
object로 구성된다. 하나의 파일이다. html, jpeg, 자바스크립트 등으로 구성. 기본 html 파일과 여러 참조 객체로 구성된다. 기본 html 파일은 page 내부의 다른 객체를 그 객체의 url 로 참조한다. url은 객체를 갖고 있는 서버의 호스트 이름과 객체의 경로 이름을 갖고 있다. 

http://www.school.edu/picture.gif 
host 이름 www.school.edu
경로 이름 picture.gif

## web browser & client 
web browser 는 http의 클라이언트 측을 구현한다. browser과 client라는 용어를 혼용하여 사용한다. web server는 url로 지정할 수 있는 웹 객체를 가지고 있다. 
브라우저는 페이지 내부의 객체에 대한 HTTP요청 메시지를 서버로 보낸다.(HTTP request) 서버는 요청을 수신하고 객체를 포함하는 HTTP 응답 메시지를 보낸다. (HTTP response)

## HTTP and TCP
HTTP 는 TCP를 전송 프로토콜로 사용한다. 
1. HTTP 클라이언트는 먼저 서버에 TCP 연결을 시작한다. (TCP는 서버와 클라이언트 보고 연결하라고 약속하는 것.)
2. 연결이 이루어지면, browser와 server process는 각각의 socket interface를 통해 TCP로 접속한다.
3. 클라이언트는 http 요청 메시지를 소켓 인터페이스로 보내고, 소켓 인터페이스로부터 http 응답 메시지를 받는다. http 서버는 소켓 인터페이스로부터 요청 메시지를 받고 응답 메시지를 보낸다.
TCP를 통해 메시지를 보내면 TCP는 **신뢰적 데이터 전송 서비스를 제공**하므로 모든 HTTP 요청 메시지가 궁극적으로 서버에 도착한다. 

### stateless protocol
HTTP 서버는 client 에 대한 정보를 유지하지 않으므로, stateless protocol이라고 부른다. 무슨말이냐면, 같은 요청을 두 번 해도, 신경쓰지 않고 또 객체를 보낸다는 뜻이다. 

## Non-Persistent Connections & Persistent Connections

### Non-Persistent Connections
1. HTTP 클라이언트는 HTTP 기본 포트 80을 통해 서버로 TCP 연결을 시도한다. TCP 연결과 관련하여 클라이언트와 서버에 각각 소켓이 있게 된다.
2. HTTP 클라이언트는 설정된 TCP 연결 소켓을 통해 서버로 HTTP 요청 메시지를 보낸다. 이 요청에 객체 경로도 포함된다.
3. HTTP 서버는 TCP 연결 소켓을 통해 요청 메시지를 받는다. 저장 장치로부터 경로의 객체를 추출한다. 객체를 캡슐화하여 HTTP 응답 메시지에 넣어서 소켓을 통해 클라이언트로 보낸다.
4. HTTP 서버는 TCP 연결을 끊으라고 한다. 클라이언트가 응답 메시지를 올바로 받을 때 까지 끊지않는다.
5. HTTP 클라이언트가 응답 메시지를 받으면, TCP연결이 중단된다. 메시지는 캡슐화된 객체가 HTML 파일인 것을 나타낸다. 클라이언트는 응답 메시지로부터 파일을 추출하고 HTML 파일을 조사하여 JPEG객체에 대한 참조를 찾는다.
6. **참조되는 JPEG 객체에 대해 1~4단계를 반복한다.**


 HTTP 1.0 은 비지속 연결을 지원한다.
 RTT(round trip time) 란 작은 packet이 클라이언트로부터 서버까지 가고, 다시 클라이언트로 되돌아오는 데 걸리는 시간이다. 여러가지 지연을 포함한다.

브라우저가 웹서버에게 TCP 연결을 요청, 서버에서 응답 (1RTT). 클라이언트는 HTTP Request를 통해 다시 요청한다. 그리고 마지막으로 서버에서 HTML파일을 TCP 연결로 보내게 된다. (1RTT) 대략 총 응답 시간은 2RTT + HTML 파일을 서버가 전송하는 데 걸리는 시간 이다.

**단점**
각 요청 객체에 대한 새로운 연결이 설정되고 유지되어야 한다. TCP 버퍼가 할당이 되어야하고, TCP 변수들이 클라이언트와 서버 양쪽에 유지되어야 한다. 그리고 매번 2RTT를 필요로 한다.

### Persistent connections
HTTP 1.1 지속 연결에서 서버는 응답을 보낸 후에 TCP 연결을 그대로 유지한다. **같은 클라이언트와 서버 간의 이후 요청과 응답은 같은 연결을 통해 보내진다.** 하나의 TCP 연결을 통해 여러 웹 페이지를 보낼 수 있다. 이들 객체에 대한 요구는 진행 중인 요구에 대한 응답을 기다리지 않고 연속해서 만들 수 있다. HTTP 서버는 일정기간 사용되지 않으면 연결을 닫는다. HTTP 의 default 모드는 pipelining을 이용한 지속 연결을 사용한다.

## HTTP message format
RFC는 HTTP message format을 정의한다.

GET /somedir/page.html HTTP/1.1
Host: www.someschool.edu
Connection: close
User-agent: Mozilla/5.0
Accept-language: fr
각 줄은 CR(carriage return) 과 LF(line feed) 로 구별된다. 마지막 줄에 이어서 CR과 LF가 따른다.
첫 줄은 요청 라인이라고 부르고 이후의 줄들은 헤더 라인이라고 부른다
BLANK LINE에도 CR과 LF는 있다.

### HTTP request message
#### 요청 라인 (request line)
version sp status code sp phrase cr lf
방식(method) / URL / HTTP version field
-> GET / POST / HEAD / PUT /DELETE
#### 헤더 라인 (header line)
header field name: sp value cr lf
Host -> 호스트 명시(web proxy cache 에서 필요)
Connection -> 지속연결을 원하는지 비지속을 원하는지 전달. 
User-agent -> 서버에게 요청을 하는 브라우저 타입 명시
Accept-language -> 어떤 언어 버전을 원하고 있음을 나타낸다. 

### Blank line
cr lf 
#### 개체 몸체(entity body)
GET일때는 비어있고, POST일 때 사용 된다.
POST 는 사용자가 서버에 웹페이지를 요청하고 있으나, 웹 페이지의 내용은 사용자가 폼 필드에 무엇을 입력하는가에 따라 달려있다.
HEAD 는 GET과 유사하지만, 요청 객체는 보내지 않는다. 디버깅용이다.
PUT 은 웹 서버에 업로드할 객체를 필요로 하는 애플리케이션에서 사용된다.
DELETE는 사용자 또는 애플리케이션이 웹 서버에 있는 객체를 지우는 것을 허용한다.

### HTTP response message
#### 상태 라인과 상태 코드(status line / status code)
status line은 버전 필드와 상태 코드, 해당 상태 메시지를 갖는다. 
200 OK -> 요청 성공, 정보가 응답으로 보내졌다.
301 Moved Permanently -> 요청이 영원히 이동되었다. 이때, 새로운 URL은 응답 메시지의 Location 헤더에 나와있다.
400 Bad Request -> 서버가 요청을 이해할 수 없다.
404 NOT Found -> 요청한 문서가 서버에 존재하지 않는다.
404 HTTP Version Not Supported -> 요청 HTTP 프로토콜 버전을 서버가 지원하지 않는다.

#### Header line
Connection -> 클라이언트에게 메시지를 보낸 후 TCP연결을 닫을지 말지 결정한다.
Date -> HTTP 응답이 서버에 의해 생성되고 보낸 날짜와 시간을 나타낸다.
Server -> 메시지가 어떤 웹 서버에 의해 만들어졌는지 나타낸다.
Last-Modified -> 객체가 생성되거나 마지막으로 수정된 시간과 날짜를 나타낸다.
Content-Length -> 송신되는 객체의 바이트 수를 나타낸다.
Content-Type -> 개체 몸체 내부의 객체가 어떤 타입인지 나타낸다.

## interaction within user and server : cookie

web cache (프록시 서버)는 기점 웹 서버를 대신하여 HTTP 요구를 충족시키는 개체이다. 
웹 캐시는 자체의 저장 디스크를 갖고 있어, 최근 호출된 객체의 사본을 저장 및 보존한다. 
GOAL : satisfy client request without involving origin server

### proxy server 
1. 웹 브라우저는 웹 캐시와 tcp 연결을 설정하고 웹 캐시에 있는 객체에 대한 HTTP 요청을 보낸다.(서버랑 연결하는거랑 똑같음)
2. 웹 캐시는 객체의 사본이 저장되어 있는지 확인하고, **저장되어 있다면** 클라이언트 브라우저로 객체를 전송한다.
3. **없다면** 기점 서버로 TCP 연결을 설정한다.  이후 웹 캐시는 캐시와 서버간의 TCP 연결로 객체에 대한 HTTP 요청을 보낸다. 기점 서버는 웹 캐시로 HTTP 응답 메시지를 보낸다.
4. 웹 캐시의 객체를 수신할 때, 객체를 지역 저장 장치에 복사하고, 클라이언트 브라우저에 HTTP 응답 메시지를 보낸다.

캐시(cache) 는 요청과 응답을 모두 하는 클라이언트이면서 서버이다. original requesting client에게는 server의 역할을 하고, original server에게는 client의 역할을 한다. 

### web cache 사용 이유
-> client request에 대한 응답 시간을 줄일 수 있다. client와 cache 사이에는 높은 속도의 연결이 설정되어 있어 웹서버 캐시에 객체를 갖고 있다면 병목 현상을 줄일 수 있다. 
-> web cache는 한 기관에서 인터넷으로 접속하는 링크 상의 웹 트래픽을 대폭 줄일 수 있다.
-> 인터넷 전체의 웹 트래픽을 실질적으로 줄여준다.

### 성능 비교
institutional network 에서 high speed LAN을 사용한다고 가정하자. institutional network의 router와 Internet의 router가 15 Mbps link로 연결되어있다. 평균 객체 사이즈는 1 Mbits이다. 그리고 request rate는 평균적으로 15 request per second이다. HTTP request message 는 무시할정도로 작다. 또한, 접속 회선의 인터넷 부분 라우터가 **HTTP 요청을 전달하고 응답을 받을 때까지 평균 소요 시간**을 `2초`라고 가정하자.

total response time은 LAN delay + access delay(router 간의 delay) + internet delay 이렇게 총합이다.

traffic intensity는 La/R 로 계산한다. L은 큐에 도착하는 packet의 개수, a는 packet 한개의 비트수, R은 전송률이다. 그래서, LAN 의 delay는 15(request per second) * 1 Mbits/per request / 100 Mbps  = 0.15가 된다.(100 Mbps는 그냥 고속을 말함) access link(router - router) delay 는 15 * 1 / 15 = 1 이 된다.

결국 traffic intensity는 벌써 1을 넘어버린다. Lan의 지연은 무시할 수 있지만, traffic intensity가 1에 가까워지면 회선의 지연이 매우 커지게 된다.

그렇기 때문에 해결방안은 두 가지이다. access link의 접속률을 100Mbps 수준으로 늘리면 traffic intensity를 해결할 수 있지만 불가능하고 비용이 많이 들어가기에 web cache를 사용한다.

cache의 hit rate는 일반적으로는 0.2 ~ 0.7인데, 여기서는 0.4라고 가정한다. cache와 client는 고속 LAN 으로 연결되어있다. 요청의 40퍼센트는 cache에 의해 즉시 만족된다. 하지만 나머지 60퍼센트의 요청은 여전히 original server와 연결되어서 traffic intensity가 0.6으로 감소한다. traffic intensity가 0.8이하이면 작은 지연에 속한다. 그래서 0.4 * 0.01(LAN) + 0.6 * 2.01(access link) 가 평균 지연이 된다.
### conditional GET
웹 캐싱은 응답 시간을 줄이지만 웹 캐시 내부에 있는 복사본이 최신 것이 아닐 수도 있다는 문제를 야기한다.
HTTP는 **브라우저로 전달되는 모든 객체가 최신의 것임을 확인**하면서 캐싱해주는데 이러한 방식을 conditional GET이라고 한다.
GET 과 If-modified-since header를 포함한다면 그게 이거다.
#### 동작 과정
1. 브라우저의 요청을 대신해서 proxy cache는 요청 메시지를 웹 서버로 보낸다.
2. 웹 서버는 cache에게 객체를 가진 응답 메시지를 보낸다. -> 여기서 cache는 브라우저에게 객체를 보내주고, 자신에게도 객체를 저장한다. 또한 cache가 객체와 더불어 **마지막으로 수정된 날짜를 함께 저장**한다는 것이다.
3. 일주일 후에 다른 브라우저가 같은 객체를 캐시에게 요청하면 캐시에 저장되어 있다.이 객체는 지난주에 웹 서버에서 수정되었으므로 브라우저는 conditional GET을 사용한다. if-modified-since 값과 Last-Modified 값과 비교해야한다. if-modified-since는 명시된 값 이후 수정된 경우에만 객체를 보내야한다.
4. 변경되지 않았다면, 304 Not Modified를 보낸다. 이 응답 메시지는 client에게 요청 객체의 caching된 복사본을 사용하라는 것을 의미한다. empty entity body로 보낸다.
## HTTP/2
### 기존의 HTTP/1.1
웹 페이지당 오직 하나의 TCP 연결을 가진다. 소켓 수를 줄이며 공정한 대역폭을 가진다. 하지만 TCP 상에서 모든 웹페이지를 보내면 HOL(Head of Line) 블로킹 문제 가 발생한다.
### HOL 블로킹 문제
HTML 페이지 안에 가장 위에 비디오 클립이 있고, 비디오 아래 수많은 작은 객체들을 포함한다고 하자. 비디오 클립이 bottleneck link를 통과해야하는데, 이게 오래걸려서 아래 객체들이 뒤에서 기다려야 한다면 효율적이지 않다.
이래서 HTTP/1.1 에서는 여러개의 병렬 TCP 연결을 열어서 문제를 해결해왔다.
### TCP 혼잡 제어
TCP 연결이 공정하게 bottleneck link를 공유하여 공평하게 대역폭을 나누게 해준다. 만일 n개의 TCP 연결이 bottleneck link에서 작동하고 있다면 하나에 1/n 대역폭을 사용하게 된다. 하나의 웹 페이지를 전송하기 위해 여러개의 병렬 TCP 연결을 열게 함으로써 브라우저는 링크 대역폭의 많은 부분을 받게 된다. HTTP/1.1 은 6개까지 병렬 TCP 연결을 열고 HOL을 막고, 많은 대역폭을 사용할 수 있게 된다.

## HTTP/2 framing
HTTP/2의 주요 목표 중 하나는 하나의 웹 페이지를 전송하기 위한 병렬 TCP 연결의 수를 줄이거나 제거하는데에 있다. 서버를 열고 유지할 때 소켓이 사용되는데, 소켓의 수를 줄이고, 동시에 TCP 혼잡 제어를 제어해야한다. 하나의 TCP 연결만 사용해야하는데, 이러면 HOL 블로킹을 피해야한다.

그래서 HTTP/2 framing이란 HTTP 메시지를 독립된 프레임으로 쪼개고, interleaving하고, 반대편 사이트에서 재조립한다. 위의 예시처럼 비디오 클립이 들어온다면, 비디오 클립을 1000개의 frame으로 나누고, 각 객체를 2개의 frame으로 나누어 비디오 클립으로부터 하나의 프레임을 전송한다. 이후 frame interleaving을 이용하여 각 소형 객체의 첫 번째 프레임을 보내고 이를 반복하여 블로킹을 피한다. 
**HTTP 메시지를 독립된 프레임들로 쪼개고 interleaving하고 반대편 사이트에서 재조립한다.**

HTTP/2 protocol의 frame 으로 구성된 framing sublayer에 의해 이루어진다. 서버가 HTTP response를 보내고자 할 때, 응답은 framing sublayer에 의해 처리되며, frame들로 나뉘어진다. 

### response message prioritization
말 그대로 요청의 우선순위들을 조정할 수 있게 한다. 애플리케이션의 성능을 최적화 하기 위해 사용한다. 클라이언트가 하나의 서버로 여러개의 요청을 할 때 요청에 우선순위를 매긴다. 서버는 가장 높은 순위의 요청을 위한 프레임을 제일 먼저 보낼 수 있다. 그리고 의존도에 따라 id를 지정하여 의존성을 나타낼 수 있다.

### server pushing
HTTP/2에서는 서버가 특정 클라이언트 요청에 대해 여러개의 응답을 보낼 수 있다. 처음 요청에 대한 응답 외에도 서버는 클라이언트의 요청 없이도 더 보낼 수 있다. HTML 기반 웹 페이지가 웹 페이지를 완벽하게 구동시킬 필요가 있는 객체들을 가리킬 수 있기에 가능하다. 이러한 객체에 대한 HTTP 요청을 기다리는 대신 서버가 **직접** HTML을 분석할 수 있고, 객체들을 식별할 수 있으며, **객체들에 대한 요청이 도착하기 전에** 객체들을 클라이언트로 보낸다. 서버는 클라이언트가 요청을 보내고 기다리는데 소요되는 지연을 없앨 수 있다.

## HTTP/3

# 2-3 Electronic Mail in the Internet
## Three major components of Electronic mail:
- User agents
- Mail servers
- SMTP(Simple Mail Transfer Protocol)

### User Agent
-> 메일 플랫폼이라고 보면 됨. 사용자가 메시지를 읽기,쓰기,전달,저장,구성 하게 해줌.
Outlook, apple mail etc

### Mail server
e-mail infrastructure 의 core이다. 각 수신자는 mail server에 mail box를 가지고 있다. 메일 박스는 메시지를 유지하고 관리한다. 메시지는 **송신자의 user agent에서 전달이 시작되고, 송신자의 mail server를 거친 후에 수신자의 mail server로 전달되며 수신자의 mail box에 저장된다.**
수신자가 mail box에 접근하여 메시지를 열어보려면 mail server는 로그인을 해야한다.

송신자는 메일 서버가 고장나서 메일이 전달이 안된다면 그 메시지를 메시지 큐(message queue)에 보관하고 나중에 그 메시지를 전달하기 위해 다시 시도한다. 재시도는 30분마다 일어나고 계속 실패시에 그 메시지를 제거하고 송신자에게 통보한다.

### SMTP
메일을 송신자의 메일 서버로부터 수신자의 메일 서버로 전송하는 데에 *TCP의 reliable data transfer service* 이용. application layer protocol 이고, client와 server를 가지고 있다. SMTP의 client와 server 모두 모든 메일 서버에서 수행되고, 상대 메일로 송신할 때는 클라이언트, 수신할 때는 서버가 된다.

## SMTP
모든 메일 메시지의 body는 7-bit ASCII를 사용. 전송 용량이 제한된다.
- handshaking
-  transfer of messages(data exchange)
-  closure
A가 user agent를 실행, B의 주소를 제공하여 메시지를 보내라고 명령한다. A의 user agent는 message를 그녀의 mail server에 보내고, 거기서 message가 message queue에 놓인다. A의 mail server에서 동작하는 SMTP의 client는 message queue의 message를 본다. B의 mail server에서 수행되는 SMTP server에게 TCP 연결을 설정한다. SMTP handshaking 이후에 SMTP client는 A의 message를 TCP 연결로 보낸다. B에서 mail server host에서 SMTP의 서버가 message를 수신한다. B의 mail server는 그 메시지를 B의 mail box에 놓는다. B는 그 message를 읽기 위해 user agent를 시동한다. 

**SMTP는 중간 메일 서버를 이용하지 않는다.**
-> message를 보낼 때 실패하더라도 중간 메일 서버에 저장되는 것이 아닌 송신자의 메일 서버에 남아있다.

### Detail
1. client SMTP는 server SMTP의 25번 port로 TCP 연결을 설정한다. 서버가 죽어있으면 나중에 시도한다.
2. 연결이 설정되면 application layer handshaking을 수행한다. 이때 SMTP client가 송신자와 수신자의 e-mail 주소를 제공한다.
3. 이후 client는 message를 보낸다.(TCP)
4. 보낼 다른 메시지가 있다면 반복하며, 아니라면 TCP를 닫는다(persistent connection)

S:  220 hamburger.edu // server's host name(user.agent)
C:  HELO crepes.fr // client's host name(user)
S:  250 Hello crepes.fr, pleased to meet you
C:  MAIL FROM: <alice@crepes.fr> // address
S:  250 alice@crepes.fr ... Sender ok 
C:  RCPT TO: <bob@hamburger.edu> //address
S:  250 bob@hamburger.edu ... Recipient ok //handshaking

C:  DATA
S:  354 Enter mail, end with ”.” on a line by itself
C:  Do you like ketchup?
C:  How about pickles?
C:  .//end of the message
S:  250 Message accepted for delivery
C:  QUIT //data exchange
S:  221 hamburger.edu closing connection //connection close

HELO -> HELLO랑 똑같음
MAIL FROM, RCPT TO, DATA, QUIT
. 하나의 점으로 된 라인은 메시지의 끝을 나타낸다.

### Mail message format
header가 body 앞에 온다. (RFC 5322)
헤더와 몸체는 CRLF로 분리된다.(blank line)
from: header line 과 to: header line은 필수이다.

header lines
- To: (필수!)
- From: (필수!)
- Subject: 
Body
- the "message" ASCII characters only
### Mail access protocols
SMTP (delivery, storage)

일반 사용자는 local host에서 user agent를 수행하고 늘 켜져 있는 공유 메일 서버에 저장된 mail box에 접근한다. mail server는 보통 사용자들과 공유한다. 

송신자 user agent에서 수신자의 mail server까지 도달해야한다. 클라이언트의 user agent가 수신자의 mail server와 직접 대화하는 것은 아니다. client의 user agent는 client의 mail server로 e-mail을 SMTP 혹은 HTTP를 이용하여 보낸다. 그리고 수신자의 mail server는 SMTP를 이용하여 수신자의 mail server로 e-mail을 중계한다.

수신자의 mail server에서 수신자의 user agent에 도달할 때는 다르다. SMTP는 PUSH protocol이고 메시지를 얻는 것은 pull 동작이기 때문에 다른 프로토콜을 사용한다. HTTP나 IMAP를 쓴다. 

# 2-4 DNS: Internet directory service(Domain Name System)

## 구성요소
- hostname
-> www.naver.com 이런거임. 알파벳 문자로 구성되므로 처리를 못하고, 인터넷에서의 위치를 제공하지 못ㅎ나다. 그래서 IP 주소로 식별된다.
- IP address
-> 121.7.106.83 0~255의 십진수로 표현하는 각 바이트는 점으로 구분한다. 계층 구조여서 왼쪽에서 오른쪽으로 조사함으로서 어디에 있는지 알 수 있다. 

hostname은 가변길이 ip address는 고정길이
### DNS가 제공하는 서비스
-> 사람은 hostname 을 선호하지만 router는 ip address를 허용한다. 
DNS는 hostname -> ip address 변환 하는 것이 주요 임무이다. hostname translations address resolutions
## DNS
1. DNS 서버들의 계층 구조로 구현된 분산 데이터 베이스이다. implemented in hierachy of many name servers
2. application layer protocol 이다.
3. UDP 상에서 수행되고 port 번호 53을 이용한다.
### DNS가 UDP를 사용하는 이유
1. 빠른 속도. TCP와 다르게 UDP는 연결 설정에 드는 비용이 없다. -> 신뢰성보다 속도가 더 중요한 서비스이므로 TCP보다 UDP가 더 적합하다. UDP는 512바이트를 넘어가지 않는 packet만 전송이 가능하고 overhead가 없기 때문에 속도가 빠른데, DNS가 전송하는 packet 사이즈는 매우 작으므로 UDP가 유리하다. 전달하는 packet의 크기가 작기 때문에 신뢰성이 보장되지 않아도 된다.
2. 연결 상태를 유지할 필요가 없다. 하지만 TCP는 호스트간의 연결 상태를 유지하고 TCP의 packet 안에는 여러 정보가 담겨있지만, UDP는 어떤 정보도 기록하지 않고 유지할 필요도 없다. 그러므로 연결 상태를 유지하지 않고 정보 기록을 최소화할 수 있는 UDP를 채택했다.

### browser가 URL 을 검색했을 때 발생하는 일
1. 사용자 컴퓨터가 DNS application 의 client를 수행한다.
2. 브라우저는 URL로부터 hostname을 추출하고, hostname을 DNS application의 client에 보낸다.
3. DNS client는 DNS server로 host name을 포함하는 질의를 보낸다.(client queries to DNS server)
4. DNS client는 결국 hostname에 대한 IP 주소를 받게 된다.
5. 브라우저가 DNS로부터 IP 주소를 받으면, 브라우저는 해당 ip 주소와 그 주소의 80번 port에 위치하는 HTTP server process로 TCP 연결을 초기화한다.

-> DNS client 와 DNS server가 있고, 사용자는 DNS application의 DNS client와 소통한다. DNS client는 DNS server에 hostname의 변환을 요청한다.

### 그 외 서비스
#### host aliasing
복잡한 호스트 이름을 가진 호스트는 하나 이상의 별칭을 가질 수 있다. DNS는 IP 주소 뿐만 아니라 제시한 별칭 호스트 이름에 대한 정식 호스트 이름을 얻기 위해 이용될 수 있다. (canonical hostname)

#### mail server aliasing
전자 메일 주소는 간단하지만 그 서버의 hostname은 더 복잡하다.

#### load distribution(DNS load balancing)
load balancing among the servers
인기 있는 사이트는 여러 서버에 중복되어 있다. 각 서버가 다른 end system에서 수행되고 다른 IP 주소를 갖는다. 이때 여러 IP 주소가 하나의 정식 hostname과 연관되어 있다. DNS 데이터베이스는 이 IP 주소 집합을 가지고 있다. 클라이언트가 주소 집합으로 매핑하는 hostname에 대한 DNS 질의를 하면, 서버는 IP 주소 집합 전체를 가지고 응답한다. 여기서 주소는 순환식으로 보낸다. 클라이언트는 대체로 주소 집합 내부의 첫 번째 IP 주소로 HTTP 요청 메시지를 보내므로, DNS 순환방식은 트래픽을 분산하는 효과를 낸다.

## DNS 동작 원리 개요
host에서 실행되는 application 이 hostname을 ip address로 변환하려한다. 
1. application이 hostname을 명시하여 DNS client를 호출한다.
2. host의 DNS client는 DNS server(네트워크)에 질의 query를 보낸다. 이때 모든 질의와 응답 메시지는 port 53의 UDP datagram으로 보내진다.
3. 응답 메시지를 application 에 전달한다.

DNS는 분산된 서버 뿐만 아니라 서버와 클라이언트 사이에서 어떻게 통신하는지를 명시하는 application layer protocol로 구성되어 있다.

### DNS가 중앙 집중 데이터베이스라면?
DNS가 간단한 설계로 모든 매핑을 포함하는 하나의 server에서 구동된다면, 서버 한 개가 고장나면 전체 인터넷이 작동하지 않는다. (single point of failure)
traffic 과부하가 걸린다. 중앙 집중 데이터베이스가 멀수록 질의가 느려진다. 유지 관리가 어렵고 확장성이 전혀 없다.

### distributed hierarchical database
DNS는 아주 많은 서버를 사용하고, 이를 계층 형태로 구성하여 전세계에 분산시킨다.

### 계층 DNS 서버의 종류(다시보기)
- root DNS server 
-> 1000개 이상의 root server instance가 세계에 흩어져있다. root name server는 TLD server의 IP 주소들을 제공한다. ICANN에 의해 조정된다.
- TLD DNS server
-> 상위레벨 도메인과 국가 상위 레벨 도메인에 대한 TLD server가 있다. authoritative DNS 서버에 대한 IP 주소를 제공한다.
- authoritative DNS server
-> 기관의 책임 DNS server
- local DNS server

root > TLD > Authoritative 순으로 우위가 높음
host는 local DNS server에 request를 보내고, local 에서 root에 request를 보내고, response를 받는다. 거기서 받은 정보를 토대로 TLD와 같은 과정을 진행하고, Authoritative에도 같게 진행하고 최종 ip 주소를 알아내서 local에서 받게된다.

++) TLD server는 예시와 같이 authoritative DNS server를 알지 않고, authoritative DNS server를 아는 중간 DNS server를 알고 있다. 그래서 중간에 과정이 하나 더 있기 때문에 오가는 과정이 10번인것이다. 

반복적 / 재귀적 질의(?)


### DNS caching
DNS 캐싱 -> DNS 지연 성능 향상, 네트워크의 DNS 메시지 수 줄이기
DNS server는 DNS response를 받았을 때, local memory에 응답에 대한 정보를 저장할 수 있다.

hostname, ip address 쌍이 DNS server에 저장되고, 다른 hostname으로부터 같은 질의가 DNS server로 도착하면, DNS server는 host 이름에 대한 책임이 없을 때조차 원하는 주소를 제공할 수 있다.

Host DNS와 ip 사이의 mapping과 host는 영구적이지 않기 때문에, 어떤 기간(TTL, time to live) 이후에 저장된 정보를 제거한다. 

## DNS record and message
### DNS Resource Records
(Name, Value, Type, TTL) 이라는 resource record를 저장한다. name 과 value는 type을 따른다. type에 따라서 name과 value에 대한 semantic이 달라진다.

- Type = A(address)
	Name / Value => hostname / ip address
- Type = NS(name server)
	Name / Value => domain / authoritative DNS server hostname
- Type = CNAME(canonical name)
	Name / Value => 정식 hostname의 alias name / 별칭 hostname 에 대한 정식 hostname
- Type = MX(mail exchange)
	Value => 별칭 hostname을 갖는 mail server의 정식 이름 
mail server의 정식 name을 얻기 위해서 mx record에 대한 질의를 해야하고, 다른 서버의 정식 이름을 얻기 위해선 CNAME record에 대한 질의를 한다.

### DNS message


# 2-5 Peer-to-Peer File Distribution
p2p 구조는 항상 켜져있는 infrastructure server에 최소한으로 의존하고 간헐적으로 연결되는 host 들(peer) 이 서로 직접 통신한다. 

server와 peer들은 access link로 인터넷에 연결되어있다. 서버의 access link upload 속도를 u(s)로, i번째 피어의 access link upload 속도를 u(i)로 한다. i번째 peer의 access link download 속도를 d(i)로 한다. 분배되는 파일의 크기는 F bit, 얻고자 하는 peer의 수는 N으로 나타낸다.

### client-server file distribution
server는 파일을 N개의 peer에게 전송해야한다. 따라서 server는 NF bit를 전송해야한다. server가 파일을 분배하는 시간은 적어도 NF/u(s)이다. d(min)이 가장 낮은 다운로드 속도를 가진 피어의 다운로드 속도라고 하자. 최소 분배 시간은 F/d(min)이다. D(cs) >= max{NF/u(s), F/d(min)}. 충분히 큰 N에 대해 client-server distribution time은 NF/u이다. N에 비례.

### p2p file distribution
시작할 때 server에서 peer로 한번은 access link를 통해 파일의 bit를 보내야한다. 최소 분배 시간은 F/u(s)이다. 한 번 보내고 다시 보낼 필요가 없다. peer에서 재분배가 가능하기 때문이다. 가장 다운로드 속도가 낮은 피어는 F/d(min) 보다 적은 시간에 F를 받을 수 없다. 여기서 최소 분배시간은 F/d이다. 시스템의 전체 업로드 용량은 서버의 전체 업로드 속도와 각 피어들의 속도를 더한 것이다. 이것이 u(total). 최소 분배 시간은 NF/u(total)이다. D(p2p) >= max{F/u(s), F/d(min), NF/u(total)}

### c-s vs p2p
client-server는 선형이고, p2p는 log scale이다. p2p는 자가 확장성을 갖는다. 

### BitTorrent
특정 파일의 분배에 참여하는 모든 피어의 모임을 토렌트라고 부른다. 피어들은 서로에게서 같은 크기의 chunk를 다운로드한다. 시간이 지날수록 chunk가 쌓여간다. (accumulate chunks over time from other peers) 피어가 청크를 다운로드할 때 청크를 다른 피어들에게 업로드한다. 

#### traker
각 토렌트는 traker라고 불리는 infrastructure node를 갖고 있다. traker는 torrent에 있는 peer들을 추적할 수 있다. A가 토렌트에 가입하면, **tracker는 peer 집합에서 임의로 50개를 선택하여 이 50개 peer들의 IP주소를 A에게 보낸다**. A는 이 목록에 있는 모든 peer와 동시에 TCP 연결을 맺고, 성공적으로 맺은 피어를 이웃 피어라고 부른다. 

#### rarest first
requesting chunks, A는 청크의 일부를 가질 것이고, 이웃들이 어떠한 청크를 가지고 있는지 정보를 알게될 것이다. 
1. 어느 청크를 먼저 요구할 것인가?
2. 어느 피어에게 청크를 요청할 것인가?
갖고 있지 않은 청크 중에서, 이웃 가운데 가장 드문 청크를 결정하고 이를 먼저 요구한다. 

#### sending chunks : tit for tat
어떤 요청에 응답할지 결정할 때 A가 가장 빠른 속도로 A에게 데이터를 제공하는 이웃에게 우선순위를 주는 것이다. 계속해서 bit를 수신하는 속도를 측정하고, 가장 빠르게 전송하는 4개의 피어를 결정하고, 걔네에게 청크를 보내서 보답한다. 4개의 peer는 unchoked(활성화되었다)고 한다. 40초마다 위 피어를 제외하고 임이의 피어에게 청크를 보낸다. 이 피어는 optimistically unchocked라고 한다. 이제 A는 임의의 피어에게 활성화될 수 있고,  그 반대도 가능하다. 여러 피어와 교역할 수 있다. 이때 A와 4개의 피어 총 5개의 피어 외 모든 이웃 피어는 어떤 청크도 교역하지 않는다. (choked by A = do not receive chunks from her)

# 2-6 Video Streaming and Content Distribution Networks

## internet video
비디오는 이미지의 연속으로서 일반적으로 초당 24~30개 이미지가 일정한 속도로 표시되는 것이다. 압축되지 않은 디지털 인코딩된 이미지는 픽셀 단위로 구성된다. 비디오는 압축될 수 있으며, 비디오 품질과 비트 전송률은 반비례한다. 비트 전송률이 높을수록 이미지 품질이 좋다. 4K 스트리밍은 10Mbps 이상의 비트 전송률이다. 
네트워크는 압축된 비디오의 전송률 이상의 스트리밍 애플리케이션에 대한 평균 처리량을 제공해야한다.

## HTTP streaming and DASH
HTTP streaming에서 video는 일반적인 URL을 갖는 일반적인 HTTP 파일로 저장된다. 
1. client는 server에게 TCP 연결을 하고, URL에 대한 HTTP GET 요청을 발생시킨다.
2. server는 HTTP response message 내에서 video file을 전송한다.
3. application buffer에 전송된 byte가 저장된다.
4. buffer의 byte 수가 미리 정해진 임계값을 초과하면 재생을 시작한다. 
5. **buffer는 주기적으로 video frame을 가져와 frame을 압축 해제한 다음 사용자의 화면에 표시한다.**
가용 대역폭이 달라도 똑같이 인코딩된 비디오를 전송받는다는 문제가 있다.

### Dash(dynamic adaptive streaming over HTTP)
video는 여러가지 버전으로 인코딩 되며, 비트율과 품질 수준이 서로 다르다.
client는 동적으로 서로 다른 버전의 video를 몇 초 분량의 길이를 갖는 비디오 조각으로 요청한다. 가용 대역폭이 충분할 때는 높은 비트율의 버전을 요청, 적을 때에는 낮은 비트율의 버전을 요청한다. 
client는 자신의 상황에 알맞은 비디오 버전을 요청한다.
각 비디오 버전은 HTTP server에 서로 다른 URL을 가지고 저장된다. HTTP server은 각 버전의 URL을 제공하는 manifest file을 갖고 있다. client는 이 manifest file을 제공 받고, 이에 따라 원하는 버전의 비디오 조각 단위를 선택하여 HTTP GET 요청 메시지에 URL과 byte-range를 지정하여 요청한다.
**DASH는 클라이언트가 서로 다른 품질 수준을 자유롭게 변화시킬 수 있도록 허용한다.**

## CDN(content distribution network)

### 단순한 방법과 문제점
단일 거대한 데이터 센터를 구축하고 거기에 모든 비디오 자료를 저장한 뒤, 전 세계의 사용자에게 비디오 스트림을 직접 전송한다.

- client가 데이터 센터로부터 멀 경우 다양한 communication link 와 ISP를 거쳐야한다. 그렇게 되면 이 링크들 중 하나라도 비디오 소비율보다 낮은 전송 용량을 갖는 경우 병목현상이 발생한다.
- 인기 있는 비디오는 같은 링크를 통해 반복적으로 전송된다. 반복 비용을 지불하게 된다.
- 한 번의 장애로 전체 서비스가 중단될 수 있다. 

### CDN
다수 지점에 분산된 서버를 운영한다. 비디오 및 다른 형태의 웹 콘텐츠 데이터의 복사본을 이러한 분산 서버에 저장한다.
사용자는 최적의 CDN 서버로 연결된다.
CDN은 사설 CDN일 수도 있으며, 제 3자가 운영할 수도 있다.

### CDN 서버 위치의 철학
- Enter Deep
--> server cluster를 세계 곳곳의 access network에 구축함으로서 ISP의 access network로 깊숙히 들어간다. 최대한 server를 user 근처에 위치시킨다.
- Bring Home
--> 핵심 지점에 큰 규모의 server cluster를 구축하여 ISP를 Home으로 가져온다. ISP에 연결하는 대신 그들의 클러스터를 IXP에 배치한다. Enter Deep 보다 처리율은 더 낮고 delay가 걸릴 수 있지만 회사의 입장에서는 유지 보수하기 편하며, 비용이 적게 든다. CDN은 콘텐츠의 복사본을 이들 클러스터에 저장하는데, 모든 복사본을 유지하지는 않는다. 요청이 오면 중앙 서버나 다른 클러스터로부터 전송받아 사용자에게 서비스하는 동시에 복사본을 만들어 저장한다.

### CDN 동작
1. 사용자가 URL을 지정하여 비디오를 요청한다.
2. CDN은 그 요청을 가로채 client에게 가장 적당한 CDN 클러스터를 선택한다.**
3. client의 요청을 해당 cluster의 서버로 연결한다.
요청을 가로챌 때 CDN은 DNS를 이용한다. DNS redirection.
1. 사용자가 URL 입력한다. 
2. 사용자의 host는 URL의 hostname에 대한 질의를 local DNS로 보낸다(여기까지 그대로)
3. local DNS는 hostname의 authoritative DNS server로 질의를 전달한다. authoritative DNS server는 해당 질의를 CDN으로 연결하기 위해 CDN server의 authoritative server의 IP를 전달한다.
4. local DNS는 authoritative DNS server로 질의를 보내고 CDN content server의 IP 주소를 local DNS server로 응답한다. client가 콘텐츠를 전송받게 될 서버가 결정된다.
5. local DNS server는 사용자 host에게 CDN server의 IP 주소를 알려준다.
6. client는 host가 알게된 IP 주소로 HTTP 혹은 DASH 프로토콜을 통해 video 를 받아온다.

### 클러스터 선택 정책
CDN이 DNS를 통해 가로채는 과정에서 CDN은 client의 로컬 DNS server의 IP 주소를 알게된다. IP 주소에 기초해 최선의 클러스터를 선택한다.
-> 지리적으로 가가운 클러스터를 설정한다. (네트워크 경로 길이 수에 따라 가장 가까운 클러스터가 아닐 수도 있다.)
-> 실시간 측정을 통해 현재 네트워크 상황을 반영하여 최선의 클러스터를 선택한다.

### netflix(나중에)
### youtube(나중에)


# 2-7 Socket Programming: Creating Network Applications

네트워크 application 을 생성할 때에는 두 프로그램, client와 server program을 작성한다. 두 프로그램을 실행하면 process가 각각 생성되고, process가 socket으로부터 읽고 쓰기를 통해 통신한다.

client-server application
- HTTP 등 RFC에 정의된 표준 프로토콜을 구현하는 애플리케이션
- 개인의 독점적인 네트워크 애플리케이션으로 RFC 또는 다른 곳에 공식적으로 출판되지 않은 application layer protocol을 채택하여 구현

## UDP socket programming
UDP를 사용할 때에는 송신 프로세스가 데이터의 packet을 소켓 문 밖으로 밀어내기 전에, packet에 목적지 주소를 붙여넣어야 한다.

이 packet이 송신자의 socket을 통과한 후 인터넷은 이 목적지 주소를 이용하여 그 패킷을 인터넷을 통해 수신 프로세스에 있는 소켓으로 route한다.

packet이 수신 소켓에 도착하면 수신 프로세스는 소켓을 통해 패킷을 추출하고 동작을 취한다.

packet에 목적지 주소를 포함한다. host는 ip 주소를 식별자로 갖는다. host는 그러나 많은 네트워크 애플리케이션 프로세스를 수행하고 있을 수 있기 때문에 목적지 host 내의 특정한 socket을 식별할 필요가 있다.
(**목적지 host를 건물이라고 한다면, packet에서 건물은 찾았지만 socket은 문이기 때문에 문이 여러개여서 어디로 들어가야할 지 모르는 상황이다.**)

이때 socket을 식별하기 위해서 있는게 **port 번호**이다. 이것이 프로세스 식별자다. packet에는 ip 주소와 port 번호로 구성된 목적지 주소가 붙게 되고, 송신자의 출발지 주소에도 붙는다. 

### socket programming
1. client는 키보드로부터 한 줄의 문자를 읽고 그 데이터를 서버로 보낸다.
2.  서버는 그 데이터를 수신하고 문자를 대문자로 변환한다.
3. 서버는 수정된 데이터를 클라이언트에게 보낸다.
4. 클라이언트는 수정된 데이터를 수신하고 그 줄을 화면에 나타낸다.

(생략)

## TCP socket programming
연결 지향 프로토콜로 서로 데이터를 보내기 전에 먼저 TCP 연결을 설정할 필요가 있다. 
TCP 연결을 생성할 때 client 소켓 주소와 server 소켓 주소를 연결과 연관시킨다. 연결이 설정된 후 socket을 통해 데이터를 TCP 연결로 보낸다. 

### welcome socket / connection socket
client process에서는 우선 TCP socket을 생성하고(이때 welcome socket의 주소인 IP와 port 번호를 명시한다), server에는 welcome socket과 connection socket 두개가 있다. client와 server는 handshake를 통해 TCP 연결을 설정한다. 우선 handshaking을 하는 동안 connection socket을 만든다. application 관점에서 client socket과 connection socket은 파이프에 의해 직접 연결된다. 

(프로그래밍 생략)

# 3-1 Introduction and Transport-Layer Services
transport layer protocol은 각기 다른 host에서 동작하는 application process간의 logical communication을 제공한다. application의 관점에서 보면, process들이 동작하는 host들이 직접 연결된 것처럼 보인다. transport layer protocol은 router가 아닌 end system에서 구현된다.

**절차**
1. 송신 측의 transport layer는 송신 application process부터 수신한 메시지를 transport layer packet으로 변환한다. 이를 transport layer segment라고 부른다. i) application message를 분할 ii) transport layer header를 추가한다. 
2. transport layer는 송신 end system에 있는 network layer로 segment를 전달한다. i) segment는 datagram안에 encapsulate되어 목적지로 전달된다. network layer는 오직 datagram의 network layer field에 대해 동작한다. 즉, datagram안에 캡슐화된 transport layer segement의 내용은 검사하지않는다.
3. 수신 측에서 network layer는 datagram으로부터 transport layer segment를 추출하고 transport layer로 segment를 보낸다.
4. transport layer는 수신 application 에서 segment 내부의 데이터를 이용할 수 있도록 수신된 segment를 처리한다.

## transport layer - network layer
transport layer protocol은 각기 다른 host에서 동작하는 process들 사이의 논리적 통신을 제공한다. 
network layer protocol은 host 사이의 논리적 통신을 제공한다.

transport layer protocol은 applicaition process와 network layer 사이에서 메시지를 주고받는 역할을 한다. 

- transport layer protocol은 하위 network layer protocol의 서비스 모델에 의해 제약 받는다.
- network layer protocol이 상응하는 서비스를 제공하지 못할 때도, 특정 서비스는 transport protocol 에 의해 제공될 수 있다. (비신뢰적 서비스)
## 인터넷 트랜스포트 계층의 개요
**TCP & UDP**
TCP(Transmission Control Protocol)
신뢰적이고 연결지향형 서비스. reliable data transfer
congestion control 혼잡제어 -> 혼잡한 네트워크 링크에서 각 tcp 연결이 링크의 대역폭을 공평하게 공유하여 통과하도록 해준다.
**UDP(User Datagram Protocol)**
비신뢰적, 비연결형 서비스.
UDP transport protocol을 사용하는 application 은 허용이 되는 한 어떤 속도로든 전송 가능하다.

**segment & datagram**
segment -> transport layer packet 
datagram -> network layer packet
+) TCP에 대한 packet을 segment, UDP에 대한 packet을 datagram이라 하기도 한다.

## IP(Internet Protocol)
IP 서비스 모델은 host간의 논리적 통신을 제공하는 최선형 전달 서비스(best effort delivery service)

IP가 통신하는 host간의 segment를 전달하기 위해 최대한 노력하지만, 어떤 보장도 하지 않는다. segment의 전달 보장 x 순서 보장 x 내부 데이터의 무결성 보장 x 
IP는 비신뢰적인 서비스이다.

# 3-2 multiplexing and demultiplexing

network layer에서는 host-host 전달 서비스 인데, host에서 동작하는 applicaiton 에 대한 process-process 전달 서비스로 확장되는 과정.

1. 목적지 host에서 transport layer는 network layer로부터 segment를 수신한다. transport layer는 network layer
2. transport layer는 segment를 중간 매개자인 socket에 전달한다. 

transport layer segment는 segment에 field 집합을 가지고 있으며, transport layer는 수신 socket을 식별하기 위해 이러한 field를 검사한 후 해당 socket으로 보낸다.

**demultiplexing**
-> transport layer segment의 data를 올바른 소켓으로 전달하는 작업을 말한다. 
-> 호스트의 각 소켓은 포트 번호를 할당 받는다. 세그먼트가 host에 도착하면, transport layer는 segment 안의 목적지 port 번호를 검사하고, 그에 상응하는 소켓으로 세그먼트를 보낸다. 세그먼트의 데이터는 소켓을 통해 해당되는 프로세스로 전달된다.
**multiplexing**
-> 출발지 host에서 socket으로부터 data를 모으고, 이에 대한 segment를 생성하기 위해 각 데이터에 header 정보로 캡슐화한다. 그 세그먼트들을 네트워크 계층으로 전달한다.

**소켓은 유일한 식별자인 포트번호를 갖는다.**
**각 세그먼트는 세그먼트가 전달된 적절한 소켓을 가리키는 특별한 필드를 갖는다.**
source port number field / destination port number field

## 비연결 다중화와 역다중화
UDP socket은 목적지 IP 주소와 목적지 port 번호로 구성된 두 요소로 된 집합에 의해 식별된다.
만약 2개의 UDP 세그먼트가 같은 목적지 IP주소와 목적지 port 번호를 가진다면, 같은 목적지 소켓을 통해 같은 프로세스로 향할 것이다. 그러면 출발지 포트 번호는 무슨 목적?
B가 A에게로 segment를 보내길 원할 때, B에서 A로 가는 segment의 목적지 port 번호는 A에서 B로 가는 세그먼트의 출발지 포트 번호로부터 가져온다. 

-> 연결이 안되어있어서 출발지 포트 번호를 이용하여 목적지를 찾아낸다.

## 연결지향형 다중화와 역다중화
TCP socket은 4개 요소의 집합에 의해 식별된다. 출발지 IP 주소, 출발지 port 번호, 목적지 IP 주소, 목적지 port 번호. 그러므로 출발지가 다르면 다른 소켓으로 향하게 된다.
TCP 연결 설정 (TCP는 welcome 소켓을 가지고 있다.)

1. TCP 서버 애플리케이션의 웰컴 소켓은 포트번호 12000을 가진 TCP 클라이언트로부터 연결 설정 요청을 기다린다.
2. TCP 클라이언트는 소켓을 생성하고 연결 설정 요청 세그먼트를 보낸다. 목적지 포트번호 / TCP 헤더에 연결 설정 비트 / 출발지 포트 번호 를 포함한다.
3.  서버 프로세스로 동작하는 host 운영체제가 목적지 12000을 포함하는 연결 요청 세그먼트를 수신하면, 이 세그먼트를 포트번호 12000으로 연결 수락을 기다리는 서버 process로 보낸다.
4. 서버는 연결 요청 세그먼트의 4개요소의 집합을 주목한다. 이게 전부 일치하면 역다중화 성공이다.

## 웹 서버와 TCP
서버는 각기 다른 클라이언트가 보낸 세그먼트를 출발지 IP 주소와 출발지 port 번호로 구별한다. 같은 웹 서버 애플리케이션과 통신하기 위해 같은 목적지 포트 번호를 이용하는 두 클라이언트를 생각한다.하지만 얘네는 다른 출발지 ip주소를 가지기 때문에 올바르게 역다중화 한다.

process -> 연결 소켓 (http request, response) -> thread

persistent HTTP / non-persistent

# 3.3 Connectionless Transport : UDP
다중화/역다중화 기능
간단한 오류 검사 기능

동작순서
1. application process로부터 message를 가져와서 multiplexing/demultiplexing service에  필요한 출발지 port 번호 field, 목적지 port 번호 field를 첨부한다.
2. 출발지 host의 IP 주소 field, 목적지 hosts의 IP 주소 field를 추가한 후에 최종 transport layer segment를 network layer로 넘겨준다.
3. network layer는 transport layer segment를 IP datagram으로 캡슐화 하고, segment를 수신 host에게 전달한다.
4. segment가 수신 host에 도착한다면 UDP는 세그먼트의 데이터를 해당하는 애플리케이션 프로세스로 전달하기 위해 목적지 port 번호를 사용한다.
**UDP는 segment를 송신하기 전에 handshaking을 하지 않는다.**

**DNS**는 UDP를 사용한다.

## UDP의 장점
**무슨 데이터를 언제 보낼지에 대해 애플리케이션 레벨에서 더 정교한 제어가 가능하다.**
-> UDP에서 application process가 데이터를 UDP에 전달하자마자 UDP는 데이터를 UDP segment로 만들고, 그 segment를 즉시 network layer로 전달한다.
**실시간 애플리케이션에서는 UDP를 사용하고, 필요한 어떤 추가 기능을 구현할 수 있다.**
UDP는 연결 설정이 없어서 어떤 지연도 없다. 
연결 상태가 없다. 지속적으로 연결을 유지하지 않고, 액티브 클라이언트를 많이 수용할 수 있다.
packet overhead가 아주 작다. TCP는 segment마다 20byte의 오버헤드를 갖지만, UDP는 8바이트이다. 

+) tcp
혼잡 제어 메커니즘과 존재하고, 오래걸릴 수 있다.

## UDP의 단점
UDP는 혼잡 제어를 하지 않는다. 혼잡 제어는 네트워크가 꼭 필요한 작업을 할 수 없게 되는 폭주 상태에 빠지는 것을 막기 위해 필요하다. 
혼잡 제어가 없다면, 라우터에 많은 packet overflow가 발생한다. 그리고 TCP 세션의 혼잡이 발생한다.

## UDP를 통한 신뢰적 데이터 전송
UDP는 비신뢰적인 서비스이지만, application 자체에서 신뢰성을 제공한다면 신뢰적 데이터 전송이 가능해진다. 크롬에서는 QUIC 프로토콜을 사용한다.
### UDP 세그먼트 구조
- source port number / destination port number
- length
- checksum
--> 수신 호스트가 사용한다. 세그먼트 오류 검사?
- application data(Datagram의 데이터 필드 위에 존재)

### UDP checksum
checksum 은 segment가 출발지로부터 목적지로 이동했을 때, UDP segment안의 비트에 대한 변경사항이 있는지 검사한다. 
(과정 생략)
비트 중에 0이 하나라도 있다면 패킷에 오류가 있다는 뜻이다.

UDP checksum을 제공하는 이유는 출발지와 목적지 사이의 모든 링크가 오류 검사를 제공한다는 보장이 없기 때문이다. 세그먼트가 정확하게 전송되었을지라도 비트 오류는 발생할 수 있다. 
**UDP는 오류 검사를 제공하지만, 오류를 회복하기 위한 어떤 일도 하지 않는다.**
주어진 링크 간의 신뢰성과 메모리의 오류 검사가 보장되지도 않고, end간의 데이터 전송 서비스가 오류 검사를 제공해야 한다면, UDP는 종단 기반으로 transport layer에서 오류 검사를 제공해야한다. 

end-end principle

# 3.4 Principles of Reliable Data Transfer
## 유한상태 머신(finite-state machine, FSM)
화살표는 state의 전이를 뜻한다. FSM의 초기 상태는 점선 화살표로 표시된다.
전이를 일으키는 event는 가로선 위에 나타낸다.
이벤트가 발생했을 때 취해지는 action은 가로선 아래에 나타낸다.

아무것도 없으면 기호 𝚲를 사용한다.

## rdt 1.0 (신뢰적)
하위 채널이 완전히 신뢰적인 경우 

sender와 receiver는 분리되어있다. rdt 1.0에서 FSM은 하나의 상태만을 가진다. 

sender
1. rdt_send(data) event -> 상위 layer application 에서 procedure 호출에 의해 발생한다. 상위 계층으로부터 data를 받고, data를 포함한 패킷을 생성한다.
2. packet = make pkt(data)
3. Udt_send(packet) 패킷을 채널로 송신한다.

receiver 
1. rdt_rcv(packet) event -> 하위의 채널로부터 packet을 수신한다. lower layer protocol의 procedure 호출에 의해 발생한다. 
2. packet에서 data를 호출한다. (extract(packet,data))
3. upper layer로 data를 전달한다. deliver_data(data)

## rdt 2.0 (채널에 오류)
packet의 bit들이 lower layer에서 손상되는 모델이다. 패킷이 전송 또는 전파되거나 버퍼링 될 때 네트워크의 물리적 오류 때문이다. 
checksum을 활용하여 bit error를 감지한다.

### Automatic Repeat reQuest ARQ 자동 재전송 요구
- 긍정 확인 응답
- 부정 확인 응답
- 오류 검출
--> 수신자가 비트 오류를 검출하고 복구할 수 있게 
- 수신자 피드백
--> 수신자가 송신자에게 피드백 제공, 패킷을 잘 수신했는지 아닌지. 긍정(ACK) 혹은 부정(NAK) 확인 응답을 보낸다.
- 재전송
--> 오류를 가지고 수신된 패킷은 송신자에 의해 재전송 된다.

### rdt 2.0에 대한 FSM

sender (2개의 상태가 존재한다.)
1. 왼쪽 상태에서 upper layer로 부터 데이터가 전달되기를 기다린다. rdt_send(data)가 발생하면, sndpkt를 생성한다. 이건 rdt 1.0과 다르게, 패킷 checksum을 포함한다. 이 패킷을 udt_send(sndpkt) 동작을 통해 전송한다.(수신자에게)
2. 오른쪽 상태에서는 송신자 protocol은 수신자로부터 ACK or NAK packet을 기다린다. i) ACK packet이 수신된다면, 정확히 수신되었음을 의미한다. protocol은 왼쪽 상태로 돌아간다. (isACK(rcvpkt)) ii) NAK packet이 수신된다면, protocol은 마지막 packet을 재전송한다. 응답이 ACK가 되기까지 무한으로 기다리고 상태는 계속 오른쪽 상태이다.
STOP AND WAIT protocol이다. 그리고 오른쪽 상태일 때, upper layer로부터 data를 더이상 전달받을 수 없다. rdt_send() event는 발생할 수 없다. 정확하게 수신자가 packet을 수신했음을 확인하기 전까지 데이터를 받지 않는다.

reciever (1개의 상태가 존재한다.)
수신자는 수신하는 동시에, 수신된 패킷이 손상되었는지에 따라 ACK 또는 NAK로 응답한다. 
NAK일 때는 NAK packet을 만들어 송신자에게 보낸다. 
ACK일 때는 ACK packet을 만들어 송신자에 보내는 동시에 rdt_send(data)에서 data를 추출하고 데이터를 보낸다.

### rdt 2.0의 결함
rdt는 ACK 혹은 NAK 패킷이 손상될 수 있는 가능성을 고려하지 않았다.
- 대안 1) 송신자가 검출 뿐만 아니라 비트 오류로부터 회복할 수 있도록 충분한 checksum bit들을 추가한다.
- 대안 2) 송신자가 왜곡된 ACK or NAK 패킷을 수신할 때 현재 데이터 패킷을 다시 송신한다. 
수신자 입장에서는 도착하는 패킷이 새로운 놈인지 재전송인지 뭔지 알 수가 없다. 
- 해결책) 데이터 패킷에 새로운 필드를 추가하고, 이 필드 안에 순서 번호를 삽입한다. 

## rdt 2.1
상태가 4개~?
1. 프로토콜 상태가 현재 송신자에 의해 전송되고 있는지에 대한 반영
2. 수신자가 기다리고 있는 패킷이 순서번호 0 또는 1을 가져야하는지에 대한 반영
프로토콜 rdt 2.1은 수신자로부터 송신자까지의 긍정 확인 응답과 부정 확인 응답을 모두 포함한다.
- 순서가 바뀐 패킷이 수신되면, 이미 전에 수신한 패킷에 대한 긍정 확인 응답을 전송한다. 순서는 네트워크 지연이나 경로 문제로 순서대로 도착하지 않을 수 있다. 
- 손상된 패킷이 수신되면, 수신자는 부정 확인 응답을 전송한다. 

중복 수신 -> NAK 를 송신하는 것 대신에 가장 최근에 정확하게 수신된 패킷에 대해 ACK를 송신한다. 같은 패킷에 대한 2개의 ACK를 수신했으므로, 두 번 ACK한 패킷의 다음 패킷을 정확하게 수신 못했다는 것을 알게 된다.

## rdt 2.2 (NAK 없는 rdt 2.1)
rdt 2.2는 rdt 2.1과 다르게, 수신자가 반드시 ACK 메시지에 의해 확인 응답되는 패킷의 순서 번호를 포함해야한다. isACK를 사용한다.

## rdt 3.0 하위 채널이 패킷을 손실하는 경우 포함
- 어떻게 packet loss 검출?
- 그때 어떤 행동을?
- 송신자에게 packet의 검출과 회복 책임을 부여한다.
-> 송신자가 packet의 손실을 확인하기 위해 시간은 오래걸린다. 왕복 시간 지연 + 수신  측 패킷 처리 시간
-> 패킷 손실이 일어났을 만한 시간을 선택하여, ACK가 이 시간 안에 수신되지 않는다면 패킷은 재전송 된다. 이는 중복 데이터 패킷의 가능성을 포함하나, 패킷의 순서번호를 통하여 처리 가능하다.
-> 시간 기반 재전송을 구현하기 위해선, countdown time가 필요하다. 

### 동작과 처리 과정
패킷의 순서번호는 0과 1이 번갈아간다. 그러므로 rdt 3.0은 alternating-bit protocol 이라고 불린다.
Sender <-> Receiver 
**무조건 data packet을 다시 보낸다**
**꼬여서 ACK1이 두번 올 경우에 아무것도 안한다**

### 파이프라이닝된 신뢰적 데이터 전송 프로토콜
rdt3.0은 전송 후 대기 이기 때문에 빠르지는 않다. 형편없는 송신자 효율을 갖는다.
확인 응답을 기다리기 전에 송신을 전송하도록 허용한다. (pipelining)
이렇게 되면 빨라진다. 당연히(컴아에서 배움)

**이러면 순서번호의 범위가 커져야 한다.**
**프로토콜의 송신과 수신측은 패킷 하나 이상을 버퍼링해야한다. 최소한 하나의 '송신자는 전송되었으나 확인 응답 되지 않은 패킷'을 버퍼링 해야한다. 수신자에게서도 필요하다**

필요한 순서 번호의 범위와 버퍼링 조건은 방식에 달려있다. 

### GBN(Go-Back-N)
송신자는 확인 응답을 기다리지 않고 여러 패킷을 전송할 수 있다. 최대 허용 수 N보다 크지 말아야 한다.
확인응답이 안 된 가장 오래된 패킷의 순서 번호를 base로 정의한다. 가장 작은 순서 번호를 nextseqnum으로 정의한다. [0, base-1] 순서번호 전송, 확인응답 o / [base, nextseqnum-1]송신 o, 확인 응답 x / [nextseqnum, base+N-1] pipelining 이용해서 전송 가능한 패킷 / base+N 이상, pipeline에서 확인응답 안 된 패킷. base의 확인응답이 돡해야 사용 가능(not usable)

다른 이름으로 sliding-window protocol
전송이 되었지만, 아직 확인응답이 안된 패킷을 위해, 허용할 수 있는 순서 번호의 범위는 순서 번호의 범위 상에서 크기가 N인 window로 나타낸다.
N은 window size

패킷의 순서번호는 헤더의 고정 길이 필드에 포함된다.
k가 패킷 순서 번호 필드의 비트 수라면 순서 번호의 범위는 [0, 2^k-1]이다.

송신자
1. rdt_send 호출
2. ACK 수신
3. timeout event
수신자
-> GBM에서 수신자는 순서가 잘못된 패킷들을 버린다. 패킷 n+1이 먼저 도착하면, 데이터가 순서대로 전달되어야하므로, 수신자는 n+1를 buffer에 저장하고 나중에 패킷 n이 수신되고 전달된 후에 상위 계층에 이 패킷을 전달한다. 만일 패킷 n이 손실된다면, GBN 재전송 규칙에 따라 수신자에게는 패킷 n과 n+1이 재전송 된다. 이 방식대로 하면 수신자 buffering이 간단한다.

### GBN 문제
-> 패킷 하나의 오류 때문에 많은 패킷을 재전송하므로 불필요한 재전송이 많아진다. 

### SR(Selective Repeat)
-> 수신자에서 오류가 발생한 패킷을 수신했다고 "의심" 되는 패킷만을 재전송한다.
- 불필요한 재전송을 피한다
- 각각의 재전송은 수신자가 개별적인 확인 응답을 요구한다. 
-> 패킷 순서와 무관하게 확인 응답을 한다. i)순서가 바뀐 패킷은 빠진 패킷이 수신될 때까지 버퍼에 저장하고, ii) 빠진 패킷이 수신된 시점에서 일련의 패킷을 순서대로 전달한다.

- 상위로부터 데이터 수신
--> data 수신될 때, 순서 번호가 송신자 window 내에 ㅇㅆ으면 data는 packet으로 송신된다. 
- 타임아웃
- ACK 수신
//넘겨 나중에 다시

# 3.5 Connection-Oriented Transport: TCP

## TCP 연결
TCP는 handshaking 때문에 connection-oriented 이다. (연결지향형) data transfer를 보장하는 parameter들을 각자 설정하기 위한 segment들을 사전에 보내야한다.
TCP connection은 두 end system의 TCP에 존재하는 상태를 공유하는 논리적인 것이다. 

TCP 서비스는 full-duplex service를 제공한다.
만약 host A와 host B의 process 사이에 TCP connection이 있다면, application layer data는 B->A로 흐르는 동시에 A->B로 흐를 수 있다.

TCP 연결은 항상 단일 송신자와 단일 수신자 사이의 point-to-point  이다.

**단일 동작으로** 한 송신자가 여러 수신자에게 데이터를 전송하는 multicasting은 TCP에서는 불가능하다.

### 과정
client process - server process
1. client application process는 server의 process와 연결을 설정하길 원한다고 TCP client에게 알린다.
2. client의 transport layer는 server의 TCP와의 TCP 연결 설정을 진행한다. client가 TCP segment를 보낸다.
3. server는 2번째 TCP segment를 보낸다.
4. client가 3번째 TCP segment를 보낸다.

처음 2개의 segment에는 payload가 없다. payload -> application layer data
3번째 segment는 payload를 포함할 수 있다.

### TCP 연결이 설정되면
TCP 두 application process는 서로 data를 주고받을 수 있다. client는 socket을 통해 데이터의 스트림을 전달한다. data가 소켓을 통해 전달되면, 데이터는 client에서 동작하고 있는 TCP에 의해 맡겨진다. 

### maximum segment size(MSS)
segment로 모아서 담을 수 있는 최대 데이터 양은 mss로 제한된다. 
-  로컬 송신 호스트에 의해 전송될 수 있는 가장 큰 링크 계층 프레임의 길이  
(`최대 전송 단위(maximum transmission unit, MTU`)
- TCP 세그먼트(IP 데이터그램 안에 캡슐화되었을 때)와 TCP/IP 헤더 길이(통상 40바이트)가 **단일 링크 계층 프레임에 딱 맞도록** 한다.

### TCP segment
 TCP header + client data
 1. network layer에 전달되어 network layer IP datagram 안에 각각 캡슐화 된다.
 2. segment는 network로 송신된다.
 3. TCP가 상대에게서 segment를 수신했을 때, segment의 data는 TCP 연결의 수신 버퍼에 위치한다.
 + TCP 연결의 양 끝은 각각 자신의 송신 버퍼와 수신 버퍼를 가지고 있다. 
 TCP 연결은 버퍼, 변수 프로세스에 대한 소켓 연결과 반대쪽에도 똑같은 3가지 집합으로 이뤄진다.
## TCP segment 구조
header field
- source and destination port number 
- checksum field
- sequence number field(32bit)
- acknowledgement number field(32bit)
- receive window(16bit)
- header length field(4bit)
- option field(가변적 길이, mss 협상, window 확장 요소)
- flag field(6bit 포함)
-> ACK / RST, SYN, FIN (연결 설정) / PSH (데이터 상위 계층에 즉시 전달해라) / URG (긴급)

+) data field

**순서 번호**
TCP는 데이터를 구조화 되어있지 않고, 단지 순서대로 정렬되어 있는 바이트 스트림으로 본다.
 segment에 대한 순서 번호는 segment에 있는 첫 번째 바이트의 바이트 스트림 번호이다.
data stream 500000 byte, mss 1000 byte -> 500개의 segment.
TCP segment header 내부의 순서 번호 field에 삽입 된다.(0, 1000, 2000, ...)

**확인 응답 번호**
TCP가 전이중 방식이다.
B로부터 도착한 각 segment는 B로부터 A로 들어온 데이터에 대한 순서 번호를 갖는다.
A가 B로부터 0~535를 받고 900~1000을 받았다고 가정하자. 이유는 몰라도 536 ~ 899를 안받았다. A는 B의 데이터 스트림을 재생성하기 위해 536번째 바이트를 아직 기다리고 있다. B에 대한 A의 다음 segment가 **확인 응답 번호 필드**에 536을 가질 것이다. TCP가 스트림에서 첫 번째 잃어버린 바이트까지의 바이트들까지만 확인 응답하기 때문에, TCP는 cumulative acknowledgment를 제공한다.

그래서 만약 900~1000이 먼저 수신되면 순서가 꼬일 수 있다. 두 가지 선택지가 있다. 순서가 바뀐 세그먼트를 즉시 버린다. 혹은 순서가 바뀐 데이터를 보유하고, 빈 공간에 잃어버린 데이터를 채우기 위해 기다린다.
### telnet 
원격 로그인을 위해 사용되는 application layer protocol 
TCP 상에서 실행되며, 한 쌍의 호스트들 사이에서 동작하도록 설계 되었다. 

A가 B로 텔넷 세션을 시작한다고 가정하자.
A는 client B는 server
**segment의 순서 번호 = data field 안에 있는 첫 번째 바이트의 순서 번호**
**확인 응답 번호 =  호스트가 기다리는 데이터의 다음 바이트의 순서 번호**
Seq = 42 ACK = 79, data = 'C'
TCP 연결이 설정된 후에 어떤 데이터도 송신되기 전, client는 바이트 79를 기다리고 있다. 서버는 바이트 42를 기다리고 있다.  
