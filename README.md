
# [Uznex API Document for Developer]
&nbsp;

### [API Info]

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Uznex는 개발자를 위해 API를 제공하여 다양한 앱과 프로그램을 개발할 수 있는 환경을 제공합니다.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;이제 누구나 쉽게 비트레이드에서 제공되는 API를 통하여

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;사용자 정보, 지갑정보, 주문, 거래 내역, 거래 취소 등의 기능을 사용할 수 있습니다.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;또한 지갑 API를 제공하여 암호화폐 유관 서비스를 구축하는데 도움을 드립니다.


### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Go to API Key creation](https://www.uznex.com/mypage/mypage.do) (You can create API Key at 'Mypage' in Uznex.)


&nbsp;

---
&nbsp;
### [API 공지]
#### Open API  변경사항 안내
##### &nbsp;&nbsp;&nbsp; <Open API 변경사항>

&nbsp;&nbsp;&nbsp;기존 거래소 마지막 거래 정보 API(Ticker)가 Deprecated 되고, 마켓 정보가 제공되는 Ticker가 추가 되었습니다.<br/>&nbsp;&nbsp;&nbsp;기존 거래소 마지막 거래 정보 API는 Ticker1을, 추가된 API는 Ticker2를 참고 바랍니다.

&nbsp;

---

&nbsp;

### [INDEX]
### 1. Public API
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1-1. Ticker&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - last tradging information on the exchange <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1-2. Orderbook&nbsp; - 
Exchange sale / Buy registration standing by or trading details <br/>
### 2. Token
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2-1. Create&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - Creation the initial Token <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2-2. Refresh&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - Update Token <br/>
### 3. Private API
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3-1. Account &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Member information search <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3-2. Balance &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Member wallet information <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3-3. Transaction - Member trading history <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3-4. Cancel &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Member's sell / buy trading cancel <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3-5. Place &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Member's sell / buy trading order registration and conclusion <br/>
### 4. Status
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4-1. Token Error <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4-2. Exception <br/>

&nbsp;

---
&nbsp;
### [Reference]

### 1. Public API
&nbsp;
---
#### 1-1.Ticker - last tradging information on the exchange

__[GET]__ &nbsp;&nbsp;&nbsp;```https://api.uznex.com/api/v1/ticker/currency/{coin_code}```

__[Curl]__ &nbsp;&nbsp;&nbsp;```curl -X GET --header 'Accept: application/json' 'https://api.uznex.com/api/v1/ticker/currency/{coin_code}'```

__[Response Body]__

```
{
    "status": "0000",
    "data": {
        "USD": {
            "open_price": "1000",
            "close_price": "10001000",
            "low": "1000",
            "high": "10003000",
            "average_price": "8594071.364285713",
            "units_traded": "6.014550000000000000",
            "volume_1day": "6.014550000000000000",
            "volume_7day": "30.019550000000000000",
            "buy_price": "0010001000.00000000",
            "sell_price": "0000000000.00000000",
            "date": 1564475297693
        },
        "BTC": {
            "open_price": "1.12345678",
            "close_price": "1.12345678",
            "low": "1.12345678",
            "high": "1.12345678",
            "average_price": "1.123456780000000000000000000000",
            "units_traded": "2.000000000000000000",
            "volume_1day": "2.000000000000000000",
            "volume_7day": "2.000000000000000000",
            "buy_price": "0000000001.12345678",
            "sell_price": "0000000000.00000000",
            "date": 1564475297863
        }
    }
}
```

__[Input Parameters]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|coin_code|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Market name_Coin name (USD_BTC, USD_UNB, BTC_EOS, BTC_XRP, etc.)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

__[Response]__

|&nbsp;&nbsp;&nbsp;Response Field&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|status: 0000|Normal|
|USD, BTC| Market code|
|open_price|Start trading amount within the last 24 hours|
|close_price|Last trading amount within the last 24 hours|
|low|Minimum trading amount within the last 24 hours|
|High|Maximum trading amount within the last 24 hours|
|average_price|Average trading amount within the last 24 hours|
|units_traded|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Currency trading volume in the last 24 hours&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|volume_1day|Currency trading volume in the last 1 day|
|volume_7day|Currency trading volume in the last 7 days|
|buy_price|The highest buying price on the waiting list|
|sell_price|The lowest selling price on the waiting list|
|date|Currnt time Timestamp|

&nbsp;
---

#### 1-2. Orderbook - Exchange selling / buying registration stading by or transaction details
__[GET]__ &nbsp;&nbsp;&nbsp;```https://api.uznex.com/api/orderbook/currency/{coin_code}```

__[Curl]__ &nbsp;&nbsp;&nbsp;```curl -X GET --header 'Accept: application/json' 'https://api.uznex.com/api/orderbook/currency/{coin_code}'```


__[Response Body]__
````
{
  "status": "0000",
  "data": {
    "timestamp": 1548934145839,
    "order_currency": "BTC",
    "payment_currency": "USD",
    "bids": [
      {
        "it_action": "buy",
        "it_market_cost": "0000000000.00000000",
        "nResCoin": "00000000.00000000"
      },
      {
        "it_action": "buy",
        "it_market_cost": "0000000000.00000000",
        "nResCoin": "00000000.00000000"
      }
    ],
    "asks": [
      {
        "it_action": "sell",
        "it_market_cost": "0000000000.00000000",
        "nResCoin": "00000000.00000000"
      },
      {
        "it_action": "sell",
        "it_market_cost": "0000000000.00000000",
        "nResCoin": "00000000.00000000"
      }
    ]
  }
}
````


__[Input Parameters]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|coin_code|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Maeket name_Coin name (USD_BTC, USD_UNB, BTC_EOS, BTC_XRP, etc.)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

__[Response]__

|&nbsp;&nbsp;&nbsp;Response Field&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|timestamp|Current time|
|order_currency|Coin|
|payment_currency|Payment currency|
|it_action|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[bids]: buy / [asks]: sell&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|it_market_cost|Market price|
|nResCoin|Available coin|

&nbsp;

---
&nbsp;
### 2. Token

#### 2-1. Create - Create the initial Token

__[POST]__ &nbsp;&nbsp;&nbsp;```https://api.uznex.com/api/v1/access_token```

```
{
  "nonce":"1548998552194",
  "hstr":"54c25b135d6e80129b71e399fecf522016ab528be7459b1c33c73730de67fad6",
  "apikey":"BTkYXt3hv5BxzieKxHiE9zovAsDSVXraNpJ",
  "grant_type":"APIKEY",
  "expires_in":60
}
```

__[Curl]__

```
curl -X POST --header 'Content-Type: application/json;charset=UTF-8' --header 'Accept: application/json' -d '{ \ 
   "nonce":"1548998552194", \ 
   "hstr":"54c25b135d6e80129b71e399fecf522016ab528be7459b1c33c73730de67fad6", \ 
   "apikey":"BTkYXt3hv5BxzieKxHiE9zovAsDSVXraNpJ", \ 
   "grant_type":"APIKEY", \ 
   "expires_in":60 \ 
 }' 'https://api.uznex.com/api/v1/access_token'
```

__[Response Body]__

```
{
  "status": "0000",
  "message": "success",
  "data": {
    "access_token": "fb2050d52602edd7798efff6fd7ed289a8d743a4bdda510e0aa374c50e3b2023",
    "access_token_expire": "1549002045865",
    "refresh_token": "48f9b90cee15348744b0da1a8e995c5d3833fd985d8f9dd138c04755b18731c7",
    "refresh_token_expire": "1551590445856"
  }
}
```

__[Input Parameters]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|nonce|Request Time (Unix Time)|
|hstr|sha256( apikey + secretkey + nonce ) → 
Hexadecimal conversion string|
|apikey|Member API key|
|grant_type|APIKEY|
|expires_in|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Access Token expire time (Minute Time, Minimun 30min ~ Maximun 60min)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

__[Response]__

|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Response Field&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|status| 0000: Normal / others: error|
|message|Result Message|
|access_token|Access Token for using Uznex API|
|access_token_expire|Access Token expire time (Unix Time)|
|refresh_token|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Refresh Token for updating Access Token&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|refresh_token_expire|Refresh Token expire time (Unix Time)|

&nbsp;
---

#### 2-2. Refresh - Update token

__[POST]__&nbsp;&nbsp;&nbsp;```https://api.uznex.com/api/v1/access_token```

```
{
  "refresh_token":"48f9b90cee15348744b0da1a8e995c5d3833fd985d8f9dd138c04755b18731c7", 
  "expires_in":60, 
  "grant_type":"REFRESH"
}
```

__[Curl]__

```
curl -X POST --header 'Content-Type: application/json;charset=UTF-8' --header 'Accept: application/json' -d '{ \ 
   "refresh_token": "48f9b90cee15348744b0da1a8e995c5d3833fd985d8f9dd138c04755b18731c7", \ 
   "expires_in":60, \ 
   "grant_type":"REFRESH" \ 
 }' 'https://api.uznex.com/api/v1/access_token'
```

__[Response Body]__

```
{
  "status": "0000",
  "message": "success",
  "data": {
    "access_token": "fb2050d52602edd7798efff6fd7ed289a8d743a4bdda510e0aa374c50e3b2023",
    "access_token_expire": "1549002045865",
    "refresh_token": "48f9b90cee15348744b0da1a8e995c5d3833fd985d8f9dd138c04755b18731c7",
    "refresh_token_expire": "1551590445856"
  }
}
```

__[Input Parameters]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|refresh_token|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Token Create Refresh Token created by API&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|expires_in|Access Token expire time (Minute Unit, Minimum 30min~Maximum60min)|
|grant_type|REFRESH|

__[Response]__

|&nbsp;&nbsp;&nbsp;Response Field&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|status|0000: Normal / others: error|
|message| Result message|
|access_token|Access Token for using Uznex API|
|access_token_expire|Access Token expire time (Unix Time)|
|refresh_token|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Refresh Token for updating Access Token  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|refresh_token_expire|Refresh Token expire time (Unix Time)|

&nbsp;

---
&nbsp;
### 3. Private API

#### 3-1. Account - Member information search

__[GET]__ &nbsp;&nbsp;&nbsp;```https://api.uznex.com/api/private/v1/account?currency={currency}```

__[Curl]__

```
curl -X GET --header 'Accept: application/json' --header 'Authorization: Bearer 125543745d3c2712529a579d1383e89469e3cc9601cd08f22e4dd6c482b5d7b9' 'https://api.uznex.com/api/private/v1/account?currency=BTC'
```

__[Response Body]__

```
{
  "status": "0000",
  "data": {
    "account_id": 3,
    "balance": 5532123.7132,
    "trade_fee": 0.005,
    "created": 1521439134000
  }
}
```

__[Input Header]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|Authorization|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Access Token&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

__[Input Parameters]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|currency|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Coin name (BTC, UNB, EOS, XRP, etc.)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|



__[Response]__

|&nbsp;&nbsp;&nbsp;Response Field&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|status|0000: Normal / others: error|
|account_id|User account ID|
|balance|Balance coin|
|trade_fee|Applicable fee rate|
|created|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Signed up time (Unix Time)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

&nbsp;
---
#### 3-2. Balance - Member wallet information

__[GET]__ &nbsp;&nbsp;&nbsp;```https://api.uznex.com/api/private/v1/balance?currency={currency}```

__[Curl]__

```
curl -X GET --header 'Accept: application/json' --header 'Authorization: Bearer 7488eeb56b924e369c2d60f738e795072d3e90740339dc42205f50743619cfb4' 'https://api.uznex.com/api/private/v1/balance?currency=BTC'
```

__[Response Body]__

```
{
  "status": "0000",
  "data": {
    "total_usd": 9999613666.0878,
    "in_use_usd": 7598430736.27575,
    "available_usd": 2401182929.81205,
    "total_btc": 5532121.7132,
    "in_use_btc": 8.8742,
    "available_btc": 5532112.839
  }
}
```

__[Input Header]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|Authorization|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Access Token&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

__[Input Parameters]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|currency|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Coin name (BTC, UNB, EOS, XRP, etc.)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

__[Response]__

|&nbsp;&nbsp;&nbsp;Response Field&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|status|0000: Normal / others: error|
|total_{currency}|Total coin Currency|
|in_use_{currency}|Used coin Currency|
|available_{currency}|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Available to use coin Curreny&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

&nbsp;
---

#### 3-3. Transaction - Member trading history

__[GET]__ 

```
https://api.uznex.com/api/private/v1/transaction?currency={currency}&deal_status={deal_status}&trd_state={trd_state}
```

__[Curl]__

```
curl -X GET --header 'Accept: application/json' --header 'Authorization: Bearer 7488eeb56b924e369c2d60f738e795072d3e90740339dc42205f50743619cfb4' 'https://api.uznex.com/api/private/v1/transaction?currency=BTC&deal_status=0&trd_state=OK'
```

__[Response Body]__

```
{
  "status": "0000",
  "data": [
    {
      "search": 0,
      "orderId": "1901251726297700000003",
      "price": 3905.5,
      "trd_state": "OK",
      "fee": 0.0015,
      "trd_type": "BUY",
      "units": 0.001,
      "transfer_date": 1548404789817,
      "btc1usd": 3905500
    },
    {
      "search": 0,
      "orderId": "1901151956097700000003",
      "price": 41636.34,
      "trd_state": "OK",
      "fee": 0.005,
      "trd_type": "SELL",
      "units": 0.01019,
      "transfer_date": 1547549769770,
      "btc1usd": 4086000
    },
    {
      "search": 0,
      "orderId": "1901151956026220000003",
      "price": 44828.905,
      "trd_state": "OK",
      "fee": 0.005,
      "trd_type": "SELL",
      "units": 0.01097,
      "transfer_date": 1547549762618,
      "btc1usd": 4086500
    },
    ...
```

__[Input Header]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|Authorization|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Access Token&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|


__[Input Parameters]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|currency|Market name_Coin name (USD_BTC, USD_UNB, BTC_EOS, BTC_XRP, etc.)|
|deal_status|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Status - 0(Total), 1(Buying), 2(Selling), 3(Cancel), 4(Normal)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|trd_status|Order status - OK, WAIT|

__[Response]__

|&nbsp;&nbsp;&nbsp;Response Field&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|status|0000: Normal / others: error|
|search|One of 0(Total), 1(Buying), 2(Selling), 3(Deposit), 4(Withdraw)|
|orderId|Order number|
|price|Trading amount|
|trd_state|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Order status (OK:
Completed the conclusion, WAIT:Waiting for conclusion)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|fee|Trading fee|
|trd_type|Status (BUY:Buying, SELL:Selling, C:Cancel, M:Correction)|
|units|Trading Currency volume|
|transfer_date|Date of trading|
|{currency}1usd|Current market price|

&nbsp;
---
#### 3-4. Cancel - Member selling / buying trading cancel

__[POST]__&nbsp;&nbsp;&nbsp;``https://api.uznex.com/api/private/v1/order/cancel``

```
{
  "currency" : "USD_BTC",
  "org_ord_no" : "190208154943577"
}
```

__[Curl]__

```
curl -X POST --header 'Content-Type: application/json;charset=UTF-8' --header 'Accept: application/json' --header 'Authorization: Bearer 7603c80ddcd596c6fffb642e44470b9cea0d79e2e67a7b9de9ff5b957d46c1c7' -d '{ \ 
   "currency" : "USD_BTC", \ 
   "org_ord_no" : "190208154943577" \ 
 }' 'https://api.uznex.com/api/private/v1/order/cancel'
``` 

__[Response Body]__

```
{
  "status": "0000",
  "data": "Success"
}
```

__[Input Header]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|Authorization|Access Token|
|Content-Type|The Content-Type entity header is used to indicate the media type of the resource.<br/>(application/json;charset=UTF-8)

__[Input Parameters]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|apikey|User API 
inherence Key|
|currency|Market name_Coin name (USD_BTC, USD_UNB, BTC_EOS, BTC_XRP, etc.)|
|org_ord_no|Order number|
|nonce|Current date (ex : 20190208)|
|hstr|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sha-256(nonce, currency, secretKey, sheckSum)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

__[Response]__

|&nbsp;&nbsp;&nbsp;Response Field&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|status|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0000: Normal / others: error&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

&nbsp;
---

#### 3-5. Place - Member's sell / buy trading order registration and conclusion

__[POST]__&nbsp;&nbsp;&nbsp;``https://api.uznex.com/api/private/v1/order/place``

```
{
  "currency" : "USD_BTC",
  "deal_type" : "B",
  "deal_money" : "10000",
  "amount" : "1",
  "fee_type" : "C"
}
```

__[Curl]__

```
curl -X POST --header 'Content-Type: application/json;charset=UTF-8' --header 'Accept: application/json' --header 'Authorization: Bearer 7603c80ddcd596c6fffb642e44470b9cea0d79e2e67a7b9de9ff5b957d46c1c7' -d '{ \ 
   "currency" : "USD_BTC", \ 
   "deal_type" : "B", \ 
   "deal_money" : "10000", \ 
   "amount" : "1", \ 
   "fee_type" : "C" \ 
 }' 'https://api.uznex.com/api/private/v1/order/place'
```

__[Response Body]__

```
{
  "status": "0000",
  "data": "Success",
  "order_id": "1902081549435770000003"
}
```

__[Input Header]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|Authorization|Access Token|
|Content-Type|The Content-Type entity header is used to indicate the media type of the resource.<br/>(application/json;charset=UTF-8)


__[Input Parameters]__

|&nbsp;&nbsp;&nbsp;Parameter Name&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|currency|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;마켓명_코인명 (USD_BTC, USD_UNB, BTC_EOS, BTC_XRP, etc.)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|deal_type|Selling/Buying sperate ( B-buying, S-selling)|
|deal_money|Order price|
|amount|Order volume|
|fee_type|Fee type (C-Coin fee) |

__[Response]__

|&nbsp;&nbsp;&nbsp;Response Field&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|status| 0000: Normal / others: error|
|order_id|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Order number&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

&nbsp;

---
&nbsp;
### 4. Status

#### 4-1. Token Error

|&nbsp;&nbsp;&nbsp;Status Value&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|2001|Member api key is not exist.|
|2002|INCONSISTENCY HSTR|
|2003|Refresh Token is not exist.|
|2004|Access Token is not exist or expired.|
|2005|No Access Token in Header.|
|2006|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;IP information has changed. Again create_access_token api call.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|2007|MEMBER_API_KEY is disabled.|
|2008|MEMBER API is not authorized.|
|2009|MEMBER API is not allow ip.|

&nbsp;
---

#### 4-2. Exception

|&nbsp;&nbsp;&nbsp;Status Value&nbsp;&nbsp;&nbsp;|Description|
|:------------:|:---------:|
|0001|Coin type input error|
|0002|Not exist order number.|
|0003|Please check the order price. / Trading amount can only be over 1,000 won.|
|0006|Please check the order volume. / The maximum coin amount is exceeded. / Please check the trading coin unit. / All cancellation is already registered.|
|1001|Invalid Parameter|
|1004|The data does not exist.|
|2000|DATA does not exist.
|3000|Order State Ready|
|9999|Interval Server Error|












