[main]: https://github.com/JaceKim-TheAL/D2505_Nextjs
[![적용기술](https://skillicons.dev/icons?i=nextjs,ts,react,vercel)][main]

# Next.js 웹페이지 구현 방법

### Step1. 프로젝트 설정
- Shell/Terminal에서 다음 명령어를 실행

```shell
npx create-next-app my-next-app
```

- 명령어는 Next.js 프로젝트를 자동으로 설정하고 필요한 패키지를 설치

```shell
PS C:\github\practice\nextjs> npx -v
10.9.2
PS C:\github\practice\nextjs> npx create-next-app jaceapp
√ Would you like to use TypeScript? ... No / Yes
√ Would you like to use ESLint? ... No / Yes
√ Would you like to use Tailwind CSS? ... No / Yes
√ Would you like your code inside a `src/` directory? ... No / Yes
√ Would you like to use App Router? (recommended) ... No / Yes
√ Would you like to use Turbopack for `next dev`? ... No / Yes
√ Would you like to customize the import alias (`@/*` by default)? ... No / Yes
Creating a new Next.js app in C:\GitHub\practice\nextjs\jaceapp.

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


added 62 packages, and audited 63 packages in 16s

10 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
Initialized a git repository.

Success! Created jaceapp at C:\GitHub\practice\nextjs\jaceapp

PS C:\github\practice\nextjs>
```
<br/>

### Step2. 개발 서버 실행
- 설치가 완료되면 프로젝트 폴더로 이동한 후 개발 서버를 시작

```shell
npm run dev
```

- 브라우저 `http://localhost:3000` 에서 기본 웹페이지를 확인
<br/>

### Step3. 페이지 추가
- Next.js에서는 `pages/` 폴더에 새로운 파일을 만들면 자동으로 경로가 생성됩니다. 
- 예를 들어, `pages/about.js`를 만들고 다음 코드를 추가하면 `/about` 페이지가 생성됩니다.

```jsx
export default function About() {
  return <h1>About Page</h1>;
}
```
<br/>

### Step4. 스타일 추가
- 스타일링을 위해 `styles/globals.css`를 수정하거나 `styled-components` 또는 `Tailwind CSS`를 사용할 수도 있다.
<br/>

### Stpe5. 데이터 가져오기 (API 요청)
- Next.js는 getServerSideProps 또는 getStaticProps를 사용해 데이터를 가져올 수 있어요.
- 예제

```jsx
export async function getServerSideProps() {
  const res = await fetch('https://api.example.com/data');
  const data = await res.json();
  
  return { props: { data } };
}
```
<br/>

### Step6. 배포
- 웹페이지를 배포하려면 Vercel 같은 서비스를 사용하면 간편하다.

```shell
npx vercel
```

- 이렇게 하면 자동으로 배포되고, <br/>
  기본적인 웹페이지가 완성!! 😃 

<br/>


