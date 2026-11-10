# 든든 정적 웹

[든든(nutri-kids-project)](https://github.com/cora1022/nutri-kids-project)을 서버 없이 운영하기 위한 정적 웹 버전입니다. 화면은 원본 프로젝트의 `frontend/`와 같고, GitHub Pages로 배포합니다.

[든든 사용해보기](https://cora1022.github.io/static-nutri/)

## 원본 프로젝트와 다른 점

- 상품 검색은 `public/data/foods.json`에 내보낸 상품 목록에서 찾습니다. 검색 조건과 정렬은 원본 서버와 같습니다.
- 한 끼 분석은 `src/services/nutritionEngine.ts`가 브라우저에서 계산합니다. 원본의 `backend/app/services/nutrition/engine.py`를 그대로 옮겼고, 운영 API 응답과 같은 값이 나오는지 테스트로 확인합니다.
- 구글 로그인 버튼은 화면에 남아 있지만 누르면 지원하지 않는다는 안내만 보여 줍니다. 모든 이용자는 게스트로 이용하고 기록은 브라우저에 저장됩니다.

## 실행 방법

```bash
npm install
npm run dev
```

## 상품 데이터 갱신

원본 API가 살아 있을 때 다음 명령으로 상품 목록을 다시 내려받습니다. 다른 주소의 API를 쓰려면 `node scripts/export-foods.mjs <API 주소>`로 실행합니다.

```bash
npm run export:foods
```

## 검증과 배포

```bash
npm run lint
npm run typecheck
npm test
npm run build
```

`main`에 푸시하면 `.github/workflows/deploy.yml`이 같은 검사를 실행하고 GitHub Pages에 배포합니다. 빌드는 상대 경로를 쓰므로 하위 경로나 사용자 도메인에서 그대로 동작합니다.
