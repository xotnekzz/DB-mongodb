# MonogoDB 설치 및 세팅

## 1. MongoDB 설치
 - `mongodb_strech_3_0_14_core.zip` 파일 압축해제

 - 압축 해제 후 core가 생성되고 추가로 config, data, logs 디렉토리를 생성한다. 
![디렉토리구성](/uploads/b93ac6be51d29f39448a17a37b66a4db/디렉토리구성.PNG)

## 2. MongoDB 세팅

### 2-1 MongoDB 계정 설정

- 관리자 계정 설정

```javascript
use admin
db.createUser( { user: "<username>",
          pwd: "<password>",
          roles: [ "userAdminAnyDatabase",
                   "dbAdminAnyDatabase",
                   "readWriteAnyDatabase"
 
] } )

```

- 사용자 계정 설정

```javascript
use <DBName>
db.createUser({ user: "<username>",
          pwd: "<password>",
          roles: ["dbAdmin", "readWrite"]
})
```

- 관리자/사용자 계정삭제

```javascript
use Admin
db.dropUser("<username>")
```

- 계정설정 EX)
![User](/uploads/dd35c90ef36e9ad67969c0197f9ae97d/User.PNG)

### 2-2 MongoDB Config
- `vim /ice/system/mongodb/config/mongodb.conf`
![dbConfig](/uploads/42924541ddc675815aede4e6df5139ae/dbConfig.PNG)


### 2-3 MongoDB Log
- `vim /ice/system/mongodb/logs/mongo.log` mongo.log 파일을 생성해야 로그가 기록된다.

## 3. MongoDB 실행
- `./mongod --config ../config/mongodb.conf --journal`(MongoDB Server)
- `./mongo IP_ADDRESS:PORT` ex) ./mongo 192.168.255.38:29000 (MongoDB Client)

