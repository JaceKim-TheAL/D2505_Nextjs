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
- [아이템 작성1](#아이템-작성1)
- []
- []
- []
- []
- []

---
### 아이템 작성1


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

<br/>

[[TOP]](#index)

---
