# PDF 합치기

PDF 두 개를 브라우저 안에서 하나로 합치는 정적 웹앱입니다. 파일은 서버로 업로드되지 않고 방문자의 브라우저에서만 처리됩니다.

## 기능

- PDF 두 개를 끌어다 놓거나 선택해서 올리기 (두 파일을 한 번에 끌어다 놓아도 됨)
- 첫 쪽 미리보기, 쪽수, 용량 표시
- 순서 바꾸기, 합친 결과의 쪽 범위 확인
- 저장할 파일 이름 지정 후 다운로드
- 실제 파일 없이 써 볼 수 있는 예시 파일 버튼

암호가 걸린 PDF는 합칠 수 없습니다.

## GitHub Pages에 배포하기

1. GitHub에서 새 저장소를 만듭니다 (예: `pdf-merge`).
2. 이 폴더의 파일을 모두 저장소 루트에 올립니다. `index.html`이 루트에 있어야 합니다.
   - 웹에서 올릴 때: 저장소 페이지 → **Add file → Upload files** → 압축을 푼 파일과 `lib` 폴더를 끌어다 놓고 커밋
   - 명령줄로 올릴 때:
     ```bash
     git init
     git add .
     git commit -m "PDF 합치기"
     git branch -M main
     git remote add origin https://github.com/<사용자명>/pdf-merge.git
     git push -u origin main
     ```
3. 저장소 **Settings → Pages**에서 **Source**를 `Deploy from a branch`로, 브랜치를 `main` / `/(root)`로 정하고 저장합니다.
4. 1–2분 뒤 `https://<사용자명>.github.io/pdf-merge/`에서 열립니다.

## 파일 구성

```
index.html              앱 전체 (HTML, CSS, JS)
lib/pdf-lib.min.js      PDF 합치기 (pdf-lib 1.17.1, MIT)
lib/pdf.min.js          미리보기 렌더링 (PDF.js 3.11.174, Apache-2.0)
lib/pdf.worker.min.js   PDF.js 워커
lib/LICENSE-*           라이브러리 라이선스
.nojekyll               GitHub Pages의 Jekyll 처리 끄기
```

라이브러리를 `lib/`에 함께 넣어 두어 외부 CDN 없이 동작합니다. 글꼴(IBM Plex Sans KR)만 Google Fonts에서 불러오며, 불러오지 못하면 시스템 글꼴로 표시됩니다.

## 로컬에서 실행

`index.html`을 바로 열면 미리보기 워커가 막힐 수 있으니 간단한 서버로 여세요.

```bash
python3 -m http.server 8000
# http://localhost:8000 접속
```
