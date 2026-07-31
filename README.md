# MARK.0 Prototype

### 저비용 열감지 인명탐색 드론

> 교육·연구 목적의 열감지 인명탐색 드론 시제품입니다.
> Pixhawk 기반 비행제어와 ESP32 열화상 처리를 결합하여 실종자 탐색을 지원하는 시스템을 구현하였습니다.

---

# 📌 문제 정의 (Problem)

재난·산악 지역에서의 실종자 수색은 넓은 지역을 장시간 탐색해야 하므로 많은 인력과 시간이 필요합니다.

기존 산업용 열화상 드론은 가격이 매우 높아 교육기관이나 학생 프로젝트에서 활용하기 어렵고, 일반 드론은 영상만 제공하기 때문에 신속한 탐색에 한계가 있습니다.

본 프로젝트는 **100만원 수준의 예산으로 제작 가능한 열감지 드론**을 목표로 하였으며,

- 열원을 탐지하여 구조대원에게 전달
- GPS 위치를 함께 확인
- 스마트폰에서 실시간으로 기체 상태 확인

이 가능한 저비용 인명탐색 시스템을 구현하는 것을 목표로 합니다.

---

# 🏗 시스템 아키텍처 (Architecture)

```text
                     3S LiPo Battery
                            │
             ┌──────────────┴──────────────┐
             │                             │
      Pixhawk Flight Controller         5V UBEC
             │                             │
             │                    ┌────────┴────────┐
             │                    │                 │
       GPS / Compass      XIAO ESP32-S3 Sense   Arduino UNO R4
             │                    │                 │
      FlySky Receiver      MLX90640 + Camera   LED / Buzzer / Servo
             │                    │                 │
             └────────── Wi-Fi Telemetry ──────────┘
                            │
                    Smartphone Dashboard
```

### 구성 요소

#### Pixhawk
- 비행 안정화
- GPS 위치 제어
- 자동복귀(RTL)
- 배터리 모니터링

#### XIAO ESP32-S3 Sense
- MLX90640 열화상 처리
- 일반 카메라 촬영
- Web Server
- microSD 저장

#### Arduino UNO R4
- LED 상태 표시
- 부저 경고
- 서보 제어
- 도킹 감지

---

# 🛠 사용 스택 (Tech Stack)

## Flight Controller

- Pixhawk
- ArduPilot (ArduCopter)

## Embedded

- Seeed XIAO ESP32-S3 Sense
- Arduino UNO R4 Minima

## Sensor

- MLX90640 Thermal Camera
- GPS + Compass

## Communication

- MAVLink
- ESP8266 Wi-Fi Telemetry
- Wi-Fi

## Software

- Arduino IDE
- QGroundControl
- Mission Planner

---

# 🚀 실행 방법 (Getting Started)

## 1. Pixhawk 설정

- ArduCopter 설치
- Quad X 프레임 선택
- 가속도계 및 나침반 보정
- 조종기 보정
- ESC 테스트

## 2. ESP32 업로드

- MLX90640 초기화
- 카메라 실행
- Web Server 실행

## 3. Arduino 업로드

- LED
- 부저
- 서보
- 도킹 센서 제어 프로그램 업로드

## 4. 스마트폰 연결

- ESP8266 Telemetry 연결
- QGroundControl 실행
- 기체 연결 확인

## 5. 열원 탐지

```text
열원 감지
    ↓
사진 촬영
    ↓
microSD 저장
    ↓
웹페이지 알림
    ↓
LED / 부저 경고
```

---

# 🤖 AI 사용 내역 (AI Usage)

본 프로젝트에서는 생성형 AI를 개발 보조 도구로 활용하였습니다.

| 활용 분야 | 내용 |
|-----------|------|
| 시스템 설계 | 전체 시스템 구조 및 모듈 구성 검토 |
| 코드 작성 | Arduino 및 ESP32 예제 코드 생성 및 수정 |
| 코드 리뷰 | 오류 분석 및 개선 방향 제안 |
| 문서 작성 | README, 제작 설명서, 발표자료 작성 |
| 알고리즘 설계 | 열원 탐지 로직 및 데이터 처리 흐름 정리 |

> AI는 개발을 지원하는 보조 도구로 활용되었으며, 최종 설계·구현·시험은 프로젝트 팀이 직접 수행하였습니다.

---

# 📚 AI 모델 · 오픈소스 · 외부 자문 명시

## AI 모델

| 모델 | 활용 내용 |
|------|----------|
| ChatGPT (OpenAI GPT-5.5) | 시스템 설계 검토, 코드 작성 보조, 문서 작성, 알고리즘 검토 |

---

## 오픈소스

| 프로젝트 | 라이선스 | 활용 목적 |
|-----------|----------|-----------|
| ArduPilot (ArduCopter) | GPL v3 | 비행 제어 |
| QGroundControl | Apache License 2.0 | 비행 상태 확인 및 설정 |
| MAVLink | LGPL | Pixhawk 통신 |
| Arduino Framework | LGPL | 임베디드 개발 |
| ESP32 Arduino Core | Apache License 2.0 | ESP32 개발 환경 |

---

## 외부 자문

본 프로젝트는 생성형 AI를 활용하여 다음과 같은 부분의 도움을 받았습니다.

- 시스템 설계 검토
- 문서 작성
- 코드 리뷰
- 알고리즘 정리

외부 전문가의 직접적인 기술 자문은 받지 않았습니다.

---

# 📄 라이선스 (License)

본 프로젝트는 교육 및 연구 목적으로 제작되었습니다.

- 비상업적 교육 목적 사용 가능
- 출처 표기 권장
- 실제 재난 구조용 인증 장비가 아닌 교육용 시제품
