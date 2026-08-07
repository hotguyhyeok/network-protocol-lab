# Network Protocol Lab

TCP, UDP, QUIC의 동작 원리를 직접 구현하고 비교 실험하며, 저수준 네트워크 프로그래밍에 대한 이해를 검증하기 위한 프로젝트입니다.

## 동기

네트워크 스택을 이론으로만 이해하는 데 그치지 않고, 직접 구현하고 실험하면서 각 프로토콜이 왜 그렇게 설계되었는지를 몸으로 확인하고 싶었습니다. 특히 TCP의 신뢰성 보장 메커니즘(재전송, 혼잡제어)과 UDP 기반 프로토콜인 QUIC가 이를 어떻게 다른 방식으로 해결하는지를 비교하는 데 관심이 있습니다.

## 프로젝트 목표

- TCP/UDP 서버를 직접 구현하며 소켓 프로그래밍과 프로토콜 동작을 코드 레벨에서 이해한다.
- select/epoll 기반 멀티플렉싱을 적용해 다중 클라이언트 처리 방식을 비교한다.
- 인위적인 패킷 손실/지연 환경에서 TCP의 재전송 동작을 관찰하고 측정한다.
- 기존 QUIC 라이브러리를 활용한 비교 실험을 통해, TCP/UDP 구현 경험을 바탕으로 QUIC의 설계상 이점과 트레이드오프를 분석한다.
- 위 결과를 정량적으로 비교(연결 설정 시간, 처리량, 손실 복구 시간 등)하여 정리한다.

## 프로젝트 구성

| 디렉토리 | 설명 | 상태 |
|---|---|---|
| [`tcp-server`](./tcp-server) | 기본 TCP 서버/클라이언트 구현 | 진행 중 |
| [`udp-server`](./udp-server) | 기본 UDP 서버/클라이언트 구현 | 진행 예정 |
| [`epoll-echo-server`](./epoll-echo-server) | select/epoll 기반 멀티플렉싱 에코 서버 | 진행 예정 |
| [`packet-loss-simulation`](./packet-loss-simulation) | `tc netem`을 이용한 패킷 손실/지연 시뮬레이션 및 TCP 재전송 관찰 | 진행 예정 |
| [`quic-experiment`](./quic-experiment) | 기존 QUIC 라이브러리 기반 비교 실험 | 진행 예정 |
| [`multi-protocol-client`](./multi-protocol-client) | TCP/UDP/QUIC 호환 클라이언트 | 진행 예정 |
| [`benchmarks`](./benchmarks) | 프로토콜별 성능 비교 및 종합 분석 | 진행 예정 |


## 개발 환경

- 언어: C
- OS: EC2(AWS) - Ubuntu24.04
- 도구: Git, Vim, AWS(테스트 환경), `tc netem`(네트워크 시뮬레이션)

## 참고 자료

- *Hands-On Network Programming with C* (Lewis Van Winkle)
