# http-api
rack gateway api reference 


* Invoice
    * [create](#post-v1invoicecreate)  
    * [info](#post-v1invoiceinfo)  
    * [cancel](#post-v1invoicecancel)  
    * [qr-code](#get-v1invoiceqr-codeinvoice_id)  
  
### POST /v1/invoice/create 

Request example:
```json
{
  "lifetime": 10,
  "amount": 10,
  "api_key": "f176ab8c801bf7576e6944fff0f24b3477087ad8f664e2a0bd811d0230d9a82a",
  "cryptocurrency": "eth"
}
```

Response example: 
```json
{
  "error": false,
  "invoice": {
    "id": "1ccc5566-4443-4b35-8a5e-453b17f00370",
    "wallet": {
      "qr_code": "http://0.0.0.0:8888/v1/invoice/qr-code/1ccc5566-4443-4b35-8a5e-453b17f00370",
      "address": "0x969BbA04b398eb00AD48Dd05f4aeC2AAD473e9f1",
      "amount_to_pay": "10",
      "cryptocurrency": "eth"
    }
  }
}
```

### POST /v1/invoice/info

Request example: 
```json
{
    "invoice_id": "1ccc5566-4443-4b35-8a5e-453b17f00370",
    "api_key": "f176ab8c801bf7576e6944fff0f24b3477087ad8f664e2a0bd811d0230d9a82a"
}
```

Response example:
```json
{
  "id": "1ccc5566-4443-4b35-8a5e-453b17f00370",
  "amount": "10",
  "cryptocurrency": "eth",
  "status": "canceled",
  "is_paid": false,
  "created_at": "2025-01-07 12:55:34"
}
```

### POST /v1/invoice/cancel

Request example:
```json
{
  "invoice_id": "1ccc5566-4443-4b35-8a5e-453b17f00370",
  "api_key": "f176ab8c801bf7576e6944fff0f24b3477087ad8f664e2a0bd811d0230d9a82a"
}
```

Response example: 
```json
{
  "error": false
}
```

### GET /v1/invoice/qr-code/[invoice_id]


### POST /v1/merchant/create
Request example: 
```json
{
  "merchant_name": "fuzz"
}
```

Response example: 
```json
{
  "error": false,
  "api_key": "a979d23afd5efc08aba579fb23339ea23f518e6e7aa03bf88c83422f158bbbc3",
  "merchant_id": "1235eb4c-f875-4159-a392-1b692b7e7502"
}
```

### POST /v1/finances/withdrawal

Request example: 
```json
{  
  "merchant_id": "1235eb4c-f875-4159-a392-1b692b7e7502",
  "to_address": "0x969BbA04b398eb00AD48Dd05f4aeC2AAD473e9f1",
  "cryptocurrency": "eth",
  "amount": 0.39933,
  "api_key": "a979d23afd5efc08aba579fb23339ea23f518e6e7aa03bf88c83422f158bbbc3"
}
```


Response example: 
```json
{
  "error": false,
  "withdrawal_id": "0830b40f-4e5c-463c-b50f-d0b7fec61360",
  "to_address": "0x969BbA04b398eb00AD48Dd05f4aeC2AAD473e9f1",
  "amount": "0.39933",
  "info": "http://0.0.0.0:8888/v1/finances/withdrawal/info/0830b40f-4e5c-463c-b50f-d0b7fec61360"
}
```


### POST /v1/finances/info/[withdrawal_id]
Response example: 
```json
{
  "error": false,
  "to_address": "0x969BbA04b398eb00AD48Dd05f4aeC2AAD473e9f1",
  "amount": "0.39933",
  "status": "success",
  "created_at": "2025-01-07 13:53:13"
}
```



### POST /v1/currency/convert

Request example: 
```json
{
  "fiat": "eur",
  "cryptocurrency": "eth",
  "amount": 10,
  "api_key": "f176ab8c801bf7576e6944fff0f24b3477087ad8f664e2a0bd811d0230d9a82a"
}
```


Response example: 
```json
{
  "error": false,
  "fiat": "EUR",
  "amount": "10",
  "cryptocurrency": "eth",
  "converted": "0.0028281503",
  "rate": "3535.88"
}
```



### POST /v1/currency/rates

Request example: 
```json
{
  "fiat": "eur",
  "api_key": "f176ab8c801bf7576e6944fff0f24b3477087ad8f664e2a0bd811d0230d9a82a"
}
```


Response example: 
```json
{
  "error": false,
  "fiat": "EUR",
  "rates": {
    "eth": "3535.88",
    "ltc": "108.76",
    "sol": "206.65",
    "ton": "5.53"
  }
}
```






```