MARK.0 Prototype
저비용 열감지 인명탐색 드론

교육·연구 목적의 열감지 인명탐색 드론 시제품입니다.
Pixhawk 기반 비행제어와 ESP32 열화상 처리를 결합하여 실종자 탐색을 지원하는 시스템을 구현하였습니다.

📌 문제 정의 (Problem)

재난·산악 지역에서의 실종자 수색은 넓은 지역을 장시간 탐색해야 하므로 많은 인력과 시간이 필요합니다.

기존 산업용 열화상 드론은 가격이 매우 높아 교육기관이나 학생 프로젝트에서 활용하기 어렵고, 일반 드론은 영상만 제공하기 때문에 신속한 탐색에 한계가 있습니다.

본 프로젝트는 100만원 수준의 예산으로 제작 가능한 열감지 드론을 목표로 하였으며,

열원을 탐지하여 구조대원에게 알려주고
GPS 위치를 함께 확인하며
스마트폰에서 실시간으로 상태를 확인할 수 있는

교육 및 연구용 인명탐색 시스템을 구현하는 것을 목표로 합니다.

🏗 시스템 아키텍처 (Architecture)
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
주요 기능
Pixhawk 기반 자동비행
GPS 위치 확인
자동복귀(RTL)
MLX90640 열원 탐지
일반 카메라 촬영
microSD 저장
스마트폰 웹 모니터링
LED / 부저 경고
도킹 감지 시연
🛠 사용 기술 (Tech Stack)
Flight Controller
Pixhawk
ArduPilot (ArduCopter)
Embedded
Seeed XIAO ESP32-S3 Sense
Arduino UNO R4 Minima
Sensor
MLX90640 Thermal Camera
GPS + Compass
Communication
MAVLink
ESP8266 Wi-Fi Telemetry
Wi-Fi
Software
Arduino IDE
QGroundControl
Mission Planner
🚀 실행 방법 (Getting Started)
1. Pixhawk 설정
ArduCopter 설치
Quad X 선택
센서 보정
조종기 보정
ESC 확인
2. ESP32 업로드
MLX90640 초기화
카메라 실행
Web Server 실행
3. Arduino 업로드
LED
부저
서보
도킹 센서
4. 스마트폰 연결
ESP8266 Telemetry 연결
QGroundControl 실행
기체 연결 확인
5. 열원 탐지
열원 감지
    ↓
사진 촬영
    ↓
microSD 저장
    ↓
웹페이지 알림
    ↓
LED / 부저 경고
🤖 AI 사용 내역 (AI Usage)

본 프로젝트에서는 생성형 AI를 개발 보조 도구로 활용하였습니다.

활용 분야	내용
시스템 설계	전체 시스템 구조 및 모듈 구성 검토
코드 작성	Arduino 및 ESP32 예제 코드 생성 및 수정
코드 리뷰	오류 분석 및 개선 방향 제안
문서 작성	README, 제작 설명서, 발표자료 작성 지원
알고리즘 설계	열원 탐지 흐름 및 데이터 처리 로직 정리

AI는 설계와 개발을 지원하는 도구로 활용되었으며, 최종 구현 및 검증은 프로젝트 팀이 직접 수행하였습니다.

📚 AI 모델 · 오픈소스 · 외부 자문 명시
AI 모델
구분	사용 내용
ChatGPT (OpenAI GPT-5.5)	시스템 설계 검토, 코드 작성 보조, 문서 작성, 알고리즘 검토
사용한 오픈소스
프로젝트	라이선스	용도
ArduPilot (ArduCopter)	GPLv3	드론 비행 제어
QGroundControl	Apache 2.0	드론 모니터링 및 설정
MAVLink	LGPL	Pixhawk 통신 프로토콜
Arduino Framework	LGPL	임베디드 개발
ESP32 Arduino Core	Apache 2.0	ESP32 개발 환경
외부 자문

본 프로젝트는 생성형 AI를 활용하여 설계 및 문서화를 지원받았으며,

드론 시스템 구성
소프트웨어 구조 설계
문서 작성
코드 리뷰

과정에서 AI의 도움을 받았습니다.

외부 전문가의 직접적인 기술 자문은 받지 않았습니다.

📄 라이선스 (License)

본 프로젝트는 교육 및 연구 목적으로 제작되었습니다.

비상업적 교육 활용 가능
출처 표기 권장
실제 구조 현장에 사용하기 위한 인증 장비가 아님

소스코드는 MIT License를 적용하는 것을 권장합니다.

MIT License

Copyright (c) 2026 TEAM MARK.0

Permission is hereby granted, free of charge,
to any person obtaining a copy of this software...
