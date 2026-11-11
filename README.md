# QR Master - Android WebView App

웹 기반 QR 코드 생성 및 실시간 카메라/이미지 스캔 서비스([https://cjaeu7382-spe.github.io/QR/](https://cjaeu7382-spe.github.io/QR/))를 안드로이드 네이티브 앱 환경으로 제공하는 웹뷰 애플리케이션입니다.

---

## 📱 주요 특징 및 기능

1. **완벽한 웹뷰(WebView) 최적화**
   - JavaScript, DOM Storage, Database 활성화
   - 당겨서 새로고침(Swipe-to-Refresh) 지원
   - 상단 부드러운 로딩 진행바(Progress Bar) 연동
   - 네트워크 연결 끊김 시 재시도 안내 화면 제공
   - 스마트 백버튼 처리 (이전 페이지 이동 및 두 번 터치 시 앱 종료)

2. **실시간 QR 스캔 및 카메라/미디어 권한 연동**
   - `WebChromeClient.onPermissionRequest` 완벽 구현으로 웹 기반 실시간 카메라 스캔 지원
   - `ActivityResultLauncher` 기반 안드로이드 런타임 카메라 권한 요청
   - 이미지 파일 업로드를 통한 QR 스캔 파일 선택기(`onShowFileChooser`) 지원

3. **QR 코드 이미지 다운로드 지원**
   - 안드로이드 시스템 `DownloadManager` 연동으로 생성된 QR 코드 이미지를 기기에 안전하게 다운로드

4. **세련된 모던 런처 아이콘**
   - 밝고 세련된 디자인 (QR 코드 매트릭스 + 네온 레이저 스캔 빔 + 생성 스파크 + 일렉트릭 바이올렛/사이언 그라디언트)
   - 표준 해상도별 Mipmap 아이콘(`mdpi`, `hdpi`, `xhdpi`, `xxhdpi`, `xxxhdpi`) 및 원형(Round) 아이콘 탑재

5. **GitHub Actions 자동 빌드 시스템 구축**
   - 로컬에 Android Studio가 없어도 GitHub에 Push하면 클라우드에서 자동으로 APK 빌드
   - 완료 후 GitHub 저장소 `Actions` 탭의 **Artifacts**에서 즉시 `.apk` 파일 다운로드 가능

---

## 🚀 GitHub에 업로드하고 APK 빌드하는 방법

로컬 컴퓨터에 Android Studio가 없으므로 아래 순서대로 GitHub 저장소를 연결해 Push하시면 됩니다.

### 1. GitHub에서 새 저장소(Repository) 생성
- [GitHub](https://github.com)에 로그인 후 새 Repository를 생성합니다 (예: `QR-Master-Android`).

### 2. 터미널(PowerShell 또는 Git Bash)에서 원격 저장소 연결 후 Push
```bash
# 1. 파일 추가 및 첫 커밋
git add .
git commit -m "Initial commit: QR Master Android WebView App"

# 2. 브랜치를 main으로 설정
git branch -M main

# 3. 본인의 GitHub 저장소 주소로 원격 연결
git remote add origin https://github.com/<본인-깃허브-아이디>/<저장소-이름>.git

# 4. GitHub에 푸시
git push -u origin main
```

### 3. 빌드된 APK 다운로드
1. GitHub 저장소 상단의 **Actions** 탭으로 이동합니다.
2. 실행 중이거나 완료된 **Android Build** 워크플로우를 클릭합니다.
3. 작업 완료 후 페이지 하단의 **Artifacts** 섹션에 있는 **`QRMaster-Debug-APK`** 를 클릭하여 다운로드합니다.
4. 압축을 풀면 스마트폰에 즉시 설치 가능한 `app-debug.apk` 파일이 들어있습니다.

---

## 🛠 기술 스택
- **Language**: Java 17
- **Target SDK**: 34 (Android 14) / **Min SDK**: 24 (Android 7.0+)
- **Build System**: Gradle 8.5, Android Gradle Plugin 8.3.2
- **CI/CD**: GitHub Actions (Ubuntu Latest runner)
