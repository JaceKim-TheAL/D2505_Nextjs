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
- [Next.js 업데이트](#nextjs-15의-주요-업데이트-내용) 
- [Next.js 소개](#nextjs란)
- [설치 및 구성](#설치-및-구성)  
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


### Next.js 15의 주요 업데이트 내용

<br/>

[[TOP]](#index)

---
