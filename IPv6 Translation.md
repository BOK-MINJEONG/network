# IPv6 Transition 환경에서의 Packet Translation과 NAT64

> IPv6 Client는 IPv4 Server와 어떻게 통신하는가?

### IPv4, IPv6
IPv6는 오래전에 등장했지만 현실 인터넷은 아직 IPv4 기반 서비스가 굉장히 많음.   
특히 실제 운영 환경에서는 IPv6-only-Client가 IPv4 Server와 통신해야 하는 상황이 자주 발생.   
그 과정에서 Translation 기술, 특히 NAT54와 DNS64가 실제로 패킷을 어떻게 변환하는지를 중심으로 다룸.   


### Packet, IPv6 Transition
- IPv4 Packet
  - Source IP
  - Destination IP
  - TTL
  - Protocol

Translation 기술은 결국 이 패킷 헤더를 수정하는 기술.   
Source, Destination Address와 port를 변경해서 서로 다른 네트워크 환경을 연결


### IPv6 Transition 기술
(방식 - 특징)
- Dual Stack: IPv4/IPv6 동시 사용
- Tunneling: IPv6 Encapsulation
- **Transition**: Header Rewrite


### NAT64 / DNS64
- 현실에서는 IPv6-only Client -> IPv4-only Server로 통신하는 경우가 많음   
근데 IPv6 Client는 IPv4 주소를 직접 이해할 수 없음. 그럼 어떻게 IPv4 Server와 통신을 할까?


### DNS64 + NAT64
![FLOW](image-1.png)   

#### DNS64
> DNS64는 IPv4-only 서버에 AAAA 레코드가 없을 경우, A 레코드를 기반으로 가상의 AAAA 레코드를 생성. 이때 prefix가 반드시 필요함
- well known prefix: **64:ff9b::/96**    
-> embedded 형식
