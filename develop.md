
# 🛡️ SafetyHome 프로젝트 정리

## ✅ 개요
긴급 상황 시 사용자의 사진, 영상, 위치, 음성 등의 정보를 수신자에게 빠르게 전달하여 안전을 확보하기 위한 Android 기반 애플리케이션.

---

## 🧱 개발 구조

### 📱 플랫폼
- Android (Java 기반)

### 🛠️ 주요 기술 스택
- **WebRTC (Kakao I Connect SDK)** – 영상 통화 및 녹화 처리
- **Firebase Cloud Messaging (FCM)** – 실시간 알림 및 토큰 관리
- **FFmpeg (Mobile-FFmpeg)** – 영상 + 음성 합성 처리
- **LocationManager + Geocoder** – GPS 위치 수신 및 주소 변환
- **MediaRecorder / MediaPlayer** – 음성 녹음 및 재생

---

## 🖥️ 화면 구성 목록

| 화면 명칭 | 설명 |
|-----------|------|
| `SplashActivity` | 앱 로딩 및 자동 로그인 확인 |
| `LoginActivity` | 사용자 로그인 |
| `SignupActivity` | 회원가입 및 정보 입력 |
| `MainActivity` | 하단 탭 및 사이드 메뉴 포함 메인 화면 |
| `CameraFragment` | 사진 촬영 기능 |
| `VideoCallFragment` | 실시간 영상 통화 및 녹화 |
| `LocationFragment` | 위치 전송, 주소 확인, 음성 녹음, 긴급전화 |
| `SettingsActivity` | 사용자 설정 (모드 설정 등) |
| `ReceiverListActivity` | 수신자 목록 관리 (추가/삭제) |
| `UserProfileActivity` | 내 정보 확인 및 수정 |
| `UploadService.java` | 백그라운드 파일 업로드 처리 |
| `MyFirebaseMessagingService.java` | 푸시 알림 수신 처리 |

---

## 🔄 화면 간 연계 구조

```
SplashActivity
   └── 자동 로그인 여부 → LoginActivity 또는 MainActivity

LoginActivity
   └── 회원 로그인 성공 → MainActivity

SignupActivity
   └── 회원가입 완료 → LoginActivity

MainActivity (탭 + Drawer)
   ├── 하단 탭
   │   ├── CameraFragment (사진촬영)
   │   ├── VideoCallFragment (영상통화)
   │   └── LocationFragment (위치 전송, 음성 녹음, 긴급전화)
   └── 사이드 메뉴
       ├── UserProfileActivity (내 정보 수정)
       ├── ReceiverListActivity (수신자 관리)
       └── SettingsActivity (촬영/위치 모드 설정)

CameraFragment
   └── 사진 촬영 후 자동 업로드 → UploadService 호출

VideoCallFragment
   └── 통화 종료 시 영상 저장 + 업로드 → UploadService

LocationFragment
   ├── 위치 수신 + 전송
   ├── 음성 녹음 파일 저장 → UploadService
   └── 긴급전화 호출

MyFirebaseMessagingService
   └── 수신자 앱 → 푸시 알림 수신 → Notification 표시
```

---

위 연계 구조는 실제 Activity와 Fragment 흐름에 맞춰 설계되었으며, 사용자가 앱을 시작해 긴급상황을 알릴 때까지의 전체 흐름을 포함합니다.
