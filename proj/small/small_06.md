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
    <td><b href="small_06.md">6.FE준비    </b></td>
    <td><a href="small_07.md">7.F사용자   </a></td>
    <td><a href="small_08.md">8.F아이템   </a></td>
    <td><a href="small_09.md">9.FE배포    </a></td>
    <td><a href="small_10.md">10.브러시업  </a></td>
  </tr>
</table>

---
# S06. 프론트엔드 개발준비
- [아이템 데이터 저장](#아이템-데이터-저장)
- [코드 정리](#코드-정리)
- [React 작성 방법 및 스타일 적용 방법](#react-작성-방법-및-스타일-적용-방법)
- [서버 컴포넌트](#서버-컴포넌트)

---
### 아이템 데이터 저장

- 더미 아이템 데이터6개를 MongoDB에 저장
- Next.js 실행 명령어를 터미널에 입력하고 `Enter`키를 눌러 실행
```shell
% npm run dev
```

- Thunder Client를 열고 HTTP 메서드와 URL 설정
<table>
  <tr>
    <td>New Request</td>
    <td>[POST] http://localhost:3000/api/user/register </td>
    <td>
      <button type="button">Send</button>
    </td>
  </tr>
  <tr>
    <td>JSON Content</td>
    <td>
<pre>
{
  "name" : "Jace",
  "email" : "jacekim@gmail.com",
  "password" : "admin123"
}
</pre>
    </td>
    <td>
      <button style="background-color: #4CAF50; color: white; padding: 10px 20px; border: none; border-radius: 5px;">
        Send
      </button>
    </td>
  </tr>
</table>


<button style="background-color: #4CAF50; color: white; padding: 10px 20px; border: none; border-radius: 5px;">
  전송
</button>

<br/>

[[TOP]](#index)

---
### 코드 정리

<br/>

[[TOP]](#index)

---
### React 작성 방법 및 스타일 적용 방법

<br/>

[[TOP]](#index)

---
### 서버 컴포넌트

<br/>

[[TOP]](#index)

---
