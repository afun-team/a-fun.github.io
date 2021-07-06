<style>
c-red { color: red }
h1 { display: none }
hr { margin-bottom: 80px !important }
api-title { font-size: 3em; font-weight: bold }
.arrow { padding-top: 40px }
</style>

<div style="font-size: 1.5em; font-weight: bold">API List</div>
<hr style="margin-bottom: 20px !important">

|API Name|Description|
|:---:|:---|
|[customer🔗](#customer)|customer 등록|
|[reward🔗](#reward)|reward 지급|
|[accounts🔗](#accounts)|account list 조회|
|[rewards🔗](#rewards)|reward 지급내역들 조회|
|[assets🔗](#assets)|assets 조회|




-내부용-

|API Name|Description|
|:---:|:---|
|[customers🔗](#customers)|customer list 조회|
|[wallet🔗](#wallet)|wallet 생성|



------

<api-title id="customer">customer</api-title>
Returns json data about a customer info.

<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Request</strong>
</div>

URL
```
POST /v1/customer HTTP/1.1
Host: https://api.alock.io
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOjEsImlhdCI6MTYyMTUwMDc0OH0.Vf-GchhDE-GWyV9mQcQAW9kEB2jlGmHzzZ1nL8oq_y8
```
<span style="color:red; font-size : 14px">**Authorization: Bearer {고객사 AccessToken}</span>

Parameter

|Name|Type|Description|Required|Example|
|:---:|:---:|---|---|---|
|<c-red>customerUID|String|고객사의 고객 고유 번호|O|"afun-UID_00000001"|


<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Response</strong>
</div>

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|userToken|Int|userToken|"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjI3MDAyODd9.w78SqeGRc-gmZPLwxTsy6LwfCiBrKm4UKnw4riUb_2M"|
|installed|Boolean|앱 설치 여부|"true"|


Error Message

|error_code|error_description	|Description|
|---|---|---|
|401|error: 'Authorization failed!' or error: 'API Token is not match!'|인증이 실패했거나 API토큰이 불일치할 경우|
|500|error|error 내용|

<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Sample</strong>
</div>

Sample Call:

  ```javascript
  POST https://api.alock.io/v1/customer HTTP/1.1
  content-type: application/json
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOjEsImlhdCI6MTYyMTUwMDc0OH0.Vf-GchhDE-GWyV9mQcQAW9kEB2jlGmHzzZ1nL8oq_y8

  {
    "customerUID": "afun-UID_00000001"
  }
  ```

Sample Response:

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

  <a href="#" class="btn--success">처음으로</a>

------












<api-title id="reward">reward</api-title>
Returns json data about a asset balance.

<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Request</strong>
</div>

URL
```
POST /v1/reward HTTP/1.1
Host: https://api.alock.io
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOjEsImlhdCI6MTYyMTUwMDc0OH0.Vf-GchhDE-GWyV9mQcQAW9kEB2jlGmHzzZ1nL8oq_y8
```

Parameter

|Name|Type|Description|Required|Example|
|:---:|:---:|---|---|---|
|<c-red>userToken|String|고객 식별 토큰|O|"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjI3MDQyODh9.ZdYP5rb54FYKM9FS_56m9ymXZOTRnt126zd5IuIv8m0"|
|<c-red>requestUID|String|각 고객사 앱에서 전송하는 유니크한 값|O|"requestUID_example_000001"|
|date|String|고객사에서 전달한 date 정보|O|"2021-05-21T07:17:15.653Z"|
|value|String|고객사에서 사용자가 사용한 금액|O|"1"|
|currency|String|통화 화폐|X|"KRW"|
|type|String|사용자의 이벤트 타입|O|"transfer" or "signup"...|
|territory|String|국가 지역 코드|X|"KR"|


<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Response</strong>
</div>

<c-red>channel_name : channel Object에 속한 name의 의미 (하단 Sample Resonse 참조)</c-red>

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|Int|Asset ID|20|
|createdAt|String|생성 시각|"2021-05-21T07:17:15.653Z"|
|updatedAt|String|업데이트 시각|"2021-05-21T07:17:15.653Z"|
|balance|String|리워드 잔고|"10000"|
|chain_name|String|체인명|"Ethereum"|
|tokenSpec_name|String|토큰명|"tokenSpec_name"|
|tokenSpec_symbol|String|토큰 심볼|"ETH"|
|tokenSpec_decimal|String|토큰 데시멀|"10"|


Error Message

|error_code|error_description	|Description|
|---|---|---|
|401|error: 'Authorization failed!' or error: 'API Token is not match!'|인증이 실패했거나 API토큰이 불일치할 경우|
|500|error|error 내용|

<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Sample</strong>
</div>

Sample Call:

  ```javascript
POST https://api.alock.io/v1/reward HTTP/1.1
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
Sample Response:

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
  "balance": "12005",
  "chain": {
    "name": "Ethereum"
  },
  "tokenSpec": {
    "name": "Ethereum",
    "symbol": "ETH",
    "decimals": "10"
  }
}

  ```

  <a href="#" class="btn--success">처음으로</a>

------














<api-title id="accounts">accounts</api-title>
Returns json data about a account list.

<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Request</strong>
</div>

URL
```
POST /v1/accounts HTTP/1.1
Host: https://api.alock.io
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOjEsImlhdCI6MTYyMTgzNDQxN30.crpvk76sgQgIjEp5z_Ei3YXLYqWC-Chnpm31mRYNGWw
```

Parameter

|Name|Type|Description|Required|Example|
|:---:|:---:|---|---|---|
|<c-red>userToken|String|암호화된 계정값|O|"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjI3MDQyODh9.ZdYP5rb54FYKM9FS_56m9ymXZOTRnt126zd5IuIv8m0"|
|<c-red>safeAccount|String|에이락 월렛 주소|X|"0x332a1d47bfcdbe0ad43dc16d5b3172bbc8c31d0b"|

고객사 API Token을 통해 호출 시, userToken 값이 요구되며,
지갑 API Token을 통해 호출 시, safeAccount 값이 요구됩니다.


<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Response</strong>
</div>

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|Int|DB상의 사용자 id|20|
|createdAt|String|생성 시각|"2021-05-21T07:17:15.653Z"|
|updatedAt|String|업데이트 시각|"2021-05-21T07:17:15.653Z"|
|customerUID|String|고객사의 고객 고유 번호|"customerUID_001"|
|elements|List\<assets>|해당 고객의 asset 리스트|하단 참조|

assets

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|int|사용자 asset id|1|
|createdAt|String|생성 시각|"2021-05-21T07:17:15.653Z"|
|updatedAt|String|업데이트 시각|"2021-05-21T07:17:15.653Z"|
|elements|\<chain>|해당 고객의 체인|하단 참조|

chain

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|int|사용자 chain id|1|
|createdAt|String|생성 시각|"2021-05-21T07:17:15.653Z"|
|updatedAt|String|업데이트 시각|"2021-05-21T07:17:15.653Z"|
|name|String|체인 이름|"Ethereum"|
|info|String|체인 정보|"something info..."|


Error Message

|error_code|error_description	|Description|
|---|---|---|
|401|error: 'Authorization failed!' or error: 'API Token is not match!'|인증이 실패했거나 API토큰이 불일치할 경우|
|500|error|error 내용|

<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Sample</strong>
</div>

Sample Call:

  ```javascript
POST https://api.alock.io/v1/accounts HTTP/1.1
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOjEsImlhdCI6MTYyMTgzNDQxN30.crpvk76sgQgIjEp5z_Ei3YXLYqWC-Chnpm31mRYNGWw

{
  "safeAccount": "0x332a1d47bfcdbe0ad43dc16d5b3172bbc8c31d0b",
  "userToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjI3MDQyODh9.ZdYP5rb54FYKM9FS_56m9ymXZOTRnt126zd5IuIv8m0"
}
  ```

Sample Response:

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
  "id": 7,
  "createdAt": "2021-06-09T08:38:28.048Z",
  "updatedAt": null,
  "customerUID": "customerUID_001",
  "assets": [
    {
      "id": 3,
      "createdAt": "2021-06-09T08:40:36.424Z",
      "updatedAt": null,
      "chain": {
        "id": 1,
        "createdAt": "2021-06-09T01:05:07.518Z",
        "updatedAt": null,
        "name": "Ethereum",
        "info": null
      }
    }
  ]
}


  ```

  <a href="#" class="btn--success">처음으로</a>

------












<api-title id="rewards">rewards</api-title>
Returns json data about a Customer's rewards.

<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Request</strong>
</div>

URL
```
POST /v1/rewards HTTP/1.1
Host: https://api.alock.io
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjb21wYW55SWQiOjEsImlhdCI6MTYyMjc4MTIwNX0.1DBH3PeicySHdw7fZBeig4MnLoIglcd2INmgvoudWYw
```

Parameter

|Name|Type|Description|Required|Example|
|:---:|:---:|---|---|---|
|<c-red>userToken|String|고객 식별 토큰|O|"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjI3MDQyODh9.ZdYP5rb54FYKM9FS_56m9ymXZOTRnt126zd5IuIv8m0"|
|<c-red>safeAccount|String|에이락 월렛 주소|X|"0x332a1d47bfcdbe0ad43dc16d5b3172bbc8c31d0b"|
|type|String|사용자의 이벤트 타입. 값이 없으면 전체 조회, 값이 있으면 해당하는 데이터만 조회|X|"transfer" or "signup"...|
|tokenSpecId|Int|해당 사용자에게 할당된 토큰. 값이 없으면 전체 조회, 값이 있으면 해당하는 데이터만 조회|X|1 or 2...|

고객사 API Token을 통해 호출 시, userToken 값이 요구되며,
지갑 API Token을 통해 호출 시, safeAccount 값이 요구됩니다.


<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Response</strong>
</div>

<c-red>channel_name : channel Object에 속한 name의 의미 (하단 Sample Resonse 참조)</c-red>

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
|channel_id|Int|고객사id|1|
|channel_name|String|고객사명|"고객사0001"|
|channel_info|String|고객사 정보|"고객사_info"|
|chain_name|String|체인명|"Ethereum"|
|tokenSpec_name|String|토큰명|"tokenSpec_name"|
|tokenSpec_symbol|String|토큰 심볼|"ETH"|
|tokenSpec_decimal|String|토큰 데시멀|"10"|
|asset_balance|String|리워드 잔고|"50000"|

Error Message

|error_code|error_description	|Description|
|---|---|---|
|401|error: 'Authorization failed!' or error: 'API Token is not match!'|인증이 실패했거나 API토큰이 불일치할 경우|
|500|error|error 내용|

<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Sample</strong>
</div>

Sample Call:

  ```javascript
POST https://api.alock.io/v1/rewards HTTP/1.1
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjb21wYW55SWQiOjEsImlhdCI6MTYyMjc4MTIwNX0.1DBH3PeicySHdw7fZBeig4MnLoIglcd2INmgvoudWYw

{
  "userToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjMwNDUzOTR9.M0kAkn0ge8kwWhs5m4OaeLhYEnAt6Tm78_Y3aB22QXg",
  "safeAccount":"에이락 앱에서 전달_Unique00801",
  "type": "transfer"
}
  ```

Sample Response:

  ```javascript
HTTP/1.1 200 OK
X-Powered-By: Express
Access-Control-Allow-Origin: *
Content-Type: application/json; charset=utf-8
Content-Length: 6575
ETag: W/"19af-Etl1Ko1A5IhedVICofAyumYc3x8"
Date: Tue, 08 Jun 2021 08:21:05 GMT
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
    "channel": {
      "id": 1,
      "name": "고객사_01",
      "info": "CO1"
    },
    "chain": {
      "id": 1,
      "name": "Ethereum",
      "info": null
    },
    "tokenSpec": {
      "id": 1,
      "name": "Ethereum",
      "symbol": "ETH",
      "decimals": "10"
    },
    "asset": {
      "id": 2,
      "balance": "12005"
    }
  },
  {
    "id": 13,
    "createdAt": "2021-06-07T06:51:59.565Z",
    "updatedAt": null,
    "requestUID": "고객사앱에서 전송_Unique_000001001",
    "date": "date_test_00001",
    "type": "transfer",
    "value": "1000",
    "currency": "KRW",
    "territory": "KR",
    "amount": "1000",
    "status": "reward",
    "channel": {
      "id": 1,
      "name": "고객사_01",
      "info": "CO1"
    },
    "chain": {
      "id": 1,
      "name": "Ethereum",
      "info": null
    },
    "tokenSpec": {
      "id": 1,
      "name": "Ethereum",
      "symbol": "ETH",
      "decimals": "10"
    },
    "asset": {
      "id": 2,
      "balance": "12005"
    }
  },
  {
    "id": 23,
    "createdAt": "2021-06-08T07:01:45.049Z",
    "updatedAt": null,
    "requestUID": "고객사앱에서 전송_Unique_10000100102",
    "date": "date_test_00001",
    "type": "transfer",
    "value": "1000",
    "currency": "KRW",
    "territory": "KR",
    "amount": "1000",
    "status": "reward",
    "channel": {
      "id": 1,
      "name": "고객사_01",
      "info": "CO1"
    },
    "chain": {
      "id": 1,
      "name": "Ethereum",
      "info": null
    },
    "tokenSpec": {
      "id": 1,
      "name": "Ethereum",
      "symbol": "ETH",
      "decimals": "10"
    },
    "asset": {
      "id": 2,
      "balance": "12005"
    }
  }
]


  ```

  <a href="#" class="btn--success">처음으로</a>

------






















<api-title id="assets">assets</api-title>

  Returns json data about a asset list.

<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Request</strong>
</div>

URL
```
POST /v1/assets HTTP/1.1
Host: https://api.alock.io
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOjEsImlhdCI6MTYyMTgzNDQxN30.crpvk76sgQgIjEp5z_Ei3YXLYqWC-Chnpm31mRYNGWw
```

Parameter

|Name|Type|Description|Required|Example|
|:---:|:---:|---|---|---|
|<c-red>userToken|String|암호화된 계정값|O|"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjI3MDQyODh9.ZdYP5rb54FYKM9FS_56m9ymXZOTRnt126zd5IuIv8m0"|
|<c-red>safeAccount|String|에이락 월렛 주소|X|"0x332a1d47bfcdbe0ad43dc16d5b3172bbc8c31d0b"|

고객사 API Token을 통해 호출 시, userToken 값이 요구되며,
지갑 API Token을 통해 호출 시, safeAccount 값이 요구됩니다.


<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Response</strong>
</div>

<c-red>channel_name : channel Object에 속한 name의 의미 (하단 Sample Resonse 참조)</c-red>

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|Int|DB상의 사용자 id|20|
|createdAt|String|생성 시각|"2021-05-21T07:17:15.653Z"|
|updatedAt|String|업데이트 시각|"2021-05-21T07:17:15.653Z"|
|customerUID|String|고객사의 고객 고유 번호|"customerUID_001"|
|elements|List\<assets>|해당 고객의 asset 리스트|하단 참조|

assets

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|int|사용자 asset id|1|
|balance|String|리워드 잔고|"50000"|
|chain_id|int|사용자 chain id|1|
|chain_name|String|chain name|"Ethereum"|
|chain_info|String|체인 정보|"something info..."|
|tokenSpec_id|int|사용자 tokenSpec id|1|
|tokenSpec_name|String|토큰명|"tokenSpec_name"|
|tokenSpec_symbol|String|토큰 심볼|"ETH"|
|tokenSpec_decimal|String|토큰 데시멀|"10"|
|tokenSpec_info|String|토큰 스펙 정보|"something info..."|

Error Message

|error_code|error_description	|Description|
|---|---|---|
|401|error: 'Authorization failed!' or error: 'API Token is not match!'|인증이 실패했거나 API토큰이 불일치할 경우|
|500|error|error 내용|

<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Sample</strong>
</div>

Sample Call:

  ```javascript
POST https://api.alock.io/v1/assets HTTP/1.1
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOjEsImlhdCI6MTYyMTgzNDQxN30.crpvk76sgQgIjEp5z_Ei3YXLYqWC-Chnpm31mRYNGWw

{
  "safeAccount": "0x332a1d47bfcdbe0ad43dc16d5b3172bbc8c31d0b",
  "userToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjI3MDQyODh9.ZdYP5rb54FYKM9FS_56m9ymXZOTRnt126zd5IuIv8m0"
}
  ```

Sample Response:

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

  <a href="#" class="btn--success">처음으로</a>

------


















**아래 내용은 에이락 내부용입니다.**
------








<api-title id="customers">customers</api-title>
Returns json data about a Customers list included in the wallet .

<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Request</strong>
</div>

URL
```
POST /v1/customers HTTP/1.1
Host: https://api.alock.io
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjb21wYW55SWQiOjEsImlhdCI6MTYyMjc4MTIwNX0.1DBH3PeicySHdw7fZBeig4MnLoIglcd2INmgvoudWYw
```

Parameter

|Name|Type|Description|Required|Example|
|:---:|:---:|---|---|---|
|walletUID|String|지갑 UID|O|"walletUID_00000001"|


<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Response</strong>
</div>

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|Int|DB상의 지갑 id|20|
|walletUID|String|지갑 UID|O|"walletUID_00000001"|
|email|String|지갑 email|"test1@test.co.kr"|
|name|String|지갑 name|"테스터"|
|info|String|사용자 정보|"information"|
|elements|List\<customers>|해당 wallet의 customer 리스트|하단 참조|

customers

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|Int|customer id|1|
|customerUID|String|고객사의 고객 고유 번호|"customerUID_001"|
|channel_id|Int|고객사id|1|
|channel_name|String|고객사 명|"고객사0001"|
|channel_info|String|고객사 정보|"information"|
|assets_id|Int|asset id|1|
|safeAccount|String|에이락 월렛 주소|"0x332a1d47bfcdbe0ad43dc16d5b3172bbc8c31d0b"|
|keyIndex|Index|에이락 월렛 주소 생성 시 사용된 인덱스 값|1|


Error Message

|error_code|error_description	|Description|
|---|---|---|
|401|error: 'Authorization failed!' or error: 'API Token is not match!'|인증이 실패했거나 API토큰이 불일치할 경우|
|500|error|error 내용|

<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Sample</strong>
</div>

Sample Call:

  ```javascript
POST https://api.alock.io/v1/customers HTTP/1.1
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjb21wYW55SWQiOjEsImlhdCI6MTYyMjc4MTIwNX0.1DBH3PeicySHdw7fZBeig4MnLoIglcd2INmgvoudWYw

{
  "walletUID": "Tester01"
}
  ```

Sample Response:

  ```javascript
HTTP/1.1 200 OK
X-Powered-By: Express
Access-Control-Allow-Origin: *
Content-Type: application/json; charset=utf-8
Content-Length: 367
ETag: W/"16f-UEWSrMs2VaT233OKUTDuEguBg4o"
Date: Tue, 08 Jun 2021 09:12:25 GMT
Connection: close

{
  "id": 115,
  "walletUID": "walletUID00411000000012",
  "email": "test@a-fun.co.kr",
  "name": "김고객",
  "info": "info001",
  "customers": [
    {
      "id": 104,
      "customerUID": "customerUID_00100015",
      "safeAccount": "Unique000701112434",
      "keyIndex": 0,
      "channel": {
        "id": 1,
        "name": "고객사_01",
        "info": "CO1",
        "customURLScheme": "https://afunuser.page.link/token"
      },
      "assets": []
    },
    {
      "id": 167,
      "customerUID": "customerUID_0010001580002",
      "safeAccount": "Unique0007011124320",
      "keyIndex": 1,
      "channel": {
        "id": 1,
        "name": "고객사_01",
        "info": "CO1",
        "customURLScheme": "https://afunuser.page.link/token"
      },
      "assets": [
        {
          "id": 3
        },
        {
          "id": 15
        }
      ]
    }
  ]
}

  ```

  <a href="#" class="btn--success">처음으로</a>

------














<api-title id="wallet">wallet</api-title>
Returns json data about a wallet info.

<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Request</strong>
</div>

URL
```
POST /v1/wallet HTTP/1.1
Host: https://api.alock.io
content-type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjb21wYW55SWQiOjEsImlhdCI6MTYyMjcwNDQyN30.qpq_UF2ebwr2IcEtvsPaS8TMU0tVCWz3B3r_7p32MVQ
```
<span style="color:red; font-size : 14px">**Authorization: Bearer {지갑 AccessToken}</span>

Parameter

|Name|Type|Description|Required|Example|
|:---:|:---:|---|---|---|
|<c-red>userToken|String|고객 식별 토큰|O|"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjI3MDQyODh9.ZdYP5rb54FYKM9FS_56m9ymXZOTRnt126zd5IuIv8m0"|
|<c-red>safeAccount|String|에이락 월렛 주소|O|"0x332a1d47bfcdbe0ad43dc16d5b3172bbc8c31d0b"|
|<c-red>keyIndex|Int|에이락 월렛 주소 생성 시 사용된 인덱스 값|O|1|
|<c-red>publicKey|String|에이락 월렛 퍼블릭키|O|"tempPublicKey1622427282147"|
|walletUID|String|지갑 UID|O|"walletUID_00000001"|
|email|String|사용자 email|X|"test1@test.co.kr"|
|name|String|wallet 사용자 이름|X|"홍길동"|
|info|String|사용자 정보|X|"info001"|
|deviceType|String|기기 타입|O|"deviceType0001"|
|deviceId|String|기기 id(푸시 알림용)|O|"deviceId0001"|


<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Response</strong>
</div>

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|Int|지갑 id|1|
|customerUID|String|고객사의 고객 고유 번호|"customerUID_001"|
|wallet_name|Int|wallet id|"wallet_name001"|
|wallet_info|Int|wallet 정보|"wallet_information"|
|channel_name|String|고객사 명|"고객사0001"|
|channel_info|String|고객사 정보|"information"|
|elements|List\<assets>|해당 고객의 asset 리스트|하단 참조|

assets

|Name|Type|Description|Example|
|:---:|:---:|---|---|
|id|int|사용자 asset id|1|
|balance|String|리워드 잔고|"50000"|
|chain_name|String|체인명|"Ethereum"|
|chain_info|String|체인 정보|"Ethereum"|
|tokenSpec_name|String|토큰명|"tokenSpec_name"|
|tokenSpec_symbol|String|토큰 심볼|"ETH"|
|tokenSpec_decimal|String|토큰 데시멀|"10"|
|tokenSpec_info|String|토큰 스펙 정보|"10"|

Error Message

|error_code|error_description	|Description|
|---|---|---|
|401|error: 'Authorization failed!' or error: 'API Token is not match!'|인증이 실패했거나 API토큰이 불일치할 경우|
|500|error|error 내용|

<div class="arrow">
  <img src="./arrow_16px.png" alt=" > ">
  <strong style="font-size:20px">Sample</strong>
</div>

Sample Call:

  ```javascript
  POST https://api.alock.io/v1/asset HTTP/1.1
  content-type: application/json
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOjEsImlhdCI6MTYyMTUwMDc0OH0.Vf-GchhDE-GWyV9mQcQAW9kEB2jlGmHzzZ1nL8oq_y8

  {
    "userToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGFubmVsSWQiOiIxIiwiY3VzdG9tZXJVSUQiOiJjdXN0b21lclVJRF8wMDEiLCJpYXQiOjE2MjI3MDQyODh9.ZdYP5rb54FYKM9FS_56m9ymXZOTRnt126zd5IuIv8m0",
    "safeAccount": "에이락 앱에서 전달",
    "keyIndex": 1,
    "publicKey": "에이락 앱에서 전달",
    "walletUID": "deviceType00001",
    "email": "test1@test.co.kr",
    "name": "test001",
    "info": "info001",
    "deviceType": "deviceType0001",
    "deviceId": "deviceId0001"
  }

  ```
Sample Response:

  ```javascript
HTTP/1.1 200 OK
X-Powered-By: Express
Access-Control-Allow-Origin: *
Content-Type: application/json; charset=utf-8
Content-Length: 513
ETag: W/"201-v1TQIeNs/J4Br85HvSaLpZkWVGc"
Date: Tue, 08 Jun 2021 09:33:53 GMT
Connection: close

{
  "customerUID": "customerUID_001",
  "wallet": {
    "name": "테스터",
    "info": ""
  },
  "channel": {
    "name": "고객사_01",
    "info": "CO1"
  },
  "assets": [
    {
      "id": 2,
      "balance": "12005",
      "chain": {
        "name": "Ethereum",
        "info": null
      },
      "tokenSpec": {
        "name": "Ethereum",
        "symbol": "ETH",
        "decimals": "10",
        "info": null
      }
    },
    {
      "id": 4,
      "balance": "0",
      "chain": {
        "name": "Ethereum",
        "info": null
      },
      "tokenSpec": {
        "name": "Ethereum",
        "symbol": "ETH",
        "decimals": "10",
        "info": null
      }
    }
  ]
}

  ```

  <a href="#" class="btn--success">처음으로</a>

------

