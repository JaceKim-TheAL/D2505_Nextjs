[nextjs15]: readme.md
[![적용기술](https://skillicons.dev/icons?i=pr,nextjs,ts,react,vercel)][nextjs15]
 
### INDEX

<table>
  <tr>
    <td><a href="small_01.md">1.개발도구   </a></td>
    <td><a href="small_02.md">2.BE준비    </a></td>
    <td><b href="small_03.md">3.B아이템   </b></td>
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
# S03. 아이템 조작기능 
- [아이템 작성1](#아이템-작성1) : 백엔드 작업을 위한 기초작업
- [아이템 작성2](#아이템-작성2) : 데이터베이스를 설정하고 Next.js를 연결해 데이터를 저장
- []

---
### 아이템 작성1
> 백엔드 작업을 위한 기초작업을 한다.

- 템플릿 코드 작성

[app/api/item/create/route.js]
```js
import { NextResponse } from 'next/server';

export async function GET(request) {
  return NextResponse.json({ message: '아이템 작성' });
}
```

확인 : 
http://localhost:3000/api/item/create

```json
{
  "message": "아이템 작성"
}
```

- Thunder Client 에서 아이템 작성
> 아이템 작성을 위해서는 데이터를 받는 단계가 필요
> 데이터는 실제로는 프론트엔드에서 전달되지만 개발단계에서 Thunder Client를 사용
<br/>

[app/api/item/create/route.js]
```js
import { NextResponse } from 'next/server';

export async function GET(request) {
  return NextResponse.json({ message: '아이템 작성 (GET)' })
}

export async function POST(request) {
  console.log(await request.json) 
  return NextResponse.json({ message: '아이템 작성 (POST)' })
}
```
- URL에 어떤 메소드(GET,POST)로 `Send` 하느냐에 따라서, route.js에서 export 되는 함수가 다르다. <br/>
  Response에서 확인!!
- 응답이 NextResponse 인 이유는 Next.js에서만 사용할 수 있는 특별한 코드이기 때문
- request엣 Thunder Client에서 보낸 JSON 데이터가 들어 있을 것이므로, console.log()를 사용해서 확인
- 이를 통해 백엔드에서 데이터를 받는 방법을 알았고, 이후 데이터베이스인 MongoDB 설정과 접속후 데이터 저장을 구현

![이미지](./images/s03_tc_request_get.png)

![이미지](./images/s03_tc_request_post.png)

![이미지](./images/s03_tc_request_json_content.png)

<br/>

[[TOP]](#index)

---
### 아이템 작성2
> 데이터베이스를 설정하고 Next.js를 연결해 데이터를 저장한다. 

<br/>

[[TOP]](#index)

---
