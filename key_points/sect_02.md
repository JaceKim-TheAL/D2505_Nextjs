[nextjs15]: https://nextjs-ko.org/docs/
[![적용기술](https://skillicons.dev/icons?i=nextjs,ts,react)][nextjs15]  
 
### INDEX

<table>
  <tr>
    <td><a href="sect_01.md">개요        </a></td>
    <td><b href="sect_02.md">라우팅      </b></td>
    <td><a href="sect_03.md">라우팅 패턴  </a></td>
    <td><a href="sect_04.md">인증        </a></td>
    <td><a href="sect_05.md">서버 액션   </a></td>
    <td><a href="sect_06.md">최적화      </a></td>
    <td><a href="sect_07.md">배포        </a></td>  
  </tr>
</table>

---
# 2. 라우팅
- [페이지](#페이지)
- [레이아웃](#레이아웃)
- [컴포넌트 방식의 탐색](#컴포넌트-방식의-탐색)

<br/>

---
라우팅 기능을 사용하기 위해선 Next.js의 파일 규칙(File Conventions)을 이해해야 합니다. <br/>
기본 파일은 아래 표에서 layout부터 순서대로 계층 구조를 나타내며, 각 페이지를 출력하기 위해 기능에 맞게 사용합니다. <br/>
이러한 명시적 파일 규칙을 통해, 프로젝트 구조를 명확하게 유지할 수 있습니다. <br/>

![컴포넌트 계층구조](./images/s02_hierarchy.jpg)

##### 명시적 컴포넌트 계층 구조(Component Hierarchy)

<table>
    <thead>
        <tr>
            <th>기본 파일</th>
            <th>확장자</th>
            <th>설명</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>error</code></td>
            <td><code>.js</code>, <code>.jsx</code>, <code>.tsx</code></td>
            <td>에러 페이지</td>
        </tr>
        <tr>
            <td><code>layout</code></td>
            <td><code>.js</code>, <code>.jsx</code>, <code>.tsx</code></td>
            <td>고정 레이아웃</td>
        </tr>
        <tr>
            <td><code>loading</code></td>
            <td><code>.js</code>, <code>.jsx</code>, <code>.tsx</code></td>
            <td>로딩 페이지</td>
        </tr>
        <tr>
            <td><code>not-found</code></td>
            <td><code>.js</code>, <code>.jsx</code>, <code>.tsx</code></td>
            <td>찾을 수 없는(404) 페이지</td>
        </tr>
        <tr>
            <td><code>page</code></td>
            <td><code>.js</code>, <code>.jsx</code>, <code>.tsx</code></td>
            <td>기본 페이지</td>
        </tr>
        <tr>
            <td><code>template</code></td>
            <td><code>.js</code>, <code>.jsx</code>, <code>.tsx</code></td>
            <td>변화 레이아웃(탐색 시)</td>
        </tr>
    </tbody>
</table>

<table>
    <thead>
        <tr>
            <th>추가 파일</th>
            <th>설명</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>default</code></td>
            <td><code>.js</code>, <code>.jsx</code>, <code>.tsx</code></td>
        </tr>
        <tr>
            <td><code>global-error</code></td>
            <td><code>.js</code>, <code>.jsx</code>, <code>.tsx</code></td>
        </tr>
        <tr>
            <td><code>route</code></td>
            <td><code>.js</code>, <code>.ts</code></td>
        </tr>
    </tbody>
</table>


### 페이지
Next.js는 폴더를 사용해 경로를 정의하는 파일 시스템 기반 라우터 방식을 사용하기 때문에, /app 폴더 내에 생성하는 각 폴더는 기본적으로 URL 경로를 의미합니다. <br/>
예를 들어, 프로젝트에 /app/movies 폴더를 생성하면 /movies 경로 즉, http://localhost:3000/movies로 접근할 수 있습니다. <br/>
그리고 접근한 그 경로에서 출력할 내용은 기본적으로 각 폴더의 page.tsx 컴포넌트에 작성합니다. <br/>
 <br/>
이렇게 매핑되는 각 경로 구간을 세그먼트(Segment)라고 합니다. <br/>

세그먼트의 이해 
![세그먼트](./images/s02_segment.jpg)
<br/>

프로젝트 구조
```shell
├─app/
│  ├─movies/
│  │  └─page.tsx
│  └─page.tsx
```
<br/>


http://localhost:3000/ 경로의 페이지 내용
```tsx
[/app/page.tsx]

export default function Home() {
  return <h1>Home page!</h1>
}
```
<br/>

http://localhost:3000/movies 경로의 페이지 내용
```tsx
[/app/movies/page.tsx]

export default function Movies() {
  return (
    <>
      <h1>Movies page!</h1>
      <ul>
        <li>Avengers</li>
        <li>Avatar</li>
        <li>Frozen</li>
      </ul>
    </>
  )
}
```
<br/>

또한 위에서 살펴본 라우팅 파일 규칙에 해당하는 이름이 아닌 파일은, 경로로 정의되지 않기 때문에 같은 폴더 안에서 자유롭게 추가해 사용할 수 있습니다.<br/>
다음 이미지에서 `page.js`, `route.js` 파일을 제외한 나머지 파일은 경로로 정의되지 않습니다.(Not Routable)<br/>

라우팅 파일과 폴더 공유(Colocation)
![세그먼트](./images/s02_page_route.jpg)
<br/>

[[TOP]](#index)

---
### 레이아웃

여러 하위 경로에서 공통으로 사용하는 UI는, 각 라우팅 폴더의 layout.tsx 컴포넌트에 작성합니다.<br/>
슬롯(Slot) 방식으로 children Prop을 사용하며, {children} 부분에는 같은 레벨에 있는 page.tsx 컴포넌트를 출력합니다.<br/>
또한 레이아웃은 중첩해서 사용할 수 있습니다.<br/>

프로젝트 구조
```shell
├─app/
│  ├─movies/
│  │  ├─layout.tsx
│  │  └─page.tsx
│  ├─layout.tsx
│  └─page.tsx
├─components/
│  └─Header.tsx
```

<br/>

다음 코드의 {children} 부분에는 /app/page.tsx 컴포넌트가 출력됩니다.<br/>

http://localhost:3000/ 경로의 레이아웃 
```tsx
[/app/layout.tsxTSX]

import './globals.css'
import Header from '@/components/Header'

export default function RootLayout({
  children
}: Readonly<{
  children: React.ReactNode
}>) {
  return (
    <html lang="ko">
      <body className="antialiased">
        <Header />
        <main className="p-2">{children}</main>
      </body>
    </html>
  )
}
```
<br/>

다음 코드의 {children} 부분에는 /app/movies/page.tsx 컴포넌트가 출력됩니다.<br/>
<br/>

http://localhost:3000/movies 경로의 레이아웃
```tsx
[/app/movies/layout.tsx]

export default function MoviesLayout({
  children
}: Readonly<{ children: React.ReactNode }>) {
  return <section>{children}</section>
}
```

<br/>

[[TOP]](#index)

---
### 컴포넌트 방식의 탐색



<br/>

[[TOP]](#index)

---