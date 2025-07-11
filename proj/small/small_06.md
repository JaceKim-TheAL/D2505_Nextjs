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
      <button style="background-color: #4CAF50; color: white; padding: 10px 20px; border: none; border-radius: 5px;">
        [Send]
      </button>
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
    <td></td>
  </tr>
</table>


<button style="background-color: #4CAF50; color: white; padding: 10px 20px; border: none; border-radius: 5px;">
  전송
</button>

<br/>

[[TOP]](#index)

---
### 코드 정리

불필요한 코드를 삭제
  - 먼저 app 폴더 안에 있는 page.module.css를 파일마다 삭제
  - 다음으로 globals.css 파일을 열고, 안의 내용을 모두 삭제
  - app 폴더의 page.js 파일을 열고 안의 내용을 모두 삭제

<br/>

[[TOP]](#index)

---
### React 작성 방법 및 스타일 적용 방법

[app/page.js]
```js
const ReadAllItems = () => {
  return (
    <div>
      <h1 className="h1-style">넥스트샵에 오신걸 환영합니다! ^^</h1>
      <h2 style={{ marginTop: '10px', marginBottom: '20px'}}>다양한 상품을 준비하겠습니다.</h2>
      <h3 style={{ color: 'blue', letterSpacing: '5px' }}>안녕히 가세요!!</h3>
    </div>
  );
}

export default ReadAllItems;
```

[app/globals.css]
```css
.....

body {
  background: var(--background);
  color: var(--foreground);
  font-family: Arial, Helvetica, sans-serif;
}

.h1-style {
  color: red;
  letter-spacing: 5px;
}

```


`URL` http://localhost:3000/


- HTML에서는 <head> 부분에 globals.css 파일을 임포트 하여야 하지만, Next.js에서는 이런 코드가 안보임!
```html
<link rel="stylesheet" href="./globals.css">
```

- app 폴더의 layout.js를 열어보면 globals.css 파일이 임포트되어 있음을 확인할 수 있다. 
```js
import "./globals.css";

```


<br/>

[[TOP]](#index)

---
### 서버 컴포넌트

서버 컴포넌트와 클리이언트 컴포넌트 비교
| 조작 | 서버 컴포넌트 | 클라이언트 컴포넌트 |
|:----|:-----------:|:----------------:|
| useState, useEffect 사용  |  X  |  O  |
| onClick 등 사용자 조작 기능 |  X  |  O  |
| 백엔드 리소스에 직접 접근    |  O  |  X  |

- React는 일반적으로 클라이언트 측의 기술로 인식되어 있다. 
- React와 그 주변 기술들이 개발됨에 따라 서버 측에서의 동작이 가능하다. 
- React 서버 컴포넌트의 장점은 높은 성능 특성이다.  <br/>
  애플리케이션에서 사용도는 대량의 JavaScript를 브라우저(클라이언트)가 아니라 성능이 뛰어난 서버 측에서 처리함으로써 애플리케이션 크기를 작게 억제하면서, 읽기 속도가 낮아지는 것을 방지할 수 있다.

- Next.js에서 기본값이 된 서버컴포넌트의 사용구분
  - 서버 컴포넌트에서는 useState, useEffect를 사용할 수 없다. 
  - 사용자 조작 관련 기능(onClick, onChange 등)도 사용할 수 없다. 
  - 이를 사용하려면 파일의 첫번째 행에 "use client"라고 기술해야 한다. 

```js
"use client"

import { useState } from "react"

const Contact = () => {
  const [data, setData] = useState("")
  return(
    <div>
    .......
    </div>
  )
}
```

<br/>

🚨 서버 컴포넌트와 클라이언트 컴포넌트는 함께 사용할 수 있을까? <br/>
- Next.js의 app 폴더 안에 만드는 React 컴포넌트는 자동으로 서버 컴포넌트가 된다.
- 그렇다면 "use client"를 붙인 컴포넌트, 즉 클라이언트에서 서버 컴포넌트를 import 해서 사용할 수 있을까?
  - 대답은 가능은 하지만 다소 보수적인 형태이다.
  - 클라이언트 컴포넌트 안에 임포트한 자식 컴포넌트는 모두 자동으로 클라이언트 컴포넌트가 되기 때문
  - 그 결과 서버 컴포넌트의 강점인 데이터베이스 연결 등의 조작을 수행할 수 없게 된다. 
  - Next.js 공식사이트에서도 서버 컴포넌트를 클라이언트 컴포넌트에 임포하는 것은 지원하지 않는 사용방법(Unsupported Pattern)이라고 설명하고 있다. 
  - 대신 권장되는 방법은 **props, children 형태로 클라이언트 컴포넌트를 전달**하는 방법이다. <br/>
    이 방법을 사용하면 클라이언트 컴포넌트화 하지 않고, 서버 컴포넌트 기능을 유지할 수 있다.
<br/>

🚀 React 서버 컴포넌트를 사용해 데이터 얻기 <br/>
- 데이터 조작에 관한 기능들(읽기/생성/수정/삭제)를 백엔드와 프론트엔드 양쪽에서 확실하게 개발하는 방법으로 진행
- React의 새로운 기능인 서버 컴포넌트를 사용하면 데이터 읽기를 수행할 때 API 서버를 경유하지 않고 데이터베이스에 직접 접근해서 실행할 수 있다. 

[page.js]
```js
import Link from "next/link"
import Image from "next/image"

const getAllItems = async() => {
    const response = await fetch(`${process.env.NEXT_PUBLIC_URL}/api/item/readall`, {cache: "no-store"})
    const jsonData = await response.json()
    const allItems = jsonData.allItems
    return allItems
}

const ReadAllItems = async() => {
    const allItems = await getAllItems()
    return (
        <div className="grid-container-in">
            <title>NextMarket</title>     
            <meta name="description" content="NextMarketです"/>
            {allItems.map(item => 
                <Link href={`/item/readsingle/${item._id}`} key={item._id}>
                    <Image src={item.image} width={750} height={500} alt="item-image" priority/>
                    <div key={item._id}> 
                        <h2>¥{item.price}</h2>
                        <h3>{item.title}</h3>
                        <p>{item.description.substring(0, 80)}...</p>  
                    </div>
                </Link>
            )}
        </div>
    )
} 

export default ReadAllItems
```

- getAllItems 로 API 서버에 접근해 모든 아이템 데이터를 얻는것을 알 수 있다. 
- 하지만 React 서버 컴포넌트에서는 데이터를 얻을 때 데이터베이스에 직접 접근할 수 있으므로 getAllItems 안을 다음과 같이 치환할 수 있다. 

[page.js]
```js
import Link from "next/link"
import Image from "next/image"
import connectDB from "../app/utils/database"           // 추가
import { ItemModel } from "../app/utils/schemaModels"   // 추가

const getAllItems = async() => {
    // 변경↓
    await connectDB()
    const allItems = await ItemModel.find()
    // 변경↑

    return allItems
}

const ReadAllItems = async() => {
    const allItems = await getAllItems()
    return (
        <div className="grid-container-in">
            <title>NextMarket</title>     
            <meta name="description" content="NextMarketです"/>
            {allItems.map(item => 
                <Link href={`/item/readsingle/${item._id}`} key={item._id}>
                    <Image src={item.image} width={750} height={500} alt="item-image" priority/>
                    <div key={item._id}> 
                        <h2>¥{item.price}</h2>
                        <h3>{item.title}</h3>
                        <p>{item.description.substring(0, 80)}...</p>  
                    </div>
                </Link>
            )}
        </div>
    )
} 

export default ReadAllItems
```
- getAllItems 안의 코드는 백엔드 쪽의 /app/api/item/readall/route.js에 기술되어 있는 모든 아이템 데이터를 얻는 코드와 기본적으로 같다는 것을 알 수 있다. 


<br/>

[[TOP]](#index)

---
