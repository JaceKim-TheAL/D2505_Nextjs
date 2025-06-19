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
- [웹사이트 vs 웹애플리케이션](#웹사이트-vs-웹애플리케이션)
- [CRUD 조작](#crud-조작)

---
### NextJS 개발준비

- 공식사이트 : https://nodejs.org/
- 설치파일다운 : [Node.js® 다운로드](https://nodejs.org/ko/download)
- 버전 : `LTS` 안정적인 버전, `CURRENT` 최신버전   cf. LTS 버전 권고
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
<br/>

[[TOP]](#index)

---