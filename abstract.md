# 🛡️ SafetyHome 프로젝트 정리 (팀 공유용)

## ✅ 개요

**SafetyHome**은 긴급 상황에서 사용자의 **사진, 영상, 위치, 음성** 등을 신속하게 지정된 보호자나 수신자에게 전달하는 **안전 알림 앱**입니다. 

이 앱은 **위급 상황에 빠르게 대응**할 수 있도록 설계되었습니다. 
사용자는 단 몇 번의 터치만으로 현재 상황을 기록하고, **자동으로 보호자에게 전송**할 수 있습니다.

예를 들어, 길거리에서 위험을 느꼈을 때 카메라를 켜고 사진이나 영상을 남기거나, 음성 녹음을 시작하고 현재 위치를 함께 전송할 수 있습니다. 이렇게 수집된 정보는 **사전에 등록된 보호자**에게 **푸시 알림 또는 문자 메시지**를 통해 전달됩니다.

즉, SafetyHome은 사용자가 위험을 감지한 순간부터 **간편하고 빠르게 도움을 요청할 수 있는 통로** 역할을 합니다. 특히 고령자, 여성, 어린이, 1인 가구 등을 대상으로 한 실생활 안전 도구로도 활용 가능합니다.

---

## 🧱 전체 구조 및 화면 구성

### 📱 개발 플랫폼
- Android 기반 모바일 앱 (자바 사용)
- 기본적인 로그인 후 메인 화면에서 **촬영**, **영상 통화**, **위치 전송** 등의 기능을 제공

### 📌 주요 화면 목록

| 화면 | 역할 |
|------|------|
| 앱 시작 화면 (Splash) | 자동 로그인 여부 확인 |
| 로그인 / 가입 | 사용자 인증 및 기본 정보 입력 |
| 메인 화면 | 탭과 사이드 메뉴를 통해 주요 기능에 접근 |
| 사진 촬영 | 사진을 찍고 바로 전송 가능 |
| 영상 통화 | 보호자와 실시간 영상 연결 |
| 위치 전송 | GPS 기반 위치 + 음성 메시지 전송 |
| 설정 | 수신자 추가/수정, 사용 모드 설정 |
| 알림 수신 | 보호자 쪽에서 알림 수신 확인 |

### 🔁 화면 간 흐름

- 앱을 실행하면 → 로그인 상태 확인 → 메인으로 이동  
- 메인 화면에서는 하단 탭으로 기능 전환  
- 사이드 메뉴에서는 개인정보나 수신자 설정 가능  
- 각 기능(촬영/통화/위치)은 실행 즉시 기록 후 자동 전송됨  

---

## ⚙️ 작업 방식

| 구분 | 설명 |
|------|------|
| **디자인** | 사전 기획안을 바탕으로 Photoshop 에서 레이어 작업, 이후 png 이미지와 원본 psd 파일 개발과 공유|
| **개발** | 기능별로 화면을 나누고, 각 화면에 필요한 기능을 독립적으로 구성<br>(예: 사진 촬영, 영상통화, 위치 전송 등) |
| **기획** | 사용자 시나리오 기반으로 간단하고 빠르게 동작할 수 있도록 흐름 설계<br>위급한 상황을 가정해 최소한의 조작으로도 전송되도록 함 |
| **저장 및 전송** | 기록된 사진/영상/위치/음성은 자동으로 서버 또는 보호자에게 전송되며, 알림도 함께 전송됨 |
| **알림 처리** | 보호자는 푸시 알림 또는 문자로 바로 상황을 확인할 수 있음 |
| **기록 병합** | 영상 통화와 별도로 녹음된 음성은 자동으로 하나의 파일로 합쳐져 전송됨 (사용자는 인식하지 못해도 무방함) |

---

## 🧭 작업 순서

### 1. 흐름 및 시나리오 정리
- 긴급 상황 기준의 행동 플로우 작성
- 보호자에게 어떤 정보가 전달되어야 하는지 구체화

### 2. 전체 화면 구성 스케치
- 기능 별 페이지 정의 (촬영, 통화, 위치, 설정 등)
- 하단 탭 + 사이드 메뉴 구조 도입

### 3. 화면 디자인
- 사용자 친화적인 인터페이스 구성
- 조작 버튼은 크고 명확하게 구성
- 색상은 경고/안전 등 상황 구분이 쉬운 계열로 사용

### 4. 기능 구현
- 각 화면에서 동작하는 기능 개별 개발
- 사진/영상/위치/음성 기록 후 자동 전송 처리
- 녹화 영상과 음성을 하나의 파일로 합치는 작업 처리 (백그라운드에서 자동 실행)

### 5. 테스트
- 실제 긴급 상황을 가정해 기능 수행 테스트
- Wi-Fi 또는 모바일 데이터 환경에서 알림 지연 여부 확인
- 보호자 쪽에서 알림 수신 확인

### 6. 배포 및 공유
- 팀 내부 테스트용으로 APK 배포
- Play Store 등록은 기획과 일정 논의 후 결정

---

## 🚀 작업 결과물
### 1. 로그인 관련
 - 회원가입 및 로그인
<div align="center" >
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/real/1.%20메인.jpeg" width="20%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/6.%20회원가입%20-%20약관동의.png" width="20%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/8.%20회원가입%20-%20정보%20입력.png" width="20%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/2.%20로그인.png" width="20%"/>
</div></br>

 - 아이디 찾기 & 비밀번호 찾기
 <!--
<div align="center">
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/3.%20아이디찾기.png" width="25%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/4.%20비밀번호%20찾기.png" width="25%"/>
</div></br>
-->
### 2. 촬영모드
 - 사진&문자 전송 (메인, 문자입력, 상단알람, 사진확인)
<div align="center">
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/10.%20촬영모드%20-%20메인.png" width="23%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/real/4-2%20문자%20전송(입력).jpeg" width="23%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/real/4-3%20사진&문자&위치%20알람.jpeg" width="23%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/real/5-7%20공유된%20사진%20확인.jpeg" width="23%"/>
</div></br>

 - 영상 통화 및 촬영 (메인, 영상통화, 상단알람, 영상확인)
<div align="center">
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/10.%20촬영모드%20-%20메인.png" width="23%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/real/5-4%20영상%20통화%20화면.jpeg" width="23%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/real/5-2%20영상%20공유%20알림.jpeg" width="23%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/real/5-6%20녹화된%20영상%20확인.jpeg" width="23%"/>
</div></br>

### 3. 위치모드
- 사진 & 위치 전송
- 음성녹음 
<div align="center">
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/19.%20위치모드.png" width="23%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/real/6-3%20음성%20녹음.jpeg" width="23%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/real/6-4%20음성%20전송.jpeg" width="23%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/real/6-6%20음성%20확인.jpeg" width="23%"/>
</div></br>

- 긴급전화
<div align="center">
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/19.%20위치모드.png" width="23%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/real/6-8%20긴급%20전화연결.jpeg" width="23%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/real/6-9%20긴급%20전화연결%20호출중.jpeg" width="23%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/real/6-10%20긴급%20전화연결중.jpeg" width="23%"/>
</div></br>

### 4. 사이드
- 회원정보 & 수신인 변경 : 회원정보변경(상단,하단), 수신인 (신규등록, 정보변경)
<div align="center">
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/real/3-1%20회원정보%20변경%20(상단).jpeg" width="23%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/real/3-2%20회원정보%20변경%20(하단).jpeg" width="23%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/real/3-3%20수신인%20신규%20등록.jpeg" width="23%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/real/3-4%20수신인%20정보%20변경.jpeg" width="23%"/>
</div></br>

### 5. 설정
- 촬영모드 & 위치모드 설정 : 촬영모드 설정(일반, GPS), 위치모드 설정(일반, GPS) 
<div align="center">
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/49%20촬영모드%20설정.png" width="23%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/50%20촬영모드%20설정(GPS).png" width="23%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/51%20위치모드%20설정.png" width="23%"/>
&nbsp;&nbsp;&nbsp;
<img src="https://github.com/cjk09083/SafetyHome/blob/main/ScreenShot/52%20위치모드%20설정(GPS).png" width="23%"/>
</div></br>
