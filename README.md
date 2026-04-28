# Quartz from Vault

`vault` 폴더에 Obsidian Markdown 파일을 넣으면 [Quartz](https://quartz.jzhao.xyz/) 기반 정적 사이트로 빌드되는 프로젝트입니다.

Markdown 문서 조회, 폴더 탐색, 검색, backlinks, graph view를 사용할 수 있습니다.

## Requirements

- Node.js 22+
- npm 10.9.2+

## Setup

```bash
npm install
```

## Add Notes

Obsidian vault의 Markdown 파일을 `vault` 폴더 안에 넣습니다.

```text
vault/
  index.md
  Books/
    Example.md
  Concepts/
    Another Note.md
```

홈 화면을 만들려면 `vault/index.md`를 두는 것을 권장합니다.

```md
# My Vault

- [[Books/Example]]
- [[Concepts/Another Note]]
```

Obsidian wiki link(`[[노트 이름]]`)는 Quartz가 자동으로 링크와 graph로 변환합니다.

## Local Preview

```bash
npm run dev
```

브라우저에서 아래 주소를 엽니다.

```text
http://localhost:8080
```

`npm run dev`가 켜져 있는 동안에는 `vault` 안의 `.md` 파일을 추가하거나 수정하면 자동으로 다시 빌드됩니다.

다른 포트로 실행해야 한다면 `--port`를 지정합니다.

```bash
npm run quartz -- build --serve --watch -d vault -o public --port 9090
```

같은 네트워크의 다른 기기에서는 아래처럼 접속할 수 있습니다.

```text
http://YOUR_LOCAL_IP:9090
```

## Build Static Site

```bash
npm run build
```

빌드 결과는 `public` 폴더에 생성됩니다. 이 폴더는 배포용 정적 파일이며 Git에는 포함하지 않습니다.

## GitHub Update

프로젝트 설정이나 README를 수정한 뒤 GitHub에 반영하려면:

```bash
git status
git add README.md package.json quartz.config.ts quartz.layout.ts vault/.gitkeep
git commit -m "Update project"
git push
```

새 Markdown 노트까지 GitHub에 올리고 싶다면 `vault` 안의 파일도 함께 add 합니다.

```bash
git add vault
git commit -m "Add vault notes"
git push
```

## Project Structure

- `vault/`: Obsidian Markdown 노트
- `public/`: 빌드된 정적 사이트
- `quartz.config.ts`: 사이트 설정
- `quartz.layout.ts`: 페이지 레이아웃과 graph/search/explorer 구성
- `quartz/`: Quartz 본체

## Useful Commands

```bash
npm run dev      # localhost:8080에서 미리보기
npm run build    # public 폴더에 정적 사이트 생성
npm run check    # TypeScript/Prettier 검사
```
