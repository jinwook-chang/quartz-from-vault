# Quartz from Vault

`vault` 폴더에 Obsidian Markdown 파일을 넣으면 Quartz 정적 사이트로 빌드됩니다.

## 사용법

```bash
npm install
npm run build
```

빌드 결과는 `public` 폴더에 생성됩니다.

로컬에서 확인하려면:

```bash
npm run dev
```

기본 주소는 `http://localhost:8080`입니다.

## 폴더

- `vault/`: Obsidian Markdown 노트
- `public/`: 빌드된 정적 사이트
- `quartz.config.ts`: 사이트 설정
- `quartz.layout.ts`: 페이지 레이아웃과 graph/search/explorer 구성
