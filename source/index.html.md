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

Welcome to the Attores API! You can use this API to generate signing requests, uploading the documents after readying them to be signed and other cool features! You also get access to the API endpoints, which can get information on various things like creating your own wallet on the Ethereum testnet, sending and receiving Ether.

You can view code examples on the right section of this page. You can check out all the blockchain transactions on [Etherscan](http://testnet.etherscan.io/).

<!-- ====================================================================================================== -->
# Ethereum Helpers

## Balance (Single Address)

```shell
curl -X GET -H "Cache-Control: no-cache" "https://dashboard.attores.com/api/rest/getbalance?key=jWH622nG5JuqqFMCn&address=0xe6e5a2941297b0c2850441740b04ea194b841f14"
```

```code
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://dashboard.attores.com/api/rest/getbalance?key=jWH622nG5JuqqFMCn&address=0xe6e5a2941297b0c2850441740b04ea194b841f14",
  "method": "GET",
  "headers": {
    "cache-control": "no-cache"
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
{
  "result": "22920041570577377666"
}
```

This endpoint retrieves the balance of a single address from the Ethereum testnet. The balance is returned in Wei. You can convert it to Ether on this page - [http://ether.fund/tool/converter](http://ether.fund/tool/converter)

### HTTP Request

`GET https://dashboard.attores.com/api/rest/getbalance`

### URL Parameters

Parameter | Type | Description
--------- | ------- | -----------
key | String | API key for your account
address | String | The address from which you want to find the balance.

## Balances (multiple addresses)

```shell
curl -X GET -H "Cache-Control: no-cache" "https://dashboard.attores.com/api/rest/getbalances?key=jWH622nG5JuqqFMCn&addresses=0xe6e5a2941297b0c2850441740b04ea194b841f14,0xb27a2b2b3fe4f2e4bb36d9c03fb8d504c98d8ecb,0xf36ca68454b2d8f3b404f06a9aea8f505f4c8359"
```

```code
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://dashboard.attores.com/api/rest/getbalances?key=jWH622nG5JuqqFMCn&addresses=0xe6e5a2941297b0c2850441740b04ea194b841f14%2C0xb27a2b2b3fe4f2e4bb36d9c03fb8d504c98d8ecb%2C0xf36ca68454b2d8f3b404f06a9aea8f505f4c8359",
  "method": "GET",
  "headers": {
    "cache-control": "no-cache"
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
{
  "result": {
    "0xb27a2b2b3fe4f2e4bb36d9c03fb8d504c98d8ecb": "54625690500970167641",
    "0xe6e5a2941297b0c2850441740b04ea194b841f14": "22920041570577377666",
    "0xf36ca68454b2d8f3b404f06a9aea8f505f4c8359": "0"
  }
}
```

This endpoint retrieves the balances of an array of addresses that you send.

### HTTP Request

`GET https://dashboard.attores.com/api/rest/getbalances`

### URL Parameters

Parameter | Type | Description
--------- | ------- | -----------
key | String | API key for your account
addresses | Comma separated strings | The addresses from which you want to find the balances.

## Get Ether 

```shell
curl -X GET -H "Cache-Control: no-cache" -H "https://dashboard.attores.com/api/rest/getEther?key=SRM9cpDbXyX8z9L7M&address=0xeB095096534817565dA13aBB0B0842023F594789"
```

```code
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://dashboard.attores.com/api/rest/getEther?key=SRM9cpDbXyX8z9L7M&address=0xeB095096534817565dA13aBB0B0842023F594789",
  "method": "GET",
  "headers": {
    "cache-control": "no-cache",
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
{
  "transactionHash": "0x0186fc7a78a7172e71fcdf84e74342e5b9012684b81d349c85b875ceb67c9160"
}
```

This endpoint will give you 10 Ether for every call. Please note that one API key can receive only 20 Ether. This measure has been put in place to avoid spamming.

### HTTP Request

`GET https://dashboard.attores.com/api/rest/getEther`

### URL Parameters

Parameter | Type | Description
--------- | ------- | -----------
key | String | API key for your account
address | String | The address at which you want to receive 10 Ether

## Get current block number

```shell
curl -X GET -H "Cache-Control: no-cache" -H "http://localhost:3000/api/rest/getBlockNumber?key=F2kz3F4RZLtuxmk6g"
```

```code
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:3000/api/rest/getBlockNumber?key=F2kz3F4RZLtuxmk6g",
  "method": "GET",
  "headers": {
    "cache-control": "no-cache",
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
{
  "blockNumber": 1545400
}
```

This endpoint will give you the current block number on the Ethereum testnet.

### HTTP Request

`GET https://dashboard.attores.com/api/rest/getBlockNumber`

### URL Parameters

Parameter | Type | Description
--------- | ------- | -----------
key | String | API key for your account

## Get confirmations on a TXN

```shell
curl -X GET -H "Cache-Control: no-cache" -H "https://dashboard.attores.com/api/rest/getConfirmations?key=mJnBz4TPaKCf3Wwxs&transactionHash=0xd1103cfbbf480cc60ce7f1827c24b5f64977cb48121d50a958147e81514f67d3"
```

```code
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://dashboard.attores.com/api/rest/getConfirmations?key=mJnBz4TPaKCf3Wwxs&transactionHash=0xd1103cfbbf480cc60ce7f1827c24b5f64977cb48121d50a958147e81514f67d3",
  "method": "GET",
  "headers": {
    "cache-control": "no-cache",
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
{
  "confirmations": 2
}
```

This endpoint will tell you the number of confirmations on a particular transaction hash. This is important when you want to make sure that the payment made by your app/account cannot be reversed.

### HTTP Request

`GET https://dashboard.attores.com/api/rest/getConfirmations`

### URL Parameters

Parameter | Type | Description
--------- | ------- | -----------
key | String | API key for your account
transactionHash | String | Transaction for which you want to check the confirmations

<!-- ====================================================================================================== -->

# Digital Signing 2.0

## Upload a document

```shell
curl -X POST -H "Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW" -H "Cache-Control: no-cache" -F "pdf=@" -F "title=testGaurang" -F "desc=Test" "https://dashboard.attores.com/api/rest/uploadPDF?key=F2kz3F4RZLtuxmk6g"
```

```code
var form = new FormData();
form.append("pdf", {"0":{}});
form.append("title", "testGaurang");
form.append("desc", "Test");

var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://dashboard.attores.com/api/rest/uploadPDF?key=F2kz3F4RZLtuxmk6g",
  "method": "POST",
  "headers": {
    "cache-control": "no-cache",
  },
  "processData": false,
  "contentType": false,
  "mimeType": "multipart/form-data",
  "data": form
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
{
  "success": {
    "id": "FXT7AkiFLGCEFNeAP",
    "hash": "0xd6c6cdc9def7bcc395f13f230fd381a2"
  }
}
```

As a first step for Digital Signing, you need to upload the documents using this endpoint, to ready it for Digital Signing. Upon success, you will get back the internal Attores ID and the hash of the document after it gets uploaded to our secure servers in an encrypted format. Please store this ID and hash, since it will be required in the next step. This endpoint is a multi-party form request, wherein you can upload the PDF using multi-party form request.

### HTTP Request

`POST https://dashboard.attores.com/api/rest/uploadPDF`

### URL Parameters

Parameter | Type | Description
--------- | ------- | -----------
key | String | API key for your account
title | String | The title of the document you are uploading
desc | String | A description of the document you are uploading
pdf | 

## Signing Request

```shell
curl -X GET -H "Cache-Control: no-cache" "https://dashboard.attores.com/api/rest/sendSignRequest?key=F2kz3F4RZLtuxmk6g&email=gaurangtorvekar@gmail.com&id=24Nfj7srWs3xgSQy6&redirectURL=https://attores.com&notifyURL=https://attores.com"
```

```code
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://dashboard.attores.com/api/rest/sendSignRequest?key=F2kz3F4RZLtuxmk6g&email=gaurangtorvekar%40gmail.com&id=24Nfj7srWs3xgSQy6&redirectURL=https%3A%2F%2Fattores.com&notifyURL=https%3A%2F%2Fattores.com",
  "method": "GET",
  "headers": {
    "cache-control": "no-cache",
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
{
  "message": "Success"
}
```

This endpoint sends a signing request to the document you have uploaded using the previous endpoint - uploadPDF. It will send an email to the email ID specified with this request, and that user can subsequently sign the document, whereafter the email ID associated with the user sending this request will get notified. 

### HTTP Request

`GET https://dashboard.attores.com/api/rest/sendSignRequest`

### URL Parameters

Parameter | Type | Description
--------- | ---- | -----------
key | String | API key for your account
email | String | The email address of the user to whom you want to send the signing request
id | String | The ID of the document that you uploaded using the uploadPDF endpoint
redirectURL | String | The URL where you want the user to be redirected after he finishes signing on the document
notifyURL | String | Attores will send the signing details to this URL

## Download signed document

```shell
curl -X GET -H "Cache-Control: no-cache" "http://localhost:3000/api/rest/downloadSignedPDF?key=gxdZxjFSueNzD4gNW&id=RyNTAYy6ewY3imMrb"
```

```code
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:3000/api/rest/downloadSignedPDF?key=gxdZxjFSueNzD4gNW&id=RyNTAYy6ewY3imMrb",
  "method": "GET",
  "headers": {
    "cache-control": "no-cache",
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
{
  "message": "PDF Saved"
}
```

This endpoint sends a download request to our servers. It will stream the PDF to your app and then you can display it on your UI. Please note that if you are using apps like Postman to test the API, it will download the PDF on your local file system.  

### HTTP Request

`GET https://dashboard.attores.com/api/rest/downloadSignedPDF`

### URL Parameters

Parameter | Type | Description
--------- | ---- | -----------
key | String | API key for your account
id | String | The ID of the document that you uploaded using the uploadPDF endpoint


## Standalone blockchain transaction 

```shell
curl -X GET -H "Cache-Control: no-cache" "https://dashboard.attores.com/api/rest/sendBlockchainTxn?key=F2kz3F4RZLtuxmk6g&email=gaurangtorvekar@gmail.com&notifyURL=https://attores.com&hash=0xdashkd"
```

```code
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://dashboard.attores.com/api/rest/sendBlockchainTxn?key=F2kz3F4RZLtuxmk6g&email=gaurangtorvekar%40gmail.com&notifyURL=https%3A%2F%2Fattores.com&hash=0xdashkd",
  "method": "GET",
  "headers": {
    "cache-control": "no-cache",
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
{
  "message": "0x63479b039b91af4d73742488b7443617656b52658ee65242bcc1eb87db431261"
}
```

This endpoint can be used by the companies who already have the UI built up for sending signing requests and already have the interface for placing the signatures on the PDF documents. Using this API endpoint, you can use the notarization features provided by Attores for sending a transaction to the Attores Digital Signing smart contract, which contains the hash of the PDF and a unique ID associated with each signer. Using this transaction, you can verify that the signature was placed on the PDF in a decentralized manner. 
This request will return the transaction hash which you can check on testnet.etherscan.io.

### HTTP Request

`GET https://dashboard.attores.com/api/rest/sendBlockchainTxn`

### URL Parameters

Parameter | Type | Description
--------- | ------- | -----------
key | String | API key for your account
email | String | The email address of the user who is signing this document
notifyURL | String | Attores will send the signing details to this URL
hash | String | The MD5 hash of the document on which the user is signing

<!-- ====================================================================================================== -->
<!-- # Wallet Management

## Create a Wallet

```shell
curl -X GET -H "Cache-Control: no-cache" "https://dashboard.attores.com/api/rest/createWallet?key=jWH622nG5JuqqFMCn&entropyValue=adjfkjskadlfjkjasdkfjksadfsadkfklasjdklfjioewafkanwvn39034590345jfsdjvijejvjew9viwejivhjwejv;ewlkfjweiofwefpwefwef"
```

```code
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://dashboard.attores.com/api/rest/createWallet?key=jWH622nG5JuqqFMCn&entropyValue=adjfkjskadlfjkjasdkfjksadfsadkfklasjdklfjioewafkanwvn39034590345jfsdjvijejvjew9viwejivhjwejv%3Bewlkfjweiofwefpwefwef",
  "method": "GET",
  "headers": {
    "cache-control": "no-cache"
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
{
  "pubKey": "e44713b2190c63fb50e603de196819498b13f6a2d845642e6b0c07f09e6f2e41",
  "seed": "ring soup raven heavy tomato friend cost rather remember fat mass sibling",
  "address": "66addf1704cc1cd6a1e66ed334daf71a0c397ffd"
}
```

This endpoint creates a Seed and a public/private key pair based on the random entropy value that you send.

### HTTP Request

`GET https://dashboard.attores.com/api/rest/createWallet`

### URL Parameters

Parameter | Type | Description
--------- | ------- | -----------
key | String | API key for your account
entropyValue | String | Entropy in the form of a random string, at least 100 characters in length. Helps to create a truly random public keypair



## Set seed

```shell
curl -X GET -H "Cache-Control: no-cache" "https://dashboard.attores.com/api/rest/setSeed?key=jWH622nG5JuqqFMCn&seed=ring%20soup%20raven%20heavy%20tomato%20friend%20cost%20rather%20remember%20fat%20mass%20sibling"
```

```code
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://dashboard.attores.com/api/rest/setSeed?key=jWH622nG5JuqqFMCn&seed=ring%20soup%20raven%20heavy%20tomato%20friend%20cost%20rather%20remember%20fat%20mass%20sibling",
  "method": "GET",
  "headers": {
    "cache-control": "no-cache"
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
{  
  "pubKey": "e44713b2190c63fb50e603de196819498b13f6a2d845642e6b0c07f09e6f2e41"
}
```
You can send your seed to this endpoint, which will return a public address generated from that seed.

The seed is a series of random words which are used to create the private key and public key (public address). When you sign the transaction with the seed, the browser converts this into the private key and uses this to sign the transaction.


### HTTP Request

`GET https://dashboard.attores.com/api/rest/setSeed`

### URL Parameters

Parameter | Type | Description
--------- | ------- | -----------
key | String | API key for your account
seed | String | The 12-word mnemonic, which will create a public/private keypair using which you can sign the transactions
 -->
<!-- ====================================================================================================== -->
<!-- 
# Creating Smart Contracts

## Create a Digital Certificate

```shell
curl -X POST -H "Cache-Control: no-cache" -H "Content-Type: application/x-www-form-urlencoded" -d 'key=aGXjpRyjv72QvPQPZ&seed=abc abc abc abc abc abc abc abc abc abc abc abc&issuanceDate=12th July 2016&studentName=John&courseName=Blockchain Development&ipfsHash=QmbuuLzxztp35bEcMp6VXx2y7NSm1aQTPhxRyKr3zZTgCN&owner=0x4b97ffa8b449513a76bef73da42d8eabbd477184&directorName=Eden&chairmanName=Rob&directorPubKey=0x4b97ffa8b449513a76bef73da42d8eabbd477184&chairmanPubKey=0x4b97ffa8b449513a76bef73da42d8eabbd477184&studentPubKey=0x4b97ffa8b449513a76bef73da42d8eabbd477184' "https://dashboard.attores.com/api/rest/createCertificate"
```

```code
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://dashboard.attores.com/api/rest/createCertificate",
  "method": "POST",
  "headers": {
    "cache-control": "no-cache"
    "content-type": "application/x-www-form-urlencoded"
  },
  "data": {
    "key": "aGXjpRyjv72QvPQPZ",
    "seed": "abc abc abc abc abc abc abc abc abc abc abc abc",
    "issuanceDate": "12th July 2016",
    "studentName": "John",
    "courseName": "Blockchain Development",
    "ipfsHash": "QmbuuLzxztp35bEcMp6VXx2y7NSm1aQTPhxRyKr3zZTgCN",
    "owner": "0x4b97ffa8b449513a76bef73da42d8eabbd477184",
    "directorName": "Eden",
    "chairmanName": "Rob",
    "directorPubKey": "0x4b97ffa8b449513a76bef73da42d8eabbd477184",
    "chairmanPubKey": "0x4b97ffa8b449513a76bef73da42d8eabbd477184",
    "studentPubKey": "0x4b97ffa8b449513a76bef73da42d8eabbd477184"
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
{  
  "contractAddress": "0x4b97ffa8b449513a76bef73da42d8eabbd477184"
}


```

This endpoint helps you ccreate and deploy a Smart Contract on the blockchain. Just send in some parameters for the Smart Contract and it will return a contract address on the testnet

### HTTP Request

`POST https://dashboard.attores.com/api/rest/createCertificate`

### URL Parameters

Parameter | Type | Description
--------- | ------- | -----------
key | String | API key for your account
seed | String | The 12-word mnemonic, which will create a public/private keypair using which you can sign the transactions
issuanceDate | String | Issuance date of the certificate, will be printed on the cert
recipientName | String | Name of the recipient
courseName | String | Name of the course/certificate
owner | String | Public key of the owner of this smart contract. He will be the superuser and only he can makes changes to the contract variables
issuerPubKey | String | Public key of the certificate issuer. Can be the owner or someone else.
issuerName | String | Entropy in the form of a random string, at least 100 characters in length. 

## Hackathon copyright

```shell
curl -X POST -H "Cache-Control: no-cache" -H "Content-Type: application/x-www-form-urlencoded" -d 'key=y6jxTL8q7uqBWPg6o&seed=abc abc abc abc abc abc abc abc abc abc abc abc&projectHash=Qm&owner=0x4b97ffa8b449513a76bef73da42d8eabbd477184' "https://dashboard.attores.com/api/rest/hackHash"
```

```code
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://dashboard.attores.com/api/rest/hackHash",
  "method": "POST",
  "headers": {
    "cache-control": "no-cache"
    "content-type": "application/x-www-form-urlencoded"
  },
  "data": {
    "key": "y6jxTL8q7uqBWPg6o",
    "seed": "abc abc abc abc abc abc abc abc abc abc abc abc",
    "projectHash": "Qm",
    "owner": "0x4b97ffa8b449513a76bef73da42d8eabbd477184"
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
{
  "contractAddress": "0x1f304ff2916fcdd8c1a79583d6512d59be9c0854"
}
```
This endpoint will enable you to 'timestamp' your project for this hackathon onto the blockchain in the form of a Smart Contract.


### HTTP Request

`POST https://dashboard.attores.com/api/rest/hackHash`

### Method Parameters

Parameter | Type | Description
--------- | ------- | -----------
key | String | API key for your account
seed | String | The 12-word mnemonic, which will create a public/private keypair using which you can sign the transactions
projectHash | String | Hash of the project code
owner | String | The public key of the owner of this contract
 -->
<!-- ====================================================================================================== -->
