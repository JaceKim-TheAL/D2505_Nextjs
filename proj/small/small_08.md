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
    <td><b href="small_08.md">8.F아이템   </b></td>
    <td><a href="small_09.md">9.FE배포    </a></td>
    <td><a href="small_10.md">10.브러시업  </a></td>
  </tr>
</table>

---
# S08. 아이템 페이지
- [전체 아이템 데이터를 읽는 페이지](#전체-아이템-데이터를-읽는-페이지)
- [1개 아이템 데이터를 읽는 페이지](#1개-아이템-데이터를-읽는-페이지)
- [아이템 데이터 작성 페이지](#아이템-데이터-작성-페이지)
- [아이템 데이터 수정 페이지](#아이템-데이터-수정-페이지)
- [아이템 데이터 삭제 페이지](#아이템-데이터-삭제-페이지)
- [페이지 표시를 제어하기](#페이지-표시를-제어하기)
- [스타일 적용과 공통 컴포넌트](#스타일-적용과-공통-컴포넌트)

---
### 전체 아이템 데이터를 읽는 페이지

[app/page.js]
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
- 이 코드에서는 데이터를 게시하는 것이 아니라 얻어야 하므로, 게시할 데이터를 넣는 body나 header는 설저할 필요가 없다.
- method 또한 fetch()가 아니라 데이터를 얻는 GET 요청이 기본이기 때문에 method: "GET"과 같이 평시할 필요가 없다. 
- 얻은 데이터를 포함하고 있는 response의 내용을 확일할 것이므로 console.log를 기술
- `URL` http://localhost:3000 을 열고, 개발자 도구의 `Console`을 확인
  - 모든 아이템 데이터를 얻을 수 있고, 얻은 데이터는 jsonData에 들어 있다
  - 클라이언트가 아닌 서버 컴포넌트이기 때문에 console.log() 실행결과는 브라우저의 `Console`에는 표시되지 않고 터미널에서만 표시된다는 점
<br/>

[[TOP]](#index)

---
### 1개 아이템 데이터를 읽는 페이지

백엔드를 개발할 때와 마찬가지로 특수한 폴더명인 [id]를 사용한다 <br/>
<br/>

[app/item/readsingle/[id]/page.js]
```js
import Image from "next/image"  
import Link from "next/link" 

const getSingleItem = async(id) => {
    const response = await fetch(`${process.env.NEXT_PUBLIC_URL}/api/item/readsingle/${id}`, {cache: "no-store"})
    const jsonData = await response.json() 
    const singleItem = jsonData.singleItem
    return singleItem 
}  

const ReadSingleItem = async(context) => {
    const singleItem = await getSingleItem(context.params.id)
    return (
        <div className="grid-container-si">
            <title>{singleItem.title}</title>     
            <meta name="description" content={singleItem.description}/>
            <div>
                <Image src={singleItem.image} width={750} height={500} alt="item-image" priority/>
            </div>
            <div>
                <h1>{singleItem.title}</h1>
                <h2>¥{singleItem.price}</h2>
                <hr/>
                <p>{singleItem.description}</p>
                <div>
                    <Link href={`/item/update/${singleItem._id}`}>아이템 수정</Link>
                    <Link href={`/item/delete/${singleItem._id}`}>아이템 삭제</Link>
                </div>
            </div>
        </div>
    )
}

export default ReadSingleItem
```
- 고정된 폴더명을 사용하면 아이템 수만큼 폴더가 늘어나 효율이 떨어지므로, <br/>
  백엔드와 마찬가지로 범용적인 템플릿 폴더를 만들고 거기에 개별 아이템 데이터를 전달해 표시
- 접속한 프론트엔드 URL에서 끝의 문자열을 얻어 fetch()를 사용해 백엔드의 URL에 붙이면 필요한 아이템 데이터를 얻을 수 있다. 
- URL 끝의 데이터는 Next.js에서 사용하는 특별한 코드인 context의 내부, params의 id이다. 
- `URL` http://localhost:3000/item/readsingle/ 뒤에 무작위 문자열을 추가하고 브라우즈 오픈
- URL의 끝은 context.params.id 로 얻을 수 있음
- 코드상에서 getSingleItem에 전달하고, 전달된 context.params.id를 받을 것이므로 id를 괄호안에 추가
- 문자열을 작성하는 큰따옴표(" ") 또는 작은따옴프(' ') 안에 JavaScript의 코드는 기술할수 없다.
  - 따라서 여기서 사용하는 것은 백틱(backtick)과 같은 ${ }이다.
  - URL 전체를 백틱으로 싸고 아래와 같이 기술
    - `fetch(http://localhost:3000/api/item/readsingle/${id})`
<br/>

[[TOP]](#index)

---
### 아이템 데이터 작성 페이지

<br/>

[app/item/readsingle/[id]/page.js]
```js

```
<br/>

[[TOP]](#index)

---
### 아이템 데이터 수정 페이지

<br/>

[[TOP]](#index)

---
### 아이템 데이터 삭제 페이지

<br/>

[[TOP]](#index)

---
### 페이지 표시를 제어하기

<br/>

[[TOP]](#index)

---
### 스타일 적용과 공통 컴포넌트

<br/>

[[TOP]](#index)

---
