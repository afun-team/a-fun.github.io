<style>
    h1 { display: none }
    h2 { font-size: 2em !important }
c-red { color: red }
</style>

<h2 id="-에이락-리워드-플랫폼-api">🚀 에이락 리워드 플랫폼 API</h2>

에이락 리워드 플랫폼은 고객사의 고객에게 암호화폐 리워드를 제공하기 위하여 구축된 서비스 플랫폼입니다. 이 문서에서는 고객사와 에이락 월렛이 각각 에이락 리워드 플랫폼 API 서버와 연동하기 위하여 필요한 정보를 제공합니다.

<br/>

📡 시스템 연동 프로세스

![alt 'A-Fun Blockchain Platform-System Process'](images/A-FunBlockchainPlatform-SystemProcess.png)

<br/>

👩‍💻 연동 절차를 요약하면 아래와 같습니다.

1. 고객사 등록 - 고객사 정보와 계약 내용 등과 통신에 필요한 정보를 사전에 등록
2. 고객 등록 - 고객사의 고객을 에이락 리워드 플랫폼에 등록
3. 에이락 월렛 설치 - 고객이 자신의 스마트폰에 에이락 월렛을 설치하고 본인 인증/ 회원 가입
4. 고객사에서 고객에게 리워드 지급 요청
5. 고객사에서 고객에게 지급된 리워드 조회
6. 에이락 월렛에서 고객에게 지급된 리워드 조회

<br/>

✅ 에이락 리워드 플랫폼과 연동하기 위하여 사전에 준비하여야 하는 사항은 아래와 같습니다.

1. 고객사 accessToken <c-red>- 에이락에서 고객사에 전달</c-red>
2. 고객 등록 여부를 고객사에 전달한 callback URL
3. 고객사 앱의 custom URL scheme 또는 deep link 등(선택 사항)

   <br/>

🔗 에이락 리워드 플랫폼의 API <c-red>개발</c-red>서버의 URL은 다음과 같습니다.

```jsx
https://dev.alock.io/v1/{api-url}
```

- 고객 등록/리워드 지급 요청 API는 POST 방식만을 사용합니다.
- 항상 요청 프로토콜의 header에 Authorization 항목에 access의 토큰이 들어있어야 합니다.
- 요청에 필요한 parameter는 json 방식을 사용합니다.

<br/>

🔗 에이락 리워드 플랫폼의 API 서버의 URL은 다음과 같습니다.

```jsx
https://api.alock.io/v1/{api-url}
```

- 고객 등록/리워드 지급 요청 API는 POST 방식만을 사용합니다.
- 항상 요청 프로토콜의 header에 Authorization 항목에 고객사의 토큰이 들어있어야 합니다.
- 요청에 필요한 parameter는 json 방식을 사용합니다.

<br/>
<h2 id="api-용어">API 용어 정리</h2>

📌 에이락 API와 관련된 용어가 다양한 의미로 사용되고 있어 에이락 API를 처음 접하는 개발자나 기존의 개발자에게 혼란을 주기도 합니다. 여기서는 에이락 API를 사용하는 개발자가 혼란을 느끼지 않게 관련 용어들을 정확하게 정의해 정리했습니다.

<br/>

1. **reward**
   ```jsx
   (주)에이락의 ‘블록체인 리워드 서비스’의 고객사 회원들에게 제공되는 가상자산 입니다.
   ```
2. **channel( 고객사 )**
   ```jsx
   (주)에이락의 가상자산 리워드 서비스를 제공하는 제휴사를 지칭합니다.
   ```
3. **company**
   ```jsx
   (주)에이락을 지칭합니다.
   ```
4. **chain**
   ```jsx
   리워드를 제공하는 블록체인 업체를 지칭합니다.
   ```
5. **wallet**
   ```jsx
   에이락 월렛 고객의 리워드 자산을 보관하고 있는 지갑입니다.
   ```
6. **asset**
   ```jsx
   에이락 월렛 고객이 지급받은 리워드 자산의 집합입니다.
   보유 중인 리워드의 정보와 블록체인 네트워크, 종류 및 수량을 포함합니다.
   ```
7. **tokenSpec**
   ```jsx
   리워드로 지급되는 가상자산의 정보입니다.
   ```
8. **account**
   ```jsx
   고객이 보유하고 있는 리워드에 대한 블록체인 네트워크 정보입니다.
   asset 정보를 포함하고 있으며 asset의 상위 개념입니다.
   ```
9. **userToken**
   ```jsx
   고객사 정보와 고객의 정보를 암호화한 고객 식별 토큰입니다.
   ```
10. **safeAccount**
    ```jsx
    wallet API 호출 시 등록되는 지갑 주소입니다.
    ```
11. **requestUID**
    ```jsx
    각 고객사 앱에서 전송하는 유니크 값입니다.
    ```
12. **customerUID**
    ```jsx
    각 고객사 앱에서 전송하는 고객 식별 고유 번호 입니다.
    ```

<h2 id="api-개요">API 개요</h2>

📌 API 목록 및 개략적인 내용은 다음과 같습니다.

<br/>

1. **고객 정보 등록**

   ```jsx
   고객사에서 전달받은 고객의 고유한 아이디 값을 받아 저장하고 고객 식별 토큰을 생성하여 반환합니다.
   고객 식별 토큰에서는 고객사 정보와 고객 정보가 들어 있습니다.
   고객사에 등록된 정보와 고객의 정보가 다르면 에이락 월렛에서 별개의 계좌가 발급되고 집계됩니다.
   ```

   - URL : /customer
   - Header
     - 고객사 API 토큰(channelAccessToken)
   - Request
     - 고객 고유 아이디(customerUID)
   - Response
     - 고객 식별 토큰(userToken)
     - 에이락 월렛 설치 여부(installed)

<br/>

2. **고객 지갑 호출**

   ```jsx
   고객사 앱에서 고객 식별 토큰을 넣어 Firebase Dynamic Link를 이용해 에이락 월렛을 호출합니다.
   에이락 월렛을 설치하지 않았다면 스토어를 호출하고, 설치가 되어 있다면 에이락 월렛을 호출합니다.
   ```

   - Firebase Dynamic Link : https://afun.page.link/?link=https://afun.page.link/?userToken%3D{userToken}&apn=com.wallets.afun
   - Request:
     - 고객 식별 토큰(UserToken)
   - Response
     - N/A

<br/>

3. **고객 지갑 등록 - 에이락 월렛 내부에서만 사용하는 API 입니다.**

   ```jsx
   고객 식별 토큰을 등록하고,고객의 지갑 주소와 공개키, deviceId, deviceType을 저장합니다.
   고객 지갑이 생성되면 고객사의 callback URL로 고객 등록 여부를 전송합니다.
   ```

   - URL: /wallet
   - Header
     - 지갑APP API 토큰(companyAccessToken)
   - Request
     - 고객 식별 토큰(userToken)
     - 고객 지갑 주소(safeAccount)
     - 고객 공개키 정보(publicKey)
     - 지갑 고유 번호(walletUID)
     - 지갑 고객 정보
     - deviceType
     - deviceId
   - Response
     - 고객 등록 정보

<br/>

4. **리워드 지급 요청**

   ```jsx
   고객 식별 토큰과 거래정보를 받아 고객사와 계약되어 있는 리워드를 고객에게 지급하고 리워드 지급 내역을 반환합니다.
   ```

   - URL: /reward
   - Header
     - 고객사 API 토큰(channelAccessToken)
   - Request
     - 고객 식별 토큰(userToken)
     - 각 고객사 앱에서 전송하는 유니크 값(requestUID)
     - 거래 종류(type) <c-red> - 에이락에서 고객사에 전달</c-red>
     - 거래 금액(value)
     - 고객사에서 전달한 정보(data)
     - 통화 화폐(currency)
     - 국가 지역 코드(territory)
   - Response
     - 리워드 지급 내역(rewards)

<br/>

5. **자산 내역 요청**

   ```jsx
   고객사의 고객이 리워드로 받아서 보유하고 있는 자산의 목록을 반환합니다.
   암호화폐의 네트워크/화폐종류에 따라 분류하여 각각의 잔고 목록을 반환합니다.
   ```

   **고객사 API 토큰 호출 시**

   - URL: /assets
   - Header
     - 고객사 API 토큰(channelAccessToken)
   - Request
     - 고객 식별 토큰(userToken)
   - Response
     - 리워드 잔고 내역(assets)

   **지갑 API 토큰 호출 시**

   - URL: /assets
   - Header
     - 지갑 앱 API 토큰(companyAccessToken)
   - Request
     - 고객 지갑 주소(safeAccount)
   - Response
     - 리워드 잔고 내역(assets)

<br/>

6. **리워드 지급 내역 요청**

   ```jsx
   고객 식별 토큰을 고객에게 지급된 리워드 내역 전체를 반환합니다.
   auth를 channel accessToken으로 사용 시 고객 식별 토큰이 필요하고,
   company accessToken 으로 사용 시 safeAccount가 필요합니다.

   1000건 단위 페이지 또는 리워드 지급 일자, 암호화폐 종류 등에 따라 분류하여 반환하는 기능을 추후 추가할 예정입니다.
   ```

   **고객사 API 토큰 호출 시**

   - URL: /rewards
   - Header
     - 고객사 API 토큰(channelAccessToken)
   - Request
     - 고객 식별 토큰(UserToken)
   - Response
     - 리워드 지급 내역(rewards)

   **지갑 API 토큰 호출 시**

   - URL: /rewards
   - Header
     - 지갑APP API 토큰(companyAccessToken)
   - Request
     - 고객 지갑 주소(safeAccount)
   - Response
     - 리워드 지급 내역(rewards)

<br/>

7. **리워드 지급 상세 내역 요청**

   ```jsx
   리워드 한 건에 대한 상세 내역을 조회하여 반환합니다.
   ```

   - URL: /rewards/{reward.id}
   - Header
     - 고객사 API 토큰(channelAccessToken)
   - Request
     - 리워드 지급 내역 id
   - Response
     - 리워드 상세 내역(rewards)

<br/>

8. **출금 요청 - 에이락 월렛 내부에서만 사용하는 API 입니다.**

   ```jsx
   고객이 보유하고 있던 리워드를 다른 지갑으로 송금을 요청합니다.
   송금 요청은 관리자의 승인을 거쳐 실제 블록체인 네트워크에서 조회하여 결과를 반환합니다.
   ```

   - URL: /transfer
   - Header
     - 지갑APP API 토큰(companyAccessToken)
   - Request
     - 고객 지갑 주소(safeAccount)
     - 암호화된 출금 요청 정보
   - Response
     - 출금 상세 내역(transfers)

<br/>

9. **출금 내역 요청**

   ```jsx
   고객이 요청한 출금 내역을 반환합니다.
   ```

   - URL: /transfers
   - Header
     - 고객사 API 토큰(channelAccessToken)
       or
     - 지갑APP API 토큰(companyAccessToken)
   - Request
     - 고객 식별 토큰(userToken)
       or
     - 고객 지갑 주소(safeAccount)
   - Response
     - 출금 상세 내역(transfers)

<br/>

10. **출금 상세 내역 요청**

    ```jsx
    고객이 요청한 출금 내역 한건에 대하여 상세 내역을 반환합니다.
    ```

    - URL: /transfers/{transfer.id}
    - Header
      - 지갑APP API 토큰(companyAccessToken)
    - Request
      - 고객 식별 토큰(UserToken)
      - 출금 상세 내역 id
    - Response
      - 출금 상세 내역(transfers)

<br/>

<h2 id="api-상세-내역">API 상세 내역</h2>

[https://docs.alock.io/api-spec](api-spec.md)
