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
| 장점 | API를 다른 애플리케이션 및 모바일 애플리케이션에서도 사용 가능 | 
        코드양을 줄이고 짧은 시간이 컴팩트하게 개발 가능    |
| 단점 | 코드 양과 개발 공정이 늘어남       | Next.js에서만 사용할 수 있음    |



<br/>

[[TOP]](#index)

---