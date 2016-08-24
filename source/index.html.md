---
title: Attores API Reference

language_tabs:
  - shell
  - code

toc_footers:
  - <a href='https://dashboard.attores.com/keys' target="_blank">Sign Up for a Developer Key</a>
  - <a href='http://attores.com' target="_blank">Attores Landing Page</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Attores API! You can use our API to access Attores API endpoints, which can get information on various things like creating your own wallet on the Ethereum testnet, sending and receiving Ether, and deploying some actual Smart Contracts based on the Attores Smart Contract templates.

You can view code examples on the right section of this page.

<!-- ====================================================================================================== -->
# Kittens

## Get All Kittens

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```code
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```code
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

<!-- ====================================================================================================== -->
# Getting balances

## Single Address

```shell
curl "https://dashboard.attores.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```code
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
{"result":"22920041570577377666"}
```

This endpoint retrieves the balance of a single address from the Ethereum testnet.

### HTTP Request

`GET https://dashboard.attores.com/api/rest/getbalance`

### URL Parameters

Parameter | Type | Description
--------- | ------- | -----------
address | String | The address from which you want to find the balance.


## Multiple addresses

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```code
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{  
  "result":{  
      "0xe6e5a2941297b0c2850441740b04ea194b841f14":"22920041570577377666",
      "0xf36ca68454b2d8f3b404f06a9aea8f505f4c8359":"0",
      "0xb27a2b2b3fe4f2e4bb36d9c03fb8d504c98d8ecb":"54812560560970167641"
  }
}
```

This endpoint retrieves the balances of an array of addresses that you send.

### HTTP Request

`GET https://dashboard.attores.com/api/rest/getbalances`

### URL Parameters

Parameter | Type | Description
--------- | ------- | -----------
addresses | Comma separated strings | The addresses from which you want to find the balances.

<!-- ====================================================================================================== -->
# Wallet Management

## Create a Wallet

```shell
curl "https://dashboard.attores.com/api/createWallet"
  -H "Authorization: meowmeowmeow"
```

```code
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
{  
  "pubKey": "0x4b97ffa8b449513a76bef73da42d8eabbd477184",
  "seed": "circle rough trumpet witness embody neck crucial series derive senior else kind"
}

```

This endpoint creates a Seed and a public/private key pair based on the random entropy value that you send.

### HTTP Request

`GET https://dashboard.attores.com/api/rest/createWallet`

### URL Parameters

Parameter | Type | Description
--------- | ------- | -----------
entropyValue | String | Entropy in the form of a random string, at least 100 characters in length. Helps to create a truly random public keypair



## Set seed

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```code
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{  
  "pubKey": "0x4b97ffa8b449513a76bef73da42d8eabbd477184"
}
```
You can send your seed to this endpoint, which will return a public address generated from that seed.

The seed is a series of random words which are used to create the private key and public key (public address). When you sign the transaction with the seed, the browser converts this into the private key and uses this to sign the transaction.


### HTTP Request

`GET https://dashboard.attores.com/api/rest/setSeed`

### URL Parameters

Parameter | Type | Description
--------- | ------- | -----------
seed | String | The 12-word mnemonic, which will create a public/private keypair using which you can sign the transactions

<!-- ====================================================================================================== -->

# Creating Smart Contracts

## Create a Digital Certificate

```shell
curl "https://dashboard.attores.com/api/createCertificate
"
  -H "Authorization: meowmeowmeow"
```

```code
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
{  
  "contractAddress": "0x4b97ffa8b449513a76bef73da42d8eabbd477184"
}


```

This endpoint helps you ccreate and deploy a Smart Contract on the blockchain. Just send in some parameters for the Smart COntract and it will return a contract address on the testnet

### HTTP Request

`POST https://dashboard.attores.com/api/rest/createCertificate`

### URL Parameters

Parameter | Type | Description
--------- | ------- | -----------
seed | String | Entropy in the form of a random string, at least 100 characters in length. 
issuanceDate | String | Entropy in the form of a random string, at least 100 characters in length. 
studentName | String | Entropy in the form of a random string, at least 100 characters in length. 
courseName | String | Entropy in the form of a random string, at least 100 characters in length. 
ipfsHash | String | Entropy in the form of a random string, at least 100 characters in length. 
owner | String | Entropy in the form of a random string, at least 100 characters in length. 
directorPubKey | String | Entropy in the form of a random string, at least 100 characters in length. 
chairmanPubKey | String | Entropy in the form of a random string, at least 100 characters in length. 
studentPubKey | String | Entropy in the form of a random string, at least 100 characters in length. 
directorName | String | Entropy in the form of a random string, at least 100 characters in length. 
chairmanName | String | Entropy in the form of a random string, at least 100 characters in length. 


## Hackathon copyright

```shell
curl "https://dashboard.attores.com/api/rest/hackHash"
  -H "Authorization: meowmeowmeow"
```

```code
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{  
  "pubKey": "0x4b97ffa8b449513a76bef73da42d8eabbd477184"
}
```
This endpoint will enable you to 'copyright' your project for this hackathon onto the blockchain in the form of a Smart Contract.


### HTTP Request

`POST https://dashboard.attores.com/api/rest/hackHash`

### Method Parameters

Parameter | Type | Description
--------- | ------- | -----------
seed | String | The 12-word mnemonic, which will create a public/private keypair using which you can sign the transactions
projectHash | String | Hash of the project code
owner | String | The public key of the owner of this contract

<!-- ====================================================================================================== -->