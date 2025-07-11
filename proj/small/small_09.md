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
    <td><a href="small_07.md">7.F사용자   </a></td>
    <td><a href="small_08.md">8.F아이템   </a></td>
    <td><b href="small_09.md">9.FE배포    </b></td>
    <td><a href="small_10.md">10.브러시업  </a></td>
  </tr>
</table>

---
# S09. 프런트엔드 배포
- [백엔드 URL 수정(환경 변수 설정)](#백엔드-url-수정환경-변수-설정)

---
### 백엔드 URL 수정(환경 변수 설정)

환경 변수를 설정한 뒤 프론트엔드를 온라인에 공개한다. 

- 수작업으로 각 파일의 URL을 변경하는 방법도 있지만, 환경 변수를 사용한다.
  - .env.development 와 .env.production 이라는 파일을 폴더의 최상위 계층에 만든다.
  - .으로 시작하는 특수한 파일명을 사용하는 점에 주의
  - development는 `개발환경`, 즉 로컬PC 환경을 나타내고
  - production은 `운영환경`, 즉 Vercel 환경 등을 의미
  - 각 파일에는 개발 환경에서 사용하는 URL과 Vercel에서 사용하는 URL을 기

[app/.env.development]
```shell
NEXT_PUBLIC_URL=http://localhost:3000
```

[app/.env.production]
```shell
NEXT_PUBLIC_URL=https://nextjs-book-fullstack-app-folder-v2.vercel.app
```
<br/>

[[TOP]](#index)

---
