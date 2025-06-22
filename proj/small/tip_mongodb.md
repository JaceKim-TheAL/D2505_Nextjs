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
# Mongo DB 
- [MongoDB란?](#mongodb란)
- [핵심 개념](#mongodb의-핵심-개념)
- [주요 특징](#mongodb의-주요-특징)
- [사용 예시 (CRUD)](#사용-예시-crud)
- [어디에 쓰이나요?](#️어디에-쓰이나요)
- [MongoDB의 유형](#mongodb의-유형)
- [MongoDB 드라이버 연결](#mongodb-드라이버-연결)
---
### MongoDB란?
MongoDB는 전통적인 RDBMS와는 다른 방식으로 데이터는 저장하는 **NoSQL 데이터베이스** 
<br/>
🌐 공식사이트 : [[MongoDB Atlas]](https://www.mongodb.com/ko-kr/docs/manual/)
<br/>

### 🧠MongoDB의 핵심 개념
- Document: JSON과 유사한 BSON(Binary JSON) 형식으로 저장되는 데이터 단위
- Collection: 여러 Document를 담는 그릇, RDB의 테이블과 비슷
- Database: 여러 Collection을 포함하는 상위 개념

### 💡MongoDB의 주요 특징
- 스키마 유연성: 미리 정해진 구조 없이 다양한 형태의 데이터를 저장 가능
- 확장성: 수평 확장이 쉬워서 대용량 데이터 처리에 유리
- 빠른 읽기/쓰기 성능: 특히 읽기 속도가 빠르고, 인덱스를 다양하게 지원
- 분산 시스템 지원: Replica Set, Sharding 등으로 고가용성과 확장성 확보

### 🔧사용 예시 (CRUD) 
```javascript
// Create
db.users.insertOne({ name: "Jace", age: 28 });

// Read
db.users.find({ age: { $gt: 20 } });

// Update
db.users.updateOne({ name: "Jace" }, { $set: { age: 29 } });

// Delete
db.users.deleteOne({ name: "Jace" });
```

### ⚓️어디에 쓰이나요?
- 실시간 분석 시스템
- IoT 데이터 저장
- 사용자 프로필, 게시글, 채팅 로그 등 유연한 구조가 필요한 서비스


### ☁️MongoDB의 유형

<table>
  <tr>
    <td>MongoDB</td>
    <td>
      로컬 환경, 즉 로컬 PC안에 데이터를 저장
    </td>
  </tr>
  <tr>
    <td>MongoDB Atlas</td>
    <td>
      클라우드, 즉 온라인에 데이터를 저장
    </td>
  </tr>
</table>

<!--
 ☁️ MongoDB 설치형 (On-Premise 또는 자체 서버) 
| 항목 | 설명 | 
|-----|-----| 
| 설치 및 운영 | 사용자가 직접 설치, 구성, 유지보수 필요 | 
| 유연성 | 서버, 설정, 보안 등 모든 것을 직접 제어 가능 | 
| 비용 | 서버 비용, 인프라 유지비, 인건비 발생 | 
| 확장성 | 수동 확장 필요 (샤딩, 클러스터 구성 등) | 
| 보안 | 직접 구성해야 하며, 실수 시 취약점 발생 가능 | 
| 백업/복구 | 직접 스크립트 작성 또는 외부 도구 사용 필요 | 
| 적합한 경우 | 고도의 커스터마이징이 필요한 환경, 내부망 전용 시스템 등 | 

☁️ MongoDB Atlas (클라우드 관리형 서비스)
| 항목 | 설명 | 
|-----|-----| 
| 설치 및 운영 | MongoDB에서 자동으로 관리 (배포, 패치, 모니터링 등) | 
| 유연성 | 설정은 제한적이지만 대부분의 기능은 UI로 쉽게 조작 가능 | 
| 비용 | 사용량 기반 과금 (무료 플랜도 존재) | 
| 확장성 | 버튼 클릭만으로 수평/수직 확장 가능 | 
| 보안 | 기본적으로 TLS, IP 화이트리스트, 암호화 등 제공 | 
| 백업/복구 | 자동 백업 및 복원 기능 내장 | 
| 적합한 경우 | 빠른 개발, 스타트업, DevOps 리소스가 부족한 팀 등 | 
-->

**유형별 비교**
| 항목 | MongoDB 설치형 | MongoDB Atlas |
|-----|---------------|---------------|  
| 형태        | On-Premise 또는 자체 서버            | 클라우드 관리형 서비스  |
| 설치 및 운영 | 사용자가 직접 설치, 구성, 유지보수 필요 | MongoDB에서 자동으로 관리 (배포, 패치, 모니터링 등) | 
| 유연성      | 서버, 설정, 보안 등 모든 것을 직접 제어 가능  | 설정은 제한적이지만 대부분의 기능은 UI로 쉽게 조작 가능 | 
| 비용        | 서버 비용, 인프라 유지비, 인건비 발생        | 사용량 기반 과금 (무료 플랜도 존재) | 
| 확장성      | 수동 확장 필요 (샤딩, 클러스터 구성 등)      | 버튼 클릭만으로 수평/수직 확장 가능 | 
| 보안        | 직접 구성해야 하며, 실수 시 취약점 발생 가능 | 기본적으로 TLS, IP 화이트리스트, 암호화 등 제공 | 
| 백업/복구    | 직접 스크립트 작성 또는 외부 도구 사용 필요  | 자동 백업 및 복원 기능 내장 | 
| 적합한 경우  | 고도의 커스터마이징이 필요한 환경, 내부망 전용 시스템 등 | 빠른 개발, 스타트업, DevOps 리소스가 부족한 팀 등 | 
- Atlas는 편리함과 자동화에 초점이 맞춰져 있고, 인프라 관리에 시간을 쓰고 싶지 않다면 최고의 선택!
- 직접 설치형 MongoDB는 제어권과 유연성이 필요할 때 유리하지만, 관리 부담이 크다!
<br/>

[[TOP]](#index)

---
### ⏯MongoDB 드라이버 연결
1. 드라이버와 버전을 선택 : Node.js ver6.7 이상
2. 드라이버 설치 : `npm install mongodb`
3. 연결 문자열을 애플리케이션 코드에 추가
```shell
mongodb+srv://jacekimtheal:<db_password>@cluster-jacekim.8pqgjqy.mongodb.net/?retryWrites=true&w=majority&appName=cluster-jacekim
```
☑ <db_password>를 jacekimtheal 데이터베이스 사용자 의 비밀번호로 바꾸세요. <br/>
☑ 모든 옵션 매개변수가 URL로 인코딩 되었는지 확인하세요 <br/>


<br/>

[[TOP]](#index)

---