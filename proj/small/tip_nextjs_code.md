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
    <td><a href="small_09.md">9.FE배포    </a></td>
    <td><a href="small_10.md">10.브러시업  </a></td>
  </tr>
</table>

---
# Next.js Code
- [import 방법](#import-방법)

---
### import 방법
자바스크립트에서 2가지(default import 와 named import) 있음 <br/>
Next.js는 JavaScript 기반이기 때문에 그대로 따른다. <br/>

🔍 차이점 정리 <br/>
| 구문 형태 | 설명 | 예시 | 
|----------|-----|-----| 
| import Something from 'module' | 👉 default export를 가져올 때 사용. <br/> 모듈에서 기본으로 하나만 내보내는 항목. | import React from 'react' | 
| import { Something } from 'module' | 👉 named export를 가져올 때 사용. <br/> 모듈에서 이름이 지정된 여러 항목 중 하나를 선택해서 가져옴. | import { useState } from 'react' | 
<br/>

🛠 예시로 이해 <br/>
- 모듈 정의
```js
// utils.js
export default function greet() {
  return "Hello!";
}

export function add(a, b) {
  return a + b;
}
```
<br/>

- 모듈 호출
```js
import greet from './utils';       // ✅ default export
import { add } from './utils';     // ✅ named export
```
<br/>

🎯 추가 팁
- default export는 이름을 자유롭게 정해서 import 가능해.
- named export는 반드시 export된 이름 그대로 써야 해.
<br/>
