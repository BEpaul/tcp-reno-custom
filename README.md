# tcp-reno-custom

## 목표
- 리눅스 커널에 구현된 TCP Congestion 알고리즘 중 하나인 TCP Reno 알고리즘을 개선한 후 직접 모듈을 올려 성능 분석을 시행한다.
- 특정 네트워크 조건에서 Reno 혼잡 제어의 문제점을 분석 후 Reno 혼잡 제어 알고리즘을 수정한다.

## 상세 설명
### 실행 환경
- Linux (Ubuntu 20.04)
- gcc 7.5.0
- Mininet
- Python 3.8.10

### 평가 방법
- Example_1.py를 이용해 Bandwidth와 ping 측정
- Iperf3 tool을 이용해 Transfer, Bitrate, Retrasmission, cwnd 측정
- 실시간으로 dmesg를 통해 버퍼에 쌓여 있는 cwnd를 확인

### 수정 사항
1. cwnd 초기값 상향
2. cwnd 최솟값 상향
3. slow start/congestion avoidance 단계에서 증가폭 상향

### 결과 분석
- 특정 상황에서 Link Utilization, Latency, Fairness에 대한 전반적인 성능 개선 확인
- cnwd의 증가폭이 커진만큼, cwnd의 증감이 보다 역동적으로 발생
- 장점: 더 빠르고 많은 패킷을 전송할 수 있어 전반적인 성능 향상이 기대됨
- 단점: 패킷 손실이 자주 발생할 수 있어 불안정하고, 비용 또한 많이 소요됨