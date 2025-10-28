# Salesmap Deal History Viewer

브라우저에서 바로 [Salesmap Deal History API](https://docs.salesmap.kr/developers/api-reference/deal/history)를 호출하고 응답을 확인할 수 있는 단일 HTML 페이지입니다. `index.html`이 메인 도구 페이지이며, 기존에 공유되었던 `deal-history.html` 경로로 접속해도 자동으로 메인 페이지로 이동합니다.

## 필요 조건

- 세일즈맵 Open API 토큰 (딜 히스토리 조회 권한 필수)
- 정적 파일을 제공할 수 있는 아무 웹 서버 (예: Python `http.server`, Node `serve` 등)

## 로컬에서 실행하기

1. 이 저장소를 클론하거나 ZIP으로 내려받습니다.
2. 프로젝트 루트에서 정적 서버를 실행합니다. 예를 들어 Python이 설치되어 있다면 다음 명령으로 가능합니다.
   ```bash
   python3 -m http.server 4173
   ```
3. 브라우저에서 `http://localhost:4173/` 주소를 열어 메인 페이지에 접속합니다.
4. API 토큰과 딜 ID를 입력하고 조회 버튼을 누르면 v2 Deal History 엔드포인트를 호출하여 결과를 확인할 수 있습니다.

## 배포하기

정적 파일 하나만 배포하면 되므로 어느 정적 호스팅 플랫폼이든 사용 가능합니다. 아래는 몇 가지 예시입니다.

### GitHub Pages

1. 저장소를 GitHub에 푸시합니다.
2. **Settings → Pages**에서 소스 브랜치(예: `main`)와 디렉터리(`/(root)`)를 선택합니다.
3. 배포가 완료되면 `https://<username>.github.io/<repo>/` 로 접속하면 곧바로 도구 페이지가 열립니다. (기존 주소인 `.../deal-history.html`로 접근해도 자동으로 루트 페이지로 이동합니다.)

### Netlify 등 기타 정적 호스팅

1. Netlify에 새 사이트를 만들고 저장소를 연결하거나, 저장소를 ZIP으로 업로드합니다.
2. 빌드 명령은 필요 없으므로 비워두거나 `none`으로 설정하고, 배포 디렉터리는 저장소 루트(`/`)로 지정합니다.
3. 배포 후 제공된 주소로 접속합니다.

### 직접 호스팅 / 기타 CDN

AWS S3, CloudFront, Nginx, Vercel 등 원하는 인프라에 `index.html` 파일을 업로드하여 제공합니다. 브라우저가 세일즈맵 API에 안전하게 접근할 수 있도록 반드시 HTTPS로 서비스하세요.

## 보안 참고사항

- API 토큰과 커서는 브라우저 `localStorage`에만 저장되며 서버로 전송되지 않습니다.
- 도메인을 신뢰할 수 있는 곳에 배포하고, 공용 PC에서는 사용 후 로컬 스토리지를 비우는 것이 좋습니다.
