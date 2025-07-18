[nextjs15]: readme.md
[![적용기술](https://skillicons.dev/icons?i=pr,nextjs,ts,react,vercel)][nextjs15]
 
### INDEX

<table>
  <tr>
    <td><b href="small_01.md">1.개발도구   </b></td>
    <td><a href="small_02.md">2.BE준비    </a></td>
    <td><a href="small_03.md">3.B아이템   </a></td>
    <td><a href="small_04.md">4.B사용자   </a></td>
    <td><a href="small_05.md">5.BE배포    </a></td>
    <td><a href="small_06.md">6.FE준비    </a></td>
    <td><a href="small_07.md">7.F사용자   </a></td>
    <td><a href="small_08.md">8.F아이템   </a></td>
    <td><a href="small_09.md">9.FE배포    </a></td>
    <td><a href="small_10.md">10.브러시업  </a></td>
  </tr>
</table>

---
# S01. 개발도구준비
- [NextJS 개발준비](#nextjs-개발준비)
- [VS Code 설치](#vs-code-설치)
- [Thunder Client 익스텐션 설치](#thunder-client-익스텐션-설치)
- [웹사이트 vs 웹애플리케이션](#웹사이트-vs-웹애플리케이션)
- [CRUD 조작](#crud-조작)

---
### NextJS 개발준비

- 공식사이트 : https://nodejs.org/
- 설치파일다운 : [Node.js® 다운로드](https://nodejs.org/ko/download)
- 버전 : `LTS` 안정적인 버전, `CURRENT` 최신버전  <br/>
  🥰 cf. 참고로 `LTS 버전` 설치하기를 권고
- npm : Node Package Manager
- 다운받은 설치파일을 실행하면, Node.js와 npm 모두 설치가 된다.
- 버전 확인
```powershell
# Docker는 각 운영 체제별로 설치 지침을 제공합니다.
# 공식 문서는 https://docker.com/get-started/에서 확인하세요.

# Node.js Docker 이미지를 풀(Pull)하세요:
docker pull node:22-alpine

# Node.js 컨테이너를 생성하고 쉘 세션을 시작하세요:
docker run -it --rm --entrypoint sh node:22-alpine

# Node.js 버전 확인:
node -v # "v22.16.0"가 출력되어야 합니다.

npm 버전 확인:
npm -v # 10.9.2가 출력되어야 합니다.

```

```powershell
PS C:\GitHub\practice\nextjs> node -v
v22.14.0
PS C:\GitHub\practice\nextjs> npm -v
10.9.2
PS C:\GitHub\practice\nextjs>

```
<br/>

[[TOP]](#index)

---
### VS Code 설치

- 웹 애플리케이션 개발에서 가장 많이 사용되는 에디터
- 다운로드 : https://code.visualstudio.com/download
<br/>

### Thunder Client 익스텐션 설치
- Thunder Client : VSCode에서 사용할 수 있는 가볍고 직관적인 REST API 테스트 도구 <br/>
- [[사용법]](https://inpa.tistory.com/entry/VS-Code-%F0%9F%92%BD-Thunder-Client-Postman-%EB%8C%80%EC%8B%A0-%EC%9D%B4%EA%B1%B0-%EC%93%B0%EC%9E%90) <br/>

- 요청 등록 <br/>
1️⃣ 설치 후 좌측 사이드바에 번개 아이콘이 생김. 클릭하면 Thunder Client가 열린다. <br/>
2️⃣ 상단의 `New Request` 버튼 클릭 <br/>
3️⃣ 요청할 API의 Method(GET, POST 등), URL, Query, Headers, Body 등을 입력 <br/>
4️⃣ `Send` 버튼을 누르면 응답 결과가 하단에 표시된다. <br/>

- 테스트 목록  <br/>
▶️ Collections 기능 <br/>
▶️ 프로젝트마다 사용하는 API 목록이 다른데 이때 콜렉션을 활용하면 프로젝마다 API 목록을 정리해 놓을 수 있어서 좋다.  <br/>

- 환경 변수 <br/>
▶️ 중복적으로 사용되는 값들을 환경변수로 설정할 수 있다. <br/>
▶️ 상단 Env를 누르고  New Environment를 선택하면 프로젝트마다 환경변수를 적용할 수 있다. <br/>
▶️ 프로젝트에서 사용하는 변수들을 여기에 등록해두면 된다. 
<br/>

[[TOP]](#index)

---
### 웹사이트 vs 웹애플리케이션

|            | 웹 사이트 | 웹 애플리케이션 |
|------------|----------|--------------|
| 정보의 흐름 | 한방향     | 양방향        |
| 구성 요소   | 프론트엔드(HTML/CSS)     | 프론트엔드(HTML/CSS/JavaScrit) + 백엔드 | 
| 예시       | 기업, 음식점의 홈페이지 등 | 중고거래플랫폼, 리뷰서비스 등 |
<br/>

[[TOP]](#index)

---
### CRUD 조작

| HTTP 메서드 | 조작   | CRUD |
|------------|:-----:|---------|
| GET        | 읽기 | `R`ead   | 
| POST       | 작성 | `C`reate | 
| PUT        | 수정 | `U`pdate | 
| DELETE     | 삭제 | `D`elete | 
<br/>

[[TOP]](#index)

---