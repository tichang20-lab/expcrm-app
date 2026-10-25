# 체험관관리프로그램 설치 안내 페이지

- 페이지: https://tichang20-lab.github.io/expcrm-app/
- 설치 파일(항상 최신): https://github.com/tichang20-lab/expcrm-app/releases/latest/download/expcrm.apk

원본은 앱 프로젝트(experience-center-crm, v2-server 브랜치)의 `landing/` 폴더에 있고, 이 저장소에는 그 내용만 올린다.

## 새 APK를 올리는 법

1. EAS로 빌드한다: `npx eas-cli@latest build -p android --profile preview`
2. 빌드 화면에서 APK를 받아 파일 이름을 `expcrm.apk`로 바꾼다.
3. 새 릴리스를 만든다: `gh release create v2.0-build3 expcrm.apk --repo tichang20-lab/expcrm-app --title "v2.0 (빌드 3)" --latest`

페이지의 버튼은 항상 "가장 최근 릴리스"의 `expcrm.apk`를 받으므로, 페이지나 이미 보낸 링크는 바꿀 필요가 없다.

## PC(웹) 버전을 올리는 법

- 주소: https://tichang20-lab.github.io/expcrm-app/web/
- 앱 코드를 고친 뒤 앱 프로젝트에서 `powershell -ExecutionPolicy Bypass -File scripts/deploy-web.ps1` 실행.
  웹으로 빌드해 이 저장소의 `web/`을 바꾸고, `404.html`(하위 주소 새로 고침용)과 안내 페이지도 함께 올린다.
- 휴대폰 APK와 같은 코드에서 올려야 화면이 같다. 새 APK를 릴리스할 때 함께 실행하는 것을 권장.

## 새 버전 안내(앱 안 알림)

`scripts/release-android.ps1 -ApkUrl <EAS APK 주소> -Build <빌드 번호> -Notes "바뀐 점"`을 쓰면
릴리스를 만들고 서버 설정 `android_latest_build`도 올려서, 그보다 낮은 빌드의 앱에 "새 버전이 있습니다"가 뜬다(빌드 6부터).
