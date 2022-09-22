# SafetyHome
<div>
<img src="https://img.shields.io/badge/Android-3DDC84?style=flat-square&logo=Android&logoColor=white"/>
<img src="https://img.shields.io/badge/WebRTC-333333?style=flat-square&logo=WebRTC&logoColor=white"/>
<img src="https://img.shields.io/badge/PHP-777BB4?style=flat-square&logo=PHP&logoColor=white"/>
<img src="https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=MySQL&logoColor=white"/>
</div>


## 안전한나라 (Android, WebRTC)
## 목적
1. 유사 & 긴급 시 사용자의 상황을 수신인에게 알리는 앱
2. 사진 & 위치 & 문자 & 영상 & 음성 등을 간편하게 저장하고 앱&문자 알림으로 공유
3. 영상 촬영은 영상 통화 연결후 녹화 => 통화가 종료되면 자동으로 녹화된 영상을 업로드 후 알림

## 담당
- Android(JAVA) 프론트/백엔드 개발
- WebRTC (Kakao I connect) 영상통화 및 녹화 기능
- Firebase Cloud Messaging (FCM) & MMS 알림
- 녹화된 영상 및 음성 편집&합성 (FFmpeg)
- GPS 위치 공유 (좌표 <-> 주소 변환)

## 기능
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

### 4. 사이드바
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
