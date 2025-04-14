
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

---

## ⚙️ 개발 방식

| 항목 | 방식 | 설명 |
|------|------|------|
| **개발 환경** | Android Studio (Java 1.8), Gradle | gradle 7.x, minSdk 24 기준 |
| **버전 관리** | Git + GitHub | Git CLI 사용, 단일 main 브랜치 운영 |
| **설계 방법** | 모듈 기반 액티비티-프래그먼트 구조 | MainActivity 기준 탭 이동 처리 |
| **UI 개발** | XML + FragmentManager | BottomNavigationView + Fragment 교체 |
| **탭 구성 방식** | BottomNavigationView (`activity_main.xml`) | Camera, VideoCall, Location 탭으로 구성 |
| **사이드메뉴** | DrawerLayout + NavigationView | 수신자 설정, 개인정보 진입 |
| **알림 방식** | `FirebaseMessagingService` 상속 | `onMessageReceived()` override |
| **영상 처리** | `Camera Intent` + WebRTC + FFmpeg | 영상 통화 후 `onPeerLeft()`에서 자동 저장 |
| **음성 녹음** | `MediaRecorder` → `.m4a` 저장 | `startRecording()`, `stopRecording()` 직접 구현 |
| **파일 업로드** | `HttpURLConnection` + POST multipart | 서버 업로드 후 응답 처리 |
| **위치 수신** | `LocationManager` + `Geocoder` | 실시간 위치와 주소 표시 |
| **보안 처리** | 권한 요청 (`ActivityCompat.requestPermissions`) | 위치, 카메라, 마이크, 저장소 권한 필수 체크 |

---

## 🧭 개발 순서 (실제 구현 중심)

### 1. 프로젝트 초기화 및 Gradle 설정
- Firebase SDK, WebRTC SDK, Mobile-FFmpeg 의존성 추가
- `AndroidManifest.xml`에 필수 권한 선언 (CAMERA, RECORD_AUDIO, ACCESS_FINE_LOCATION 등)

### 2. 로그인 및 회원가입 구현
- `LoginActivity.java`, `SignupActivity.java` 작성
- `SharedPreferences`로 자동 로그인 상태 유지
- Retrofit 없이 간단한 로그인 로직 (FirebaseAuth 연동 가능)

### 3. 탭 레이아웃 및 프래그먼트 연결
- `activity_main.xml` 내 `BottomNavigationView` 선언
- `MainActivity.java` → `replaceFragment()` 함수로 각 프래그먼트 연결

```java
private void replaceFragment(Fragment fragment) {
    getSupportFragmentManager().beginTransaction()
        .replace(R.id.main_frame, fragment)
        .commit();
}
```

### 4. 촬영 모드 (CameraFragment)
- 사진 촬영: `Intent(MediaStore.ACTION_IMAGE_CAPTURE)`
- 영상 통화: `VideoCallFragment` + Kakao I WebRTC SDK
- 영상 녹화: WebRTC 종료 시 저장 (`onPeerLeft()` 내부)
- 영상 업로드: `UploadService.java`에서 파일 전송

### 5. 위치 모드 (LocationFragment)
- `LocationManager.requestLocationUpdates()`로 실시간 GPS 수신
- `Geocoder`로 주소 텍스트 변환
- `MediaRecorder`로 음성 녹음 `.m4a` 생성
- `Intent.ACTION_CALL`로 긴급 번호 연결

### 6. 사이드 메뉴 및 설정 페이지
- `NavigationView`로 메뉴 전환
- 수신인 추가/삭제 기능 → SQLite or JSON 저장
- 설정화면: `SettingsActivity`에서 SwitchCompat로 모드 설정 저장

### 7. 알림 처리 (FCMService)
- `MyFirebaseMessagingService` extends `FirebaseMessagingService`
- `onMessageReceived()`에서 알림 도착 시 Notification 출력
- 백그라운드 수신 및 디바이스별 토큰 저장

### 8. 테스트 및 배포
- Android 10 이상 디바이스로 실기기 테스트
- 네트워크 지연 상황에서 영상/음성/위치 전송 시나리오별 QA
- APK 파일 내장 서명 후 배포 (ADB push, 내부 웹 배포 가능)







---

## 📌 확장/개선 포인트

| 영역 | 개선 방안 |
|------|-----------|
| 상태관리 | ViewModel + LiveData 구조 적용 |
| UI 구조 | Jetpack Compose 도입 가능 |
| 보안 | HTTPS 업로드, Firebase Auth 토큰 인증 추가 |
| UX | 알림 히스토리 저장, 상황 로그 서버 전송 |
| 관리자 연동 | 수신자용 웹 대시보드 (React + Firebase) 구성 |
