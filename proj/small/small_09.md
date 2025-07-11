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

🚀 React와 Next.js의 긴밀한 관계 <br/>
- Next.js 버전 13에서 도입된 app 폴더 안에는 서버 컴포넌트가 기본값으 되어 있다.
- 하지만 현재 React의 최신 버전인 버전 18에서는 서버 컴포넌트는 아직 실험 단계로만 제공되고 있으며, 다음 버전인 React 19부터 본격적으로 제공된다. 
- 본가에서는 채용되지 않은 기술이  `React 프레임워크` 인 Next.js에는 기본값으로 되어 있는 이유는 무엇일까?
  - 사실 최근 React 개발팀과 Next.js 개발사인 Vercel은 매우 가까운 협업 관계에 있으며, 
  - React 개발팀의 많은 멤버가 Vercel로 이동하고 있다. 
  - 본가인 React에서는 아직 안정 버전이 아닌 기능이 Next.js에 먼저 도입되는 이유가 여기에 있다.
  - 이러한 결과로 Vercel 및 React 개발팀은 서버 컴포넌트를 포함하는 다양한 새로운 기술이 운영환경에서 사용되었을 때의 실전 데이터를 수집하고, 그것을 React 개발에 피드백으로 제공할 수 있다. 
  - 한편 실험적인 기능을 기본으로 제공하는 Next.js의 태도에 불만을 느끼는 엔지니어도 적지 않은것으로 보인다.


<br/>

[[TOP]](#index)

---
