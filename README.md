# React BoilerPlate

- typescript v4.9.5
- vite v4.1.4
  - vite-tsconfig-paths 를 이용한 절대 경로 설정
- React v18.2.0
  - - react-router-dom
  - emotion
    - react
    - styled
- storybook v6.5.16
- prettier
- eslint

## scripts

- `dev`: 개발 서버를 돌릴 수 있음
- `build`: 배포용 빌드 파일을 만듬
- `preview`: 배포용 빌드 파일을 미리 봄
- `storybook`: 스토리북 개발 서버 실행
- `build-storybook`: 배포용 스토리북 빌드 파일 생성

## settings

- emotion 설정
  - `src/styles/theme` 에서 테마 코드 설정 (`src/dtypes/emotion.d.ts`)
    - 테마 설정을 하지 않을 것이라면 코드 삭제도 좋음
    - Theme Type과 코드 설정 바람 (디자인 색상 설정 필요)
  - `src/styles/GlobalStyle` 에서 initial css 설정
- `index.html` 파일에서 title, favicon 등의 설정
- `public/manifest.json` 파일에서 title, description, logo 등의 설정
- `package.json` 파일에서 title, description 등의 설정

## publics

`/public` 폴더 아래에 static assets를 넣고 index.html에서 제공한다.

## eslint

### installed packages

- `eslint` : 코드의 문법을 검사하는 린팅과 코드의 스타일을 잡아주는 포맷팅 기능
- `prettier` : 코드의 스타일을 잡아주는 포맷팅 기능
- `@typescript-eslint/eslint-plugin` : Typescript 관련 린팅규칙을 설정하는 플러그인
- `@typescript-eslint/parser` : Typescript 를 파싱하기 위해 사용
- `eslint-config-prettier` : prettier와 충돌을 일으키는 ESLint 규칙들을 비활성화 시키는 config
- `eslint-plugin-prettier` : Prettier에서 인식하는 코드상의 포맷 오류를 ESLint 오류로 출력
- `eslint-plugin-react` : React에 관한 린트설정을 지원
- `eslint-plugin-react-hooks` : React Hooks의 규칙을 강제하도록 하는 플러그인
- `eslint-plugin-jsx-a11y` : JSX 내의 접근성 문제에 대해 즉각적인 AST 린팅 피드백을 제공
- `eslint-plugin-import` : ES2015+의 import/export 구문을 지원하도록 함

```json
{
  "import/order": [
    "error",
    {
      // 각 그룹별로 모듈 순서를 정의
      "groups": ["builtin", "external", "parent"],
      // pathGroups: import 경로를 정규식으로 정의하여 그룹화
      "pathGroups": [
        {
          // pattern: 해당 패턴에 해당하는 모듈을 그룹화
          "pattern": "react*",
          // group: 그룹의 이름을 지정
          "group": "builtin",
          // position: 그룹의 위치를 지정 (해당 그룹에 앞, 뒤를 지정)
          "position": "before"
        },
        {
          "pattern": "@emotion/*",
          "group": "external"
        }
      ],
      // pathGroupsExcludedImportTypes: 구성된 pathGroup에서 처리하지 않는 가져오기 유형을 정의
      "pathGroupsExcludedImportTypes": ["builtin"],
      // alphabetize: import를 알파벳 순서로 정렬
      "alphabetize": {
        // order: 알파벳 순서를 지정 (asc: 오름차순, desc: 내림차순)
        "order": "asc",
        // caseInsensitive: 대소문자 무시 여부
        "caseInsensitive": true
      },
      "newlines-between": "never"
    }
  ]
}
```

## Storybook

### vite 설정

- Storybook은 기본적으로 cra를 기반으로 동작하여 webpack을 사용
- 따라서 vite에 대한 설정이 필요

```bash
npx storybook init
npm install @storybook/builder-vite --save-dev
```

```js
module.exports = {
  stories: [
    '../stories/**/*.stories.mdx',
    '../stories/**/*.stories.@(js|jsx|ts|tsx)',
  ],
  addons: ['@storybook/addon-links', '@storybook/addon-essentials'],
  core: {
    builder: '@storybook/builder-vite', // 👈 The builder enabled here.
  },
};
```

### addon 설정

[링크](https://velog.io/@velopert/start-storybook)
