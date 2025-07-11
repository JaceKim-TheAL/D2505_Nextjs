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
    <td><b href="small_10.md">10.브러시업  </b></td>
  </tr>
</table>

---
# S10. 브러시업
- [이미지 업로드 기능 개발](#이미지-업로드-기능-개발)
- [로딩](#로딩)
- [메타 데이터 설정 방법](#메타-데이터-설정-방법)
- [이후의 학습에 관해](#이후의-학습에-관해)

---
### 이미지 업로드 기능 개발

이미지 업로드 기능을 앱에 추가하여 사용자가 원하는 이미지를 저장 할 수 있다. 

- 앞에서 개발한 애플리케이션의 아이템 사진에는 public 폴더의 이미지를 사용했다.
- 하지만 여기서에서는 사용자가 원하는 사진을 애플리케이션에 표시하게 할 수 없으므로, 클라우드 서비스인 Cloudinary를 사용해 애플리케이션에 이미지 업로드 기능을 추가한다.
- 먼저 Cloudinary에 사용자 등록을 한다. 
- `URL` https://cloudinary.com/ 
<br/>

![cloudinary등록](./images/s10_cloudianry_start.png)

![cloudinary키](./images/s10_cloudianry_key.png)

```js
    // Configuration
    cloudinary.config({ 
        cloud_name: 'duelol9lx', 
        api_key: '183283821252485', 
        api_secret: '<your_api_secret>' // Click 'View API Keys' above to copy your API secret
    });

```


[[TOP]](#index)

---
### 로딩

<br/>

[[TOP]](#index)

---
### 메타 데이터 설정 방법

<br/>

[[TOP]](#index)

---
### 이후의 학습에 관해

<br/>

[[TOP]](#index)

---
