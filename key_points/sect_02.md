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

![세그먼트](./images/s02_segment.jpg)
<br/>

- 세그먼트의 이해

프로젝트 구조
```shell
├─app/
│  ├─movies/
│  │  └─page.tsx
│  └─page.tsx
```

/app/page.tsx

```tsx
export default function Home() {
  return <h1>Home page!</h1>
}
```
http://localhost:3000/ 경로의 페이지 내용



<br/>

[[TOP]](#index)

---
