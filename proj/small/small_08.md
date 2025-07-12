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
- 백엔드에서 받은 response에 들어 있는 데이터는 JSON으로 변환해야 한다.
  - 변환 작업은 데이터를 모두 얻은 뒤 수행해야 하므로 await와 async를 코드에 추가
  - 얻은 데이터를 확인하기 위해 console.log()도 추가
    - `console.log(jsonData.singleItem)`
- 각 아이템 데이터를 브라우저에서 표시
  - async, await, 캐시를 저장하지 않도록 하는 코드도 fetch()안에 추
```js
const getSingleItem = async(id) => {
    const response = await fetch(`${process.env.NEXT_PUBLIC_URL}/api/item/readsingle/${id}`, {cache: "no-store"})    // 추가
    const jsonData = await response.json() 
    console.log(jsonData.singleItem)    // 삭제
    const singleItem = jsonData.singleItem    // 추가
    return singleItem     // 추가
}  

const ReadSingleItem = async(context) => {    // 추가
    const singleItem = await getSingleItem(context.params.id)    // 추가
    console.log(singleItem)    // 추가
    return(
      ..................
```

- 브라우저에서 데이터를 표시
  - 작업은 각 아이템으로 분할하는 map()이 없는 것을 제외하고 /app/page.js 와 거의 같다.
  - Next.js의 <Image>를 임포트해서 사용
<br/>

[[TOP]](#index)

---
### 아이템 데이터 작성 페이지

데이터 게시 기능을 개발한 뒤 Local Storage와 연동하는 기능 추가
<br/>

[app/item/create/page.js]
```js
"use client"
import { useState } from "react"
import { useRouter } from "next/navigation" 
import useAuth from "../../utils/useAuth"
import ImgInput from "../../components/imgInput"

const CreateItem = () => {
    const [title, setTitle] = useState("")
    const [price, setPrice] = useState("")
    const [image, setImage] = useState("")
    const [description, setDescription] = useState("")

    const router = useRouter()
    const loginUserEmail = useAuth() 

    const handleSubmit = async(e) => {
        e.preventDefault() 
        try{
            const response = await fetch(`${process.env.NEXT_PUBLIC_URL}/api/item/create`, {
                method: "POST",
                headers: { 
                    "Accept": "application/json", 
                    "Content-Type": "application/json",
                    "Authorization": `Bearer ${localStorage.getItem("token")}`
                },
                body: JSON.stringify({
                    title: title,
                    price: price,
                    image: image,
                    description: description,
                    email: loginUserEmail  
                })
            })
            const jsonData = await response.json()
            alert(jsonData.message)  
            router.push("/") 
            router.refresh()
        }catch{
            alert("아이템 작성 실패") 
        }
    }

    if(loginUserEmail){
        return (
            <div>
                <title>작성 페이지</title>     
                <meta name="description" content="작성 페이지입니다."/>
                <h1 className="page-title">아이템 작성</h1>
                <ImgInput setImage={setImage}/>
                <form onSubmit={handleSubmit}>
                    <input value={title} onChange={(e) => setTitle(e.target.value)} type="text" name="title" placeholder="아이템명" required/>
                    <input value={price} onChange={(e) => setPrice(e.target.value)} type="text" name="price" placeholder="가격" required/>
                    <input value={image} onChange={(e) => setImage(e.target.value)} type="text" name="image" placeholder="이미지" required/>
                    <textarea value={description} onChange={(e) => setDescription(e.target.value)} name="description" rows={15} placeholder="상품 설명" required></textarea>
                    <button>작성</button>
                </form>
            </div>
        )
    }  
}

export default CreateItem
```
- 이 컴포넌트는 클라이언트 컴포넌트로 사용할 것이므로 첫번째 줄에 "use client"를 기술
- 아이템 데이터를 입력받는 각 항목을 만든다
- 입력된 각 항목의 데이터를 보관하는 state를 만든다
- <input>과 <textarea>에 입력된 데이터를 각 state에 보관
- 다음은 데이터 송신 처리를 수행하는 handleSubmit을 만들고 <form>과 연결
- 실패했을 때의 처리를 기술하기 위한 try catch, 데이터 캐시를 위한 fetch()도 추가
- 아이템 데이터 게시 대상은 백엔드 http://localhost:3000/api/item/create 이므로 fetch()에 기술
  - 데이터 송신 관련 설정은 headers에 기술하고, 보낼 데이터는 body에 넣는다
  - 데이터는 JSON 형식으로 보낼것이므로 JSON.stringify()를 잊지 않도록한다
- 백엔드 데이터에는 title, price 같은 항목뿐만 아니라 email도 있음
  - 이 email 데이터는 후반에 만들 `사용자 로그인 기능을 프론토엔드 측에서 판정하는 파일(useAuth.hs)` 에서 얻는다.  
  - 여기서는 우선 email 항목을 만들고 아래와 같이 기술
    - email: "더미 데이터"    // 추가  
- 아이템 작성이 성공하면 alert()를 표시한 뒤, 홈페이지로 이동
  - Next.js에서 제공하는 next/navigation을 사용
- 마지막으로 처리 완료를 기다리는 await와 async, 브라우저의 새로 고침을 방지하는 preventDefault()를 기술
- 이 아이템 작성 페이지가 툭수한 점은, 로그인한 사용자 아이템을 작성할 수 있다는 점때문이다. 
  - 아이템 작성, 편집 및 삭제 요청은 middleware.js를 통과하여 유효한 토큰이 있는지 확인  
  - 그렇기 때문에 이 아이템 게시 페이지에서 백엔드로 데이터를 보낼때는 토큰도 함께 보내야 한다.
- 아이템 작성 성공이라는 알람이 뜨고 홈페이지로 이동했다면, MongoDB를 열어보고 확인

![미들웨어_적용범위제한](./images/s08_middleware_role.png)
<br/>

[/middleware.js]
```js
import { NextResponse } from "next/server"
import { jwtVerify } from "jose" 

export async function middleware(request){
    const token = await request.headers.get("Authorization")?.split(" ")[1]

    if(!token){
        return NextResponse.json({message: "토큰 없음"})
    }

    try{
        const secretKey = new TextEncoder().encode("next-market-app-book") 
        const decodedJwt = await jwtVerify(token, secretKey) 
        return NextResponse.next()
    }catch{
        return NextResponse.json({message: "토큰이 올바르지 않으므로 로그인하십시오"})
    }
}

export const config = {
    matcher: ["/api/item/create", "/api/item/update/:path*", "/api/item/delete/:path*"],
}
```

<br/>



[[TOP]](#index)

---
### 아이템 데이터 수정 페이지

<br/>

[app/item/update/[id]/page.js]
```js

```
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
