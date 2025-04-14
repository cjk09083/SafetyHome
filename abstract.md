# 🛡️ SafetyHome 프로젝트 정리 (팀 공유용)

## ✅ 개요

**SafetyHome**은 긴급 상황에서 사용자의 **사진, 영상, 위치, 음성** 등을 신속하게 지정된 보호자나 수신자에게 전달하는 **안전 알림 앱**입니다. 

이 앱은 **위급 상황에 빠르게 대응**할 수 있도록 설계되었습니다. 
사용자는 단 몇 번의 터치만으로 현재 상황을 기록하고, **자동으로 보호자에게 전송**할 수 있습니다.

예를 들어, 길거리에서 위험을 느꼈을 때 카메라를 켜고 사진이나 영상을 남기거나, 음성 녹음을 시작하고 현재 위치를 함께 전송할 수 있습니다. 이렇게 수집된 정보는 **사전에 등록된 보호자**에게 **푸시 알림 또는 문자 메시지**를 통해 전달됩니다.

즉, SafetyHome은 사용자가 위험을 감지한 순간부터 **간편하고 빠르게 도움을 요청할 수 있는 통로** 역할을 합니다. 특히 고령자, 여성, 어린이, 1인 가구 등을 대상으로 한 실생활 안전 도구로도 활용 가능합니다.

---

## 🧱 전체 구조 및 작업 환경

### ⚙️ 작업 환경
- 개발 툴: Android Studio (Java 기반)
- 운영체제: Android OS 10 이상 권장
- 화면 설계 도구: Figma, PPT 스케치
- 버전 관리: GitHub 사용, main 브랜치 기준 협업
- 앱 구조: 화면 단위 기능 모듈 설계

### 📱 개발 플랫폼
- Android 기반 모바일 앱 (자바 사용)
- 기본적인 로그인 후 메인 화면에서 **촬영**, **영상 통화**, **위치 전송** 등의 기능을 제공

### 📌 주요 화면 구성

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

| 항목 | 방식 | 설명 |
|------|------|------|
| **작업 도구** | Android Studio | 모바일 앱 개발에 사용하는 대표적인 개발 환경 |
| **기록 및 저장** | Git + GitHub | 작업 내용을 버전별로 관리하고 백업할 수 있는 도구 |
| **기능 구성** | 화면 단위로 나눠 개발 | 각 기능(촬영, 위치, 통화 등)을 별도 화면으로 구성하고 연결 |
| **화면 구성** | 버튼 + 메뉴 방식 | 주요 기능은 탭 버튼, 설정 등은 사이드 메뉴로 진입 |
| **기능 전환 방식** | 하단 탭 메뉴 | 사용자 친화적으로 기능 이동이 가능하도록 구성 |
| **사이드 메뉴** | 왼쪽에서 열리는 설정창 | 개인정보, 수신자 목록, 사용 설정 접근에 활용 |
| **알림 전달** | 푸시 알림 또는 문자 메시지 | 보호자에게 상황 발생 즉시 알려줌 |
| **영상 처리 방식** | 영상 + 음성 자동 저장 및 합성 | 영상통화 종료 시 자동으로 저장되고, 녹음한 음성과 하나로 병합 |
| **음성 녹음** | 앱 내 녹음 기능 | 버튼을 누르면 자동 녹음되어 저장됨 |
| **자료 전송 방식** | 서버로 자동 업로드 | 촬영한 사진, 영상 등은 자동으로 보호자에게 전달됨 |
| **위치 수신** | 휴대폰 GPS 활용 | 현재 위치를 실시간으로 받아서 함께 전송함 |
| **보안 기능** | 접근 권한 확인 | 위치, 마이크, 카메라 등 민감 정보 접근은 사용자 동의 필요 |

---

## 🧭 작업 순서
### 1. 초기 기획 회의
- 기획자와 함께 전체 앱의 목적과 사용자 흐름 논의
- 핵심 기능 도출 및 필요한 화면 구성 도식화

### 2. 화면 구성 및 기능 검토
- 개발자가 전체 페이지 구조 및 기능 흐름을 초안으로 구성
- 기획자와 함께 탭 구성, 사이드 메뉴, 버튼 위치 등 상세 동선 검토

### 3. 디자인 제작 및 전달
- 기획자가 Photoshop을 활용해 화면 디자인을 제작
- 각 화면을 `.psd` 원본 파일과 `.png` 미리보기 이미지로 개발자에게 전달

### 4. 앱 퍼블리싱 및 기능 구현
- 개발자가 전달받은 디자인을 기반으로 Android 화면 퍼블리싱 진행
- 각 기능(촬영 모드, 위치모드, 설정 및 관리 등) 모듈화하여 구현
#### 📸 촬영 모드
- 카메라 호출 → 사진 촬영 → 전송 버튼 클릭 시 자동 서버 업로드
- 영상 통화 버튼 → 상대 연결 → 통화 종료 시 자동 녹화 파일 저장 및 보호자 전송

#### 📍 위치 모드
- 현재 위치 자동 표시 (지도 기반 주소 변환)
- 녹음 버튼 클릭 시 음성 기록 → 저장 후 보호자에게 함께 전송
- 긴급 전화 버튼 → 사전 지정 번호로 즉시 전화 연결

#### ⚙️ 설정 및 관리
- 사용자는 수신자 목록을 추가/수정할 수 있으며, 저장된 설정에 따라 알림 대상 자동 결정
- 앱 내 설정에서 모드별 기능 활성/비활성 설정 가능
  
### 5. 테스트
- 실제 긴급 상황을 가정해 기능 수행 테스트
- Wi-Fi 또는 모바일 데이터 환경에서 알림 지연 여부 확인
- 보호자 쪽에서 알림 수신 확인

### 6. 배포 및 공유
- 팀 내부 테스트용으로 APK 배포
- Play Store 등록 후 공식배포

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





