<style>
c-red { color: red }
</style>


**customer**
**wallet**
**reward**
**assets**

-내부용-
**accounts**
**customers**




**customer**
----
  Returns json data about a customer info.

- **Request**

URL
```
POST /customer HTTP/1.1
Host: http://localhost:4000
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOjEsImlhdCI6MTYyMTUwMDc0OH0.Vf-GchhDE-GWyV9mQcQAW9kEB2jlGmHzzZ1nL8oq_y8
```
<span style="color:red; font-size : 14px">**Authorization의 Bearer 이하 내용은 에이락에서 전달</span>

Parameter

|Name|Type|Description|Require|Example|
|:---:|:---:|---|---|---|
|<c-red>customerUID|String|고객사의 고객 고유 번호|O|"afun-UID_00000001"|
|name|String|사용자 이름|O|"홍길동"|
|info|String|사용자 정보|X|"첫번째 테스트 유저"|


- **Response**

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|userToken|Int|userToken|"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjI3MDAyODd9.w78SqeGRc-gmZPLwxTsy6LwfCiBrKm4UKnw4riUb_2M"|
|installed|Boolean|앱 설치 여부|"true"|


Error Message
|error_code|error_description	|Description|
|---|---|---|
|401|error: 'Authorization failed!' or error: 'API Token is not match!'|인증이 실패했거나 API토큰이 불일치할 경우|
|500|error|error 내용|

Sample

Sample Call:

  ```javascript
  POST http://localhost:4000/customer HTTP/1.1
  content-type: application/json
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOjEsImlhdCI6MTYyMTUwMDc0OH0.Vf-GchhDE-GWyV9mQcQAW9kEB2jlGmHzzZ1nL8oq_y8

  {
    "customerUID": "afun-UID_00000001",
    "name": "홍길동",
    "info": "첫번째 테스트 유저"
  }
  ```

Sample Respons:

  ```javascript
  HTTP/1.1 200 OK
  X-Powered-By: Express
  Access-Control-Allow-Origin: *
  Content-Type: application/json; charset=utf-8
  Content-Length: 202
  ETag: W/"ca-SEMOVXTvVLl/gTZJr7dLX2h3H1U"
  Date: Mon, 07 Jun 2021 06:49:07 GMT
  Connection: close

  {
    "userToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjMwNDg1NDd9.KvKNI7-M5DGQ1usI4oXSxZ6n4qnW8hb6pp3kLkepiJA",
    "installed": true
  }
  ```

------















**wallet**
----
  Returns json data about a wallet info.

- **Request**

URL
```
POST /wallet HTTP/1.1
Host: http://localhost:4000
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjb21wYW55SWQiOjEsImlhdCI6MTYyMjcwNDQyN30.qpq_UF2ebwr2IcEtvsPaS8TMU0tVCWz3B3r_7p32MVQ
```
<span style="color:red; font-size : 14px">**Authorization의 Bearer 이하 내용은 에이락에서 전달</span>

Parameter

|Name|Type|Description|Require|Example|
|:---:|:---:|---|---|---|
|<c-red>userToken|String|고객 식별 토큰|O|"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjI3MDQyODh9.ZdYP5rb54FYKM9FS_56m9ymXZOTRnt126zd5IuIv8m0"|
|<c-red>safeAccount|String|에이락 월렛 주소|X|"0x332a1d47bfcdbe0ad43dc16d5b3172bbc8c31d0b"|
|<c-red>publicKey|String|에이락 월렛 퍼블릭키|O|"tempPublicKey1622427282147"|
|walletUID|String|지갑 UID|O|"walletUID_00000001"|
|email|String|사용자 email|X|"test1@test.co.kr"|
|name|String|사용자 이름|X|"홍길동"|
|info|String|사용자 정보|X|"info001"|
|deviceType|String|기기 타입|O|"deviceType0001"|
|deviceId|String|기기 id(푸시 알림용)|O|"deviceId0001"|


- **Response**

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|Int|지갑 id|1|
|createdAt|String|생성 시간|"2021-06-03T07:11:28.175Z"|
|updatedAt|String|업데이트 시간|"2021-06-03T07:11:28.175Z"|
|customerUID|String|고객사의 고객 고유 번호|"customerUID_001"|
|safeAccount|String|에이락 월렛 주소|"0x332a1d47bfcdbe0ad43dc16d5b3172bbc8c31d0b"|
|publicKey|String|에이락 월렛 퍼블릭키|"tempPublicKey1622427282147"|
|channel_name|String|고객사명|"고객사0001"|
|wallet_nane|Int|wallet id|"wallet_name001"|
|elements|List\<assets>|해당 고객의 asset 리스트|하단 참조|

assets

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|int|사용자 asset id|1|
|createdAt|String|생성 시각|"2021-05-21T07:17:15.653Z"|
|updatedAt|String|업데이트 시각|"2021-05-21T07:17:15.653Z"|
|balance|String|리워드 잔고|"50000"|
|customer_name|String|사용자 이름|"홍길동"|
|account_nickname|String|계좌 별칭|"투자용계좌"|
|chain_name|String|체인명|"Ethereum"|
|tokenSpec_name|String|토큰명|"tokenSpec_name"|
|tokenSpec_symbol|String|토큰 심볼|"ETH"|
|tokenSpec_decimal|String|토큰 데시멀|"10"|

Error Message

|error_code|error_description	|Description|
|---|---|---|
|401|error: 'Authorization failed!' or error: 'API Token is not match!'|인증이 실패했거나 API토큰이 불일치할 경우|
|500|error|error 내용|

Sample

Sample Call:

  ```javascript
  POST http://localhost:4000/account HTTP/1.1
  content-type: application/json
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOjEsImlhdCI6MTYyMTUwMDc0OH0.Vf-GchhDE-GWyV9mQcQAW9kEB2jlGmHzzZ1nL8oq_y8

  {
    "userToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjI3MDQyODh9.ZdYP5rb54FYKM9FS_56m9ymXZOTRnt126zd5IuIv8m0",
    "safeAccount": "에이락 앱에서 전달",
    "publicKey": "에이락 앱에서 전달",
    "walletUID": "deviceType00001",
    "email": "test1@test.co.kr",
    "name": "test001",
    "info": "info001",
    "deviceType": "deviceType0001",
    "deviceId": "deviceId0001"
  }

  ```
Sample Respons:

  ```javascript
HTTP/1.1 200 OK
X-Powered-By: Express
Access-Control-Allow-Origin: *
Content-Type: application/json; charset=utf-8
Content-Length: 511
ETag: W/"1ff-BVqjzpj9add5jyibwfQ8aTtW9M8"
Date: Mon, 07 Jun 2021 06:50:55 GMT
Connection: close

{
  "id": 1,
  "createdAt": "2021-06-04T04:46:29.624Z",
  "updatedAt": null,
  "customerUID": "customerUID_001",
  "safeAccount": "에이락 앱에서 전달_Unique00801",
  "publicKey": "에이락 앱에서 전달_Unique00801",
  "channel_name": "고객사0001",
  "wallet_name": "wallet_name001",
  "assets": [
    {
      "id": 2,
      "createdAt": "2021-06-04T05:44:18.280Z",
      "updatedAt": null,
      "balance": "5005",
      "customer_name": "홍길동",
      "account_nickname": "투자용계좌",
      "chain_name": "Ethereum",
      "tokenSpec_name": "tokenSpec_name",
      "tokenSpec_symbol": "ETH",
      "tokenSpec_decimal": "10",
    },
    {
      "id": 4,
      "createdAt": "2021-06-07T04:02:41.428Z",
      "updatedAt": null,
      "balance": "0",
      "customer_name": "홍길동",
      "account_nickname": "투자용계좌",
      "chain_name": "Ethereum",
      "tokenSpec_name": "tokenSpec_name",
      "tokenSpec_symbol": "ETH",
      "tokenSpec_decimal": "10"
    }
  ]
}
  ```
------









**reward**
----
  Returns json data about a asset balance.

- **Request**

URL
```
POST /reward HTTP/1.1
Host: http://localhost:4000
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOjEsImlhdCI6MTYyMTUwMDc0OH0.Vf-GchhDE-GWyV9mQcQAW9kEB2jlGmHzzZ1nL8oq_y8
```

Parameter

|Name|Type|Description|Require|Example|
|:---:|:---:|---|---|---|
|<c-red>userToken|String|고객 식별 토큰|O|"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjI3MDQyODh9.ZdYP5rb54FYKM9FS_56m9ymXZOTRnt126zd5IuIv8m0"|
|<c-red>requestUID|String|각 고객사 앱에서 전송하는 유니크한 값|O|"requestUID_example_000001"|
|date|String|고객사에서 전달한 date 정보|O|"something.."|
|value|String|고객사에서 사용자가 사용한 금액|O|"1"|
|currency|String|통화 화폐|X|"KRW"|
|type|String|사용자의 이벤트 타입|O|"transfer" or "signup"...|
|territory|String|국가 지역 코드|X|"KR"|


- **Response**

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|Int|Asset ID|20|
|createdAt|String|생성 시각|"2021-05-21T07:17:15.653Z"|
|updatedAt|String|업데이트 시각|"2021-05-21T07:17:15.653Z"|
|balance|String|리워드 잔고|"10000"|
|customer_name|String|사용자 이름|"홍길동"|
|account_nickname|String|계좌 별칭|"투자용계좌"|
|chain_name|String|체인명|"Ethereum"|
|tokenSpec_name|String|토큰명|"tokenSpec_name"|
|tokenSpec_symbol|String|토큰 심볼|"ETH"|
|tokenSpec_decimal|String|토큰 데시멀|"10"|


Error Message

|error_code|error_description	|Description|
|---|---|---|
|401|error: 'Authorization failed!' or error: 'API Token is not match!'|인증이 실패했거나 API토큰이 불일치할 경우|
|500|error|error 내용|

Sample

Sample Call:

  ```javascript
POST http://localhost:4000/reward HTTP/1.1
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOjEsImlhdCI6MTYyMTgzNDQxN30.crpvk76sgQgIjEp5z_Ei3YXLYqWC-Chnpm31mRYNGWw

{
  "userToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjI3MDQyODh9.ZdYP5rb54FYKM9FS_56m9ymXZOTRnt126zd5IuIv8m0",
  "requestUID": "고객사앱에서 전송_Unique_000002",
  "date": "date_test_00001",
  "value": "1000",
  "currency": "KRW",
  "type": "transfer",
  "territory": "KR"
}
  ```
Sample Respons:

  ```javascript
HTTP/1.1 200 OK
X-Powered-By: Express
Access-Control-Allow-Origin: *
Content-Type: application/json; charset=utf-8
Content-Length: 135
ETag: W/"87-EAvSOLtv83DV7aSPGeTBzel+V00"
Date: Mon, 07 Jun 2021 06:51:59 GMT
Connection: close

{
  "id": 2,
  "createdAt": "2021-06-04T05:44:18.280Z",
  "updatedAt": null,
  "balance": "6005",
  "customer_name": "홍길동",
  "chain_name": "Ethereum",
  "account_nickname": "투자용계좌",
  "tokenSpec_name": "tokenSpec_name",
  "tokenSpec_symbol": "ETH",
  "tokenSpec_decimal": "10"
}

  ```
------

















**assets**
----
  Returns json data about a asset list.

- **Request**

URL
```
POST /assets HTTP/1.1
Host: http://localhost:4000
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOjEsImlhdCI6MTYyMTgzNDQxN30.crpvk76sgQgIjEp5z_Ei3YXLYqWC-Chnpm31mRYNGWw
```

Parameter

|Name|Type|Description|Require|Example|
|:---:|:---:|---|---|---|
|<c-red>userToken|String|암호화된 계정값|O|"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjI3MDQyODh9.ZdYP5rb54FYKM9FS_56m9ymXZOTRnt126zd5IuIv8m0"|
|<c-red>safeAccount|String|에이락 월렛 주소|X|"0x332a1d47bfcdbe0ad43dc16d5b3172bbc8c31d0b"|


- **Response**

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|Int|DB상의 사용자 id|20|
|createdAt|String|생성 시각|"2021-05-21T07:17:15.653Z"|
|updatedAt|String|업데이트 시각|"2021-05-21T07:17:15.653Z"|
|customerUID|String|고객사의 고객 고유 번호|"customerUID_001"|
|safeAccount|String|에이락 월렛 주소|"0x332a1d47bfcdbe0ad43dc16d5b3172bbc8c31d0b"|
|publicKey|String|에이락 월렛 퍼블릭키|"tempPublicKey1622427282147"|
|channelId|Int|channelId|1|
|walletId|Int|walletId|1|
|elements|List\<assets>|해당 고객의 assets 리스트|하단 참조|

assets
|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|int|사용자 asset id|1|
|createdAt|String|생성 시각|"2021-05-21T07:17:15.653Z"|
|updatedAt|String|업데이트 시각|"2021-05-21T07:17:15.653Z"|
|balance|String|리워드 잔고|"50000"|
|elements|\<chain>|해당 고객의 체인|하단 참조|
|elements|\<account>|해당 고객의 지갑|하단 참조|
|elements|\<tokenSpec>|해당 고객의 토큰스펙|하단 참조|

chain
|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|int|사용자 chain id|1|
|createdAt|String|생성 시각|"2021-05-21T07:17:15.653Z"|
|updatedAt|String|업데이트 시각|"2021-05-21T07:17:15.653Z"|
|name|String|chain name|"Ethereum"|
|regNumber|String|사업자 등록번호|"04861486-486-4887725"|
|info|String|체인 정보|"something info..."|

account
|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|int|사용자 account id|1|
|createdAt|String|생성 시각|"2021-05-21T07:17:15.653Z"|
|updatedAt|String|업데이트 시각|"2021-05-21T07:17:15.653Z"|
|address|String|암호화폐 지갑 주소|"0x00115ag48r4vr86s6v4rbn"|
|nickname|String|암호화폐 지갑 별칭|"my_first_account"|
|info|String|지갑 정보|"something info..."|
|ownerId|Int|ownerId|1|
|chainId|Int|chainId|1|

tokenSpec
|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|int|사용자 tokenSpec id|1|
|createdAt|String|생성 시각|"2021-05-21T07:17:15.653Z"|
|updatedAt|String|업데이트 시각|"2021-05-21T07:17:15.653Z"|
|address|String|token address|"0x00115ag48r4vr86s6v4rbn"|
|name|String|tokenSpec name|"my_first_account"|
|symbol|String|token symbol|"ETH"|
|decimal|String|token decimal|"10"|
|info|String|토큰 스펙 정보|"something info..."|
|chainId|Int|chainId|1|

Error Message

|error_code|error_description	|Description|
|---|---|---|
|401|error: 'Authorization failed!' or error: 'API Token is not match!'|인증이 실패했거나 API토큰이 불일치할 경우|
|500|error|error 내용|

Sample

Sample Call:

  ```javascript
POST http://localhost:4000/assets HTTP/1.1
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOjEsImlhdCI6MTYyMTgzNDQxN30.crpvk76sgQgIjEp5z_Ei3YXLYqWC-Chnpm31mRYNGWw

{
  "safeAccount": "0x332a1d47bfcdbe0ad43dc16d5b3172bbc8c31d0b",
  "userToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjI3MDQyODh9.ZdYP5rb54FYKM9FS_56m9ymXZOTRnt126zd5IuIv8m0"
}
  ```

Sample Respons:

  ```javascript
HTTP/1.1 200 OK
X-Powered-By: Express
Access-Control-Allow-Origin: *
Content-Type: application/json; charset=utf-8
Content-Length: 1708
ETag: W/"6ac-iZUw4HTmLh1aJmLO9W3s6zl4/Ig"
Date: Mon, 07 Jun 2021 07:05:01 GMT
Connection: close

{
  "id": 1,
  "createdAt": "2021-06-04T04:46:29.624Z",
  "updatedAt": null,
  "customerUID": "customerUID_001",
  "safeAccount": "에이락 앱에서 전달_Unique00801",
  "publicKey": "에이락 앱에서 전달_Unique00801",
  "channelId": 1,
  "walletId": 7,
  "assets": [
    {
      "id": 2,
      "createdAt": "2021-06-04T05:44:18.280Z",
      "updatedAt": null,
      "balance": "6005",
      "ownerId": 1,
      "chainId": 1,
      "accountId": 1,
      "tokenSpecId": 1,
      "chain": {
        "id": 1,
        "createdAt": "2021-06-04T04:37:00.496Z",
        "updatedAt": null,
        "name": "Ethereum",
        "regNumber": "0001",
        "info": null,
        "apiToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFpbklkIjoxLCJpYXQiOjE2MjI3ODE0MjB9.AVyRaeeJCDqCS_gw4WMNpdUB9hEUsb0n09XvMjRoC1M"
      },
      "account": {
        "id": 1,
        "createdAt": "2021-06-04T05:37:47.800Z",
        "updatedAt": null,
        "address": "0x00",
        "nickname": "test_nick",
        "info": null,
        "ownerId": 1,
        "chainId": 1
      },
      "tokenSpec": {
        "id": 1,
        "createdAt": "2021-06-04T04:43:13.574Z",
        "updatedAt": null,
        "address": "0x001",
        "name": "Ethereum",
        "symbol": "ETH",
        "decimals": "10",
        "info": null,
        "chainId": 1
      }
    },
    {
      "id": 4,
      "createdAt": "2021-06-07T04:02:41.428Z",
      "updatedAt": null,
      "balance": "0",
      "ownerId": 1,
      "chainId": 1,
      "accountId": 4,
      "tokenSpecId": 1,
      "chain": {
        "id": 1,
        "createdAt": "2021-06-04T04:37:00.496Z",
        "updatedAt": null,
        "name": "Ethereum",
        "regNumber": "0001",
        "info": null,
        "apiToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFpbklkIjoxLCJpYXQiOjE2MjI3ODE0MjB9.AVyRaeeJCDqCS_gw4WMNpdUB9hEUsb0n09XvMjRoC1M"
      },
      "account": {
        "id": 4,
        "createdAt": "2021-06-07T03:27:17.639Z",
        "updatedAt": null,
        "address": "0xF93e202436CB458E99DC12c33bD1875A32eF491b",
        "nickname": "테스트 계정",
        "info": null,
        "ownerId": 3,
        "chainId": 1
      },
      "tokenSpec": {
        "id": 1,
        "createdAt": "2021-06-04T04:43:13.574Z",
        "updatedAt": null,
        "address": "0x001",
        "name": "Ethereum",
        "symbol": "ETH",
        "decimals": "10",
        "info": null,
        "chainId": 1
      }
    }
  ]
}

  ```

------


















**아래 내용은 에이락 내부용입니다.**
------

-----



**accounts**
----
  Returns json data about a account list.

- **Request**

URL
```
POST /accounts HTTP/1.1
Host: http://localhost:4000
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOjEsImlhdCI6MTYyMTgzNDQxN30.crpvk76sgQgIjEp5z_Ei3YXLYqWC-Chnpm31mRYNGWw
```

Parameter

|Name|Type|Description|Require|Example|
|:---:|:---:|---|---|---|
|<c-red>userToken|String|암호화된 계정값|O|"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjI3MDQyODh9.ZdYP5rb54FYKM9FS_56m9ymXZOTRnt126zd5IuIv8m0"|
|<c-red>safeAccount|String|에이락 월렛 주소|X|"0x332a1d47bfcdbe0ad43dc16d5b3172bbc8c31d0b"|


- **Response**

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|Int|DB상의 사용자 id|20|
|createdAt|String|생성 시각|"2021-05-21T07:17:15.653Z"|
|updatedAt|String|업데이트 시각|"2021-05-21T07:17:15.653Z"|
|channelId|Int|channelId|1|
|walletId|Int|walletId|1|
|customerUID|String|고객사의 고객 고유 번호|"customerUID_001"|
|safeAccount|String|에이락 월렛 주소|"0x332a1d47bfcdbe0ad43dc16d5b3172bbc8c31d0b"|
|publicKey|String|에이락 월렛 퍼블릭키|"tempPublicKey1622427282147"|
|elements|List\<accounts>|해당 고객의 지갑 리스트|하단 참조|

accounts

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|int|사용자 account id|1|
|createdAt|String|생성 시각|"2021-05-21T07:17:15.653Z"|
|updatedAt|String|업데이트 시각|"2021-05-21T07:17:15.653Z"|
|ownerId|Int|ownerId|1|
|chainId|Int|chainId|1|
|address|String|암호화폐 지갑 주소|"0x00115ag48r4vr86s6v4rbn"|
|nickname|String|암호화폐 지갑 별칭|"my_first_account"|
|info|String|지갑 정보|"something info..."|
|elements|\<chain>|해당 고객의 체인|하단 참조|

chain

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|int|사용자 chain id|1|
|createdAt|String|생성 시각|"2021-05-21T07:17:15.653Z"|
|updatedAt|String|업데이트 시각|"2021-05-21T07:17:15.653Z"|
|name|String|체인 이름|"Ethereum"|
|regNumber|String|사업자 등록번호|"04861486-486-4887725"|
|info|String|체인 정보|"something info..."|


Error Message

|error_code|error_description	|Description|
|---|---|---|
|401|error: 'Authorization failed!' or error: 'API Token is not match!'|인증이 실패했거나 API토큰이 불일치할 경우|
|500|error|error 내용|

Sample

Sample Call:

  ```javascript
POST http://localhost:4000/accounts HTTP/1.1
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOjEsImlhdCI6MTYyMTgzNDQxN30.crpvk76sgQgIjEp5z_Ei3YXLYqWC-Chnpm31mRYNGWw

{
  "safeAccount": "0x332a1d47bfcdbe0ad43dc16d5b3172bbc8c31d0b",
  "userToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjI3MDQyODh9.ZdYP5rb54FYKM9FS_56m9ymXZOTRnt126zd5IuIv8m0"
}
  ```

  Sample Respons:

  ```javascript
HTTP/1.1 200 OK
X-Powered-By: Express
Access-Control-Allow-Origin: *
Content-Type: application/json; charset=utf-8
Content-Length: 1040
ETag: W/"410-WN9gG9VDE/NcmoRN6wVKloL/YsM"
Date: Mon, 07 Jun 2021 06:55:41 GMT
Connection: close

{
  "id": 1,
  "createdAt": "2021-06-04T04:46:29.624Z",
  "updatedAt": null,
  "customerUID": "customerUID_001",
  "safeAccount": "에이락 앱에서 전달_Unique00801",
  "publicKey": "에이락 앱에서 전달_Unique00801",
  "channelId": 1,
  "walletId": 7,
  "accounts": [
    {
      "id": 1,
      "createdAt": "2021-06-04T05:37:47.800Z",
      "updatedAt": null,
      "address": "0x00",
      "nickname": "test_nick",
      "info": null,
      "ownerId": 1,
      "chainId": 1,
      "chain": {
        "id": 1,
        "createdAt": "2021-06-04T04:37:00.496Z",
        "updatedAt": null,
        "name": "Ethereum",
        "regNumber": "0001",
        "info": null,
        "apiToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFpbklkIjoxLCJpYXQiOjE2MjI3ODE0MjB9.AVyRaeeJCDqCS_gw4WMNpdUB9hEUsb0n09XvMjRoC1M"
      }
    },
    {
      "id": 3,
      "createdAt": "2021-06-04T05:37:47.800Z",
      "updatedAt": null,
      "address": "0x001",
      "nickname": "test_nick2",
      "info": null,
      "ownerId": 1,
      "chainId": 2,
      "chain": {
        "id": 2,
        "createdAt": "2021-06-04T04:37:09.110Z",
        "updatedAt": null,
        "name": "Tether",
        "regNumber": "0002",
        "info": null,
        "apiToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFpbklkIjoyLCJpYXQiOjE2MjI3ODE0Mjl9.bnuhTPF5cnVDVjcyFFv3UZpjuew9wXPTmbZClQKCLZM"
      }
    }
  ]
}


  ```

------









**customers**
----
  Returns json data about a Customers list included in the wallet .

- **Request**

URL
```
POST /customers HTTP/1.1
Host: http://localhost:4000
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjb21wYW55SWQiOjEsImlhdCI6MTYyMjc4MTIwNX0.1DBH3PeicySHdw7fZBeig4MnLoIglcd2INmgvoudWYw
```

Parameter

|Name|Type|Description|Require|Example|
|:---:|:---:|---|---|---|
|walletUID|String|wallet UID|O|"walletUID0001"|

- **Response**

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|Int|DB상의 wallet id|20|
|createdAt|String|생성 시각|"2021-05-21T07:17:15.653Z"|
|updatedAt|String|업데이트 시각|"2021-05-21T07:17:15.653Z"|
|walletUID|String|wallet UID|"walletUID0001"|
|email|String|wallet email|"test1@test.co.kr"|
|name|String|wallet name|"테스터"|
|info|Int|사용자 정보|1|
|elements|List\<customers>|해당 wallet의 customer 리스트|하단 참조|

customers

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|Int|customer id|1|
|createdAt|String|생성 시간|"2021-06-03T07:11:28.175Z"|
|updatedAt|String|업데이트 시간|"2021-06-03T07:11:28.175Z"|
|customerUID|String|고객사의 고객 고유 번호|"customerUID_001"|
|safeAccount|String|에이락 월렛 주소|"0x332a1d47bfcdbe0ad43dc16d5b3172bbc8c31d0b"|
|publicKey|String|에이락 월렛 퍼블릭키|"tempPublicKey1622427282147"|
|channel_name|Int|channel id 값|"고객사0001"|
|wallet_nane|Int|wallet id|"wallet_name001"|


Error Message

|error_code|error_description	|Description|
|---|---|---|
|401|error: 'Authorization failed!' or error: 'API Token is not match!'|인증이 실패했거나 API토큰이 불일치할 경우|
|500|error|error 내용|

Sample

Sample Call:

  ```javascript
POST http://localhost:4000/customers HTTP/1.1
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjb21wYW55SWQiOjEsImlhdCI6MTYyMjc4MTIwNX0.1DBH3PeicySHdw7fZBeig4MnLoIglcd2INmgvoudWYw

{
  "walletUID": "Tester01"
}
  ```

Sample Respons:

  ```javascript
HTTP/1.1 200 OK
X-Powered-By: Express
Access-Control-Allow-Origin: *
Content-Type: application/json; charset=utf-8
Content-Length: 765
ETag: W/"2fd-hnnyYmmRiYQ4a8LYzaltLWInQiI"
Date: Mon, 07 Jun 2021 07:05:58 GMT
Connection: close

{
  "id": 4,
  "createdAt": "2021-06-07T02:25:19.691Z",
  "updatedAt": null,
  "walletUID": "Tester01",
  "email": "test@a-fun.co.kr",
  "name": "테스터",
  "info": null,
  "customers": [
    {
      "id": 3,
      "createdAt": "2021-06-07T02:21:17.105Z",
      "updatedAt": null,
      "customerUID": "tester01",
      "safeAccount": "",
      "publicKey": "",
      "channel_name": "고객사0001",
      "wallet_nane": "wallet_name001"
    },
    {
      "id": 4,
      "createdAt": "2021-06-07T02:22:01.418Z",
      "updatedAt": null,
      "customerUID": "tester02",
      "safeAccount": "1",
      "publicKey": "1",
      "channel_name": "고객사0001",
      "wallet_nane": "wallet_name001"
    }
  ]
}

  ```
------









**rewards**
----
  Returns json data about a Customer's rewards.

- **Request**

URL
```
POST /rewards HTTP/1.1
Host: http://localhost:4000
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjb21wYW55SWQiOjEsImlhdCI6MTYyMjc4MTIwNX0.1DBH3PeicySHdw7fZBeig4MnLoIglcd2INmgvoudWYw
```

Parameter

|Name|Type|Description|Require|Example|
|:---:|:---:|---|---|---|
|<c-red>userToken|String|고객 식별 토큰|O|"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjI3MDQyODh9.ZdYP5rb54FYKM9FS_56m9ymXZOTRnt126zd5IuIv8m0"|
|<c-red>safeAccount|String|에이락 월렛 주소|X|"0x332a1d47bfcdbe0ad43dc16d5b3172bbc8c31d0b"|
|type|String|사용자의 이벤트 타입|X|"transfer" or "signup"...|


- **Response**

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|Int|리워드 ID|20|
|createdAt|String|생성 시각|"2021-05-21T07:17:15.653Z"|
|updatedAt|String|업데이트 시각|"2021-05-21T07:17:15.653Z"|
|requestUID|String|각 고객사 앱에서 전송하는 유니크한 값|"RequestUID_0001"|
|date|String|고객사에서 전달한 date 정보|"something date.."|
|type|String|사용자의 이벤트 타입|"transfer"|
|value|String|고객사에서 사용자가 사용한 금액|"10000"|
|currency|String|통화 화폐|"KRW"|
|territory|String|국가 지역 코드|X|"KR"|
|amount|String|리워드 금액|"100"|
|status|String|리워드 지급 상태|"reward"|
|channel_name|String|고객사명|"고객사0001"|
|customer_name|String|사용자 이름|"홍길동"|
|account_nickname|String|계좌 별칭|"투자용계좌"|
|chain_name|String|체인명|"Ethereum"|
|tokenSpec_name|String|토큰명|"tokenSpec_name"|
|tokenSpec_symbol|String|토큰 심볼|"ETH"|
|tokenSpec_decimal|String|토큰 데시멀|"10"|
|elements|\<asset>|해당 사용자의 asset 리스트|하단 참조|

asset

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|int|사용자 asset id|1|
|createdAt|String|생성 시각|"2021-05-21T07:17:15.653Z"|
|updatedAt|String|업데이트 시각|"2021-05-21T07:17:15.653Z"|
|balance|String|리워드 잔고|"50000"|


Error Message

|error_code|error_description	|Description|
|---|---|---|
|401|error: 'Authorization failed!' or error: 'API Token is not match!'|인증이 실패했거나 API토큰이 불일치할 경우|
|500|error|error 내용|

Sample

Sample Call:

  ```javascript
POST http://localhost:4000/rewards HTTP/1.1
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjb21wYW55SWQiOjEsImlhdCI6MTYyMjc4MTIwNX0.1DBH3PeicySHdw7fZBeig4MnLoIglcd2INmgvoudWYw

{
  "userToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjMwNDUzOTR9.M0kAkn0ge8kwWhs5m4OaeLhYEnAt6Tm78_Y3aB22QXg",
  "safeAccount":"에이락 앱에서 전달_Unique00801",
  "type": "transfer"
}
  ```

Sample Respons:

  ```javascript
HTTP/1.1 200 OK
X-Powered-By: Express
Access-Control-Allow-Origin: *
Content-Type: application/json; charset=utf-8
Content-Length: 4230
ETag: W/"1086-L02B47iOh7+lVwV2P5vegdJ+ocI"
Date: Mon, 07 Jun 2021 08:08:02 GMT
Connection: close

[
  {
    "id": 2,
    "createdAt": "2021-06-04T05:44:18.280Z",
    "updatedAt": null,
    "requestUID": "고객사앱에서 전송_Unique_000001",
    "date": "date_test_00001",
    "type": "transfer",
    "value": "1000",
    "currency": "KRW",
    "territory": "KR",
    "amount": "1000",
    "status": "reward",
    "channel_name": "고객사0001",
    "customer_name": "홍길동",
    "account_nickname": "투자용계좌",
    "chain_name": "Ethereum",
    "tokenSpec_name": "tokenSpec_name",
    "tokenSpec_symbol": "ETH",
    "tokenSpec_decimal": "10",
    "assetId": 2,
    "asset": {
      "id": 2,
      "createdAt": "2021-06-04T05:44:18.280Z",
      "updatedAt": null,
      "balance": "8005",
    }
  },
  {
    "id": 3,
    "createdAt": "2021-06-04T05:44:35.084Z",
    "updatedAt": null,
    "requestUID": "고객사앱에서 전송_Unique_000002",
    "date": "date_test_00001",
    "type": "transfer",
    "value": "1000",
    "currency": "KRW",
    "territory": "KR",
    "amount": "1000",
    "status": "reward",
    "channel_name": "고객사0001",
    "customer_name": "홍길동",
    "account_nickname": "투자용계좌",
    "chain_name": "Ethereum",
    "tokenSpec_name": "tokenSpec_name",
    "tokenSpec_symbol": "ETH",
    "tokenSpec_decimal": "10",
    "assetId": 2,
    "asset": {
      "id": 2,
      "createdAt": "2021-06-04T05:44:18.280Z",
      "updatedAt": null,
      "balance": "8005"
    }
  }
]

  ```
------









