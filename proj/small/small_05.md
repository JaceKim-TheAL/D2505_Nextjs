[nextjs15]: readme.md
[![적용기술](https://skillicons.dev/icons?i=pr,nextjs,ts,react,vercel)][nextjs15]
 
### INDEX

<table>
  <tr>
    <td><a href="small_01.md">1.개발도구   </a></td>
    <td><a href="small_02.md">2.BE준비    </a></td>
    <td><a href="small_03.md">3.B아이템   </a></td>
    <td><a href="small_04.md">4.B사용자   </a></td>
    <td><b href="small_05.md">5.BE배포    </b></td>
    <td><a href="small_06.md">6.FE준비    </a></td>
    <td><a href="small_07.md">7.F사용자   </a></td>
    <td><a href="small_08.md">8.F아이템   </a></td>
    <td><a href="small_09.md">9.FE배포    </a></td>
    <td><a href="small_10.md">10.브러시업  </a></td>
  </tr>
</table>

---
# S05. 백엔드 배포 
- [Vercel을 이용한 배포 순서](#vercel을-이용한-배포-순서)
- [기본 배포 절차](#기본-배포-절차)
- [CLI를 통한 배포](#cli를-통한-배포)

---
### Vercel을 이용한 배포 순서
> Vercel은 Next.js의 개발사이기 때문에 Next.js 애플리케이션과 호환성이 높고 원활한 연동을 제공한다. <br/>
> Git에 코드를 푸시하고 Vercel에서 배포 작업을 수행해 백엔드를 온라인에 공개한다. <br/>

- URL에서 Vercel에 접속 : 
- URL : [Vercel](https://vercel.com/)
<br/>

[대시보드 화면] 
- 코드를 푸시한 저장소를 찾아 `Import` 버튼을 클릭한다.
<br/>

[배포설정 화면]
- 특별한 설정은 필요하지 않으므로, 아래쪽으로 스크롤한 뒤 `Deploy` 버튼을 클릭한다.
<br/>

[더 알아보기]
### API 와 Server Actions, 무엇을 사용할 것인가?
- Next.js 버전 14부터 안정 버전이 된 새로운 기능인 `Server Actions`를 사용하면 데이터베이스에 직접 CRUD 조작을 할 수 있다.
- Server Actions를 사용하면 백엔드 API를 개발할 필요가 없다.
- API와 Server Actions는 경쟁 관계에 있지 않으며, 2가지를 동시에 사용할 수도 있다.
- 애플리케이션에 따라 가장 적합한 것을 선택하는 것이 중요하다.

[API와 SErver Actions 비교]
|     | API(Route Handlers) | Server Actions |
|-----|---------------------|----------------|
| 특징 | 범용성               | 한정적          |
| 용도 | DB와의 복잡한 연동 조작을 하는 경우 | 단순한 CRUD 조작을 주로 하는 경우 |
| 장점 | API를 다른 애플리케이션 및 모바일 애플리케이션에서도 사용 가능 | 코드양을 줄이고 짧은 시간이 컴팩트하게 개발 가능    |
| 단점 | 코드 양과 개발 공정이 늘어남       | Next.js에서만 사용할 수 있음    |

<br/>

[[TOP]](#index)

---
### 기본 배포 절차

1️⃣ Vercel 가입 및 로그인 <br/>
- Vercel 공식 사이트에 접속 후 GitHub 계정으로 로그인

2️⃣ 프로젝트 가져오기 <br/>
- 대시보드에서 Add New > Project 클릭
- 연동된 Git 저장소에서 배포할 프로젝트 선택 후 Import

3️⃣ 설정 확인 <br/>
- Vercel이 자동으로 프레임워크, 빌드 명령어, 출력 디렉토리를 감지
- 필요 시 환경 변수 추가 가능

4️⃣ 배포 실행 <br/>
- Deploy 버튼 클릭 → 자동으로 빌드 및 배포 진행
- 배포 완료 후 *.vercel.app 도메인이 생성됨

<br/>

[[TOP]](#index)

---
### CLI를 통한 배포

1️⃣ Node.js 설치 후 다음 명령어 실행: <br/>
```shell
npm install -g vercel
```

2️⃣ 프로젝트 폴더에서: <br/>
```shell
vercel
```

3️⃣ 질문에 따라 설정 진행 → 배포 완료 시 URL 제공 <br/>
<br/>

💡 팁 <br/>
- Git에 push만 해도 자동으로 재배포됨 (CI/CD)
- `vercel.json` 파일로 라우팅 설정 가능 (SPA에서 404 방지)
- 커스텀 도메인 연결도 지원
<br/>

🚀 참조 튜토리얼 : 
- [블로그](https://velog.io/@lovelys0731/Vercel%EB%A1%9C-React-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EB%A5%BC-%EB%B0%B0%ED%8F%AC%ED%95%B4-%EB%B3%B4%EC%9E%90-1-Vercel-%EB%B0%B0%ED%8F%AC-%EA%B8%B0%EB%B3%B8)
- [가이드](https://blog.naver.com/macolombe/223895606848)

<br/>

[[TOP]](#index)

---
