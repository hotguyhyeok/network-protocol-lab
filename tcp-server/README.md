# tcp-server

TCP 소켓 프로그래밍의 기본 동작을 직접 구현하며 이해하기 위한 서버/클라이언트 구현입니다.

## 목표

- POSIX 소켓 API(`getaddrinfo`, `socket`, `bind`, `listen`, `accept`, `connect`, `send`, `recv`)를 사용해 TCP 서버와 클라이언트를 처음부터 구현합니다.
- 3-way handshake, 연결 종료(4-way termination)과정을 코드 레벨에서 확인합니다.
- 단일 소켓으로 IPv4/IPv6 클라이언트를 모두 수락하는 듀얼스택 서버를 구현합니다.
- 단일 클라이언트를 순차 처리하는 기본 구조를 구현하고, 이후 `epoll-echo-server` 단계에서 멀티플렉싱으로 확장할 수 있는 기반을 마련합니다.

## 범위

- 구현: 단일 스레드, 블로킹 I/O 기반 에코 서버/클라이언트, IPv4/IPv6 듀얼스택
- 미포함: 멀티스레딩, I/O 멀티플렉싱(select/epoll) - 해당 내용은 `epoll-echo-server`에서 다뤄짐
- 미포함: 암호화, 인증 등 보안 관련 기능

## 실행 방법

```sh
# server execution
./tcp_server <port>

# client execution
./tcp_client <server_ip> <port>
```

## 검증 및 관찰 항목

- `tcpdump` 명령어를 이용해 이용해 handshake/termination 패킷 캡처 및 분석
- 다중 클라이언트 순차 접속 시 blocking accept로 인한 대기 현상 확인
- IPv4 클라이언트 접속 시 IPv4-mapped IPv6 주소로 수신되는지 확인

## 트러블슈팅 / 구현 노트


## 참고 자료

- *Hands-On Network Programming with C* (Lewis Van Winkle)
