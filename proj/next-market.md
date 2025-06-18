# Proejct : Next-Market


### 프로젝트(Next-Market) 생성

npx create-next-app 프로젝트명

```shell
PS C:\GitHub\practice\nextjs> npx create-next-app next-market
√ Would you like to use TypeScript? ... No / Yes
√ Would you like to use ESLint? ... No / Yes
√ Would you like to use Tailwind CSS? ... No / Yes
√ Would you like your code inside a `src/` directory? ... No / Yes
√ Would you like to use App Router? (recommended) ... No / Yes
√ Would you like to use Turbopack for `next dev`? ... No / Yes
√ Would you like to customize the import alias (`@/*` by default)? ... No / Yes
Creating a new Next.js app in C:\GitHub\practice\nextjs\next-market.

Using npm.

Initializing project with template: app-tw


Installing dependencies:
- react
- react-dom
- next

Installing devDependencies:
- typescript
- @types/node
- @types/react
- @types/react-dom
- @tailwindcss/postcss
- tailwindcss


added 62 packages, and audited 63 packages in 15s

10 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
Initialized a git repository.

Success! Created next-market at C:\GitHub\practice\nextjs\next-market

npm notice
npm notice New major version of npm available! 10.9.2 -> 11.4.2
npm notice Changelog: https://github.com/npm/cli/releases/tag/v11.4.2
npm notice To update run: npm install -g npm@11.4.2
npm notice
PS C:\GitHub\practice\nextjs>
PS C:\GitHub\practice\nextjs> cd .\next-market\
PS C:\GitHub\practice\nextjs\next-market> ls


    디렉터리: C:\GitHub\practice\nextjs\next-market


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-06-18   오후 2:21                app
d-----      2025-06-18   오후 2:21                node_modules
d-----      2025-06-18   오후 2:21                public
-a----      2025-06-09   오후 3:20            480 .gitignore
-a----      2025-06-09   오후 3:20            211 next-env.d.ts
-a----      2025-06-09   오후 3:20            133 next.config.ts
-a----      2025-06-18   오후 2:21          58476 package-lock.json
-a----      2025-06-18   오후 2:21            495 package.json
-a----      2025-06-09   오후 3:20             81 postcss.config.mjs
-a----      2025-06-09   오후 3:20           1450 README.md
-a----      2025-06-18   오후 2:21            598 tsconfig.json


PS C:\GitHub\practice\nextjs\next-market>
```

- app : 대부분의 앱개발이 이루어지는 폴더
- node_modules : 설치된 패키지가 저장
- public : 정적 파일이 위치한 장소로 이미지 등을 여기에 배치



### 앱서버 구동

프로젝트 폴더에서 `npm run dev` 로 앱서버 스타트

```shell
PS C:\GitHub\practice\nextjs\next-market> npm run dev

> next-market@0.1.0 dev
> next dev --turbopack

   ▲ Next.js 15.3.3 (Turbopack)
   - Local:        http://localhost:3000
   - Network:      http://192.168.54.82:3000

 ✓ Starting...
 ```


### 백엔드 폴더의 동작

app/api 폴더안에 새폴더를 만들고 route.js 파일을 생성

[app/api/hello/route.js]
```js
import {NextResponse} from 'next/server';
export async function GET(request) {
  const {searchParams} = new URL(request.url);
  const name = searchParams.get('name') || 'World';

  return NextResponse.json({message: `안녕하세요, ${name}님!`});
}
```

확인 : 
http://localhost:3000/api/hello?name=Jace

```json
{
  "message": "안녕하세요, Jace님!"
}
```


### Tip. app 폴더와 pages 폴더 구성의 차이

- app 폴더 도입 이전(Next.js 버전12까지) 사용되던 것이 pages 폴더 <br/>
 👉🏽 pages 폴더에서 백엔드 API를 개발할 때는 폴더명을 api로 지정해야 했음. <br/>
 👉🏽 app 폴더에서는 route.js 파일을 app 폴더 안에 만들면, 해당 폴더명이 URL로 매핑되어 백엔드 코드로 기능함 <br/>
     ∴ api폴더 만들필요 없음

- 폴더 구성 

| URL | app 폴더 | pages 폴더 |
|-----|---------|-----------|
| /api/hello   | /app/api/hello/route.js   | /pages/api/hello.js   |
| /api/goodbuy | /app/api/goodbye/route.js | /pages/api/goodbye.js |


### 필요한 폴더와 파일 작성

- 백엔드 개발을 시작하기 위한 기초 작업
- 아이템관리(item폴더)와 사용자관리(user폴더) 생성
- 작성/수정/삭제 등의 처리를 담당하는 파일
> - /app/api/item/create/route.js 
> - /app/api/item/update/route.js 
> - /app/api/item/delete/route.js 
- 조회 처리를 담당하는 파일
> - /app/api/item/readsingle/route.js 
> - /app/api/item/readall/route.js 

