# 인사 관리 사이트 
인사담당자가 직원들의 근태, 급여, 업무, 성과, 인사 관리 등을 관리할 수 있는 인사 관리 사이트를 개발하였다. 백엔드 개발을 맡아 급여, 업무, 성과, 프로필의 REST API를 구현하였고 프론트 담당과 notion을 통해 API 경로를 공유하며 진행하였다. 
<br>

## 개발 기능

- 인사 관리(사용자, 부서)
    - 인적사항관리
    - 인사발령
    - 인사현황
    - 조직도관리
- 근태 관리
    - 근태이력관리
    - 근무일정/시간
    - 초과 근무
- 급여 관리
    - 급여이력조회
    - 성과급 관리
- 업무 관리
    - 업무 조회(진행사항 등)
    - 업무 배정
- 성과 관리
    - 업적 평가
    - 역량 평가
    

## Preview
**급여관리 검색 & 수정**

![급여관리(검색,수정)resize](https://user-images.githubusercontent.com/76679463/110294913-d169ee80-8033-11eb-93ca-e164c704d8af.gif)


**업무관리 검색 & 추가**

![업무관리(검색,추가)resize](https://user-images.githubusercontent.com/76679463/110295375-60770680-8034-11eb-98d8-68f1b20bf332.gif)


**업무관리 수정**

![업무관리(수정)resize](https://user-images.githubusercontent.com/76679463/110295381-610f9d00-8034-11eb-9909-c4eabbb71cb7.gif)


**성과관리 검색 & 수정**

![성과관리(검색,수정)resize](https://user-images.githubusercontent.com/76679463/110295386-6371f700-8034-11eb-8777-a7fadb63c9c8.gif)


**프로필**

<img width="960" alt="프로필" src="https://user-images.githubusercontent.com/76679463/110295395-666ce780-8034-11eb-93a3-64b3b9f79f76.PNG">


**페이지네이션(공통)**

![페이지네이션risize](https://user-images.githubusercontent.com/76679463/110295398-679e1480-8034-11eb-8d91-910093294657.gif)     

<br>

## Backend architecture

### 데이터베이스 ERD

![erd](https://user-images.githubusercontent.com/50051656/103268353-a2614c00-49f6-11eb-8b8a-1364bfbe9f59.PNG)

### 도메인

![domain](https://user-images.githubusercontent.com/50051656/103268357-a2f9e280-49f6-11eb-8d9a-00b61415844b.PNG)  

### REST API
| Web API | URI | Description |
| :--- | :--- | :--- |
| 근태관리 | /attendance | - |
| 급여관리 | /salary | - |
| 급여관리 수정 | /salary/{empId}/edit | 
| 업무관리 | /work?nameType=:nameType&name=:name | :nameType - 업무명, 직원명, 부서명 드롭다운 선택 , :name - 이름 |
| 업무관리 추가 | /work/create | - |
| 업무관리 수정 | /work/{workId}/edit | - |
| 성과관리 | /evaluation=:nameType&name=:name | :nameType - 업무명, 직원명, 부서명 드롭다운 선택 , :name - 이름 |
| 성과관리 수정 | /evaluation.{evalBlockId}/edit | - |
| 인적사항관리 | /employee | - |
| 인사현황 | /transfer | - |
| 프로필 | /profile | 비밀번호 변경 기능 주석처리, ~~/profile/accessRecord 전체 접속기록 내역 API~~ | 

<br>

## 설치 및 실행 방법
### 설치
```
git clone https://github.com/songyen/WEB_Personnel_Management.git
cd frontend
npm install
```

### Spring Boot

- #### application.yaml 수정 (/src/main/resources 폴더 내에 존재)

```
spring:
  datasource:
    url: <해당 DB 주소>
    username: <DB ID>
    password: <DB PW>
    driver-class-name: <해당 DB 드라이버>
    ex) driver-class-name: org.h2.driver (H2)
        driver-class-name: com.mysql.cj.jdbc.Driver (MYSQL)
```

- #### Build And Run

```
1. ./gradlew build -x test
2. cp GeoLite2-City.mmdb build/libs
3. java -jar -Djava.net.perferIPv4Stack=true build/libs/<생성된 jar 파일>
4. localhost:8080/init 접속  // 더미데이터 생성
5. npm start
```


<img width="921" alt="캡처" src="https://user-images.githubusercontent.com/76679463/110306150-d4b7a700-8040-11eb-89ff-c426ec746f8a.PNG">  

 > 아이디 : test10@okky.kr (또는 test20@okky.kr, test30@okky.kr, test40@okky.kr, test50@okky.kr)
 

 > 비밀번호 : 1234

## 의존 라이브러리

- data-jpa
- thymeleaf
- spring-web
- security
- lombok
- devtools
- h2 database
- mysql
- JWT
- [maxmind.geoip2](https://github.com/maxmind) // 접속 클라이언트 ip를 통해 위치 정보 얻는 오픈소스

## 개발 환경

- Gradle Project
- Spring Boot 2.4.1
- Java jdk 11
