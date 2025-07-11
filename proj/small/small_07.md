[nextjs15]: readme.md
[![적용기술](https://skillicons.dev/icons?i=pr,nextjs,ts,react,vercel)][nextjs15]
 
### INDEX

<table>
  <tr>
    <td><a href="small_01.md">1.개발도구   </a></td>
    <td><a href="small_02.md">2.BE준비    </a></td>
    <td><a href="small_03.md">3.B아이템   </a></td>
    <td><a href="small_04.md">4.B사용자   </a></td>
    <td><a href="small_05.md">5.BE배포    </a></td>
    <td><a href="small_06.md">6.FE준비    </a></td>
    <td><b href="small_07.md">7.F사용자   </b></td>
    <td><a href="small_08.md">8.F아이템   </a></td>
    <td><a href="small_09.md">9.FE배포    </a></td>
    <td><a href="small_10.md">10.브러시업  </a></td>
  </tr>
</table>

---
# S07. 사용자등록 및 로그인
- [필수 폴더 및 파일](#필수-폴더-및-파일)
- [사용자 등록 페이지](#사용자-등록-페이지)
- [로그인 페이지](#로그인-페이지)

---
### 필수 폴더 및 파일

- 백엔드를 개발할 때 본 것처럼 app 폴더 안에서는 폴더명이 URL로 사용되며 코드는 그 안에 만든 route.js 파일에 작성했다. 
- 이것은 프론트엔드에서도 기본적으로 같다. 
- 한가지 차이는 파일명으로 route.js가 아니라 page.js를 사용하는 것이다. 
<br/>

[app/register/page.js]
```js
const Register = () => {
  return (
    <div>
      <h1>사용자 등록</h1>
    </div>
  );
}

export default Register;
```

`URL` http://localhost:3000/register


- app 안의 폴더명이 URL로 사요오디고, 코드는 그 안에 만든 page.js에 기술할 수 있는 것을 확인
- user 폴더(사용자관련)와 itemp 폴더(아이템관련)를 aap 폴더안에 만든다
  - register 폴더는 사용자 관련 페이지이므로, user 폴더로 이동한다.
  - item 폴더 안에 create, read, update, delete 폴더를 만들고 그 안에 page.js 파일을 작성 

<br/>

[[TOP]](#index)

---
### 사용자 등록 페이지

<br/>

[[TOP]](#index)

---
### 로그인 페이지

<br/>

[[TOP]](#index)

---
