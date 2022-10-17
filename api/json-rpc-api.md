---
description: 'Test host: http://api.cata.show/'
---

# CATA Restful API

{% swagger baseUrl="/" path="ini_db" method="get" summary="create minerva table" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200" description="" %}
```
{
  "status": 0,
  "msg": "success",
  "cid": "Qmb6SYjWeWgmZN7ERNDgjKrCBCG9JJrNdTriqKiZ7a4JWv"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="/insert_metadata" path="" method="post" summary="Insert metadata into minerva" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="" type="object" required="false" %}
{

"db":"ipfs://QmNr3U2TAPnP2wA4n2fP161Lqzp5JusW1Mo8iT9WaqFTj8"

"metadata":\[{"title":"abc1","nft\_id":1}]

}
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
  "status": 0,
  "msg": "success",
  "cid": "QmYUQee1mTUGjEMtk2ZBn8LdE1YVWueF3q5ec7WMgXsGfc"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="/upload_file" path="/" method="post" summary=" upload file" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="" type="object" required="false" %}
{

\\

"file":"base64\_str"

\\

}
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
  "status": 0,
  "msg": "success",
  "cid": "QmVgoCXecnPxsYFzJdPqkaMnyd35XkC3qFvQcQFTr5QRam"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="/get_metadata" path="?" method="get" summary="get metadata by nft id" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="db_link" type="string" required="false" %}

{% endswagger-parameter %}

{% swagger-parameter in="query" name="nft_id" type="string" required="false" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
  "status": 0,
  "msg": "COMPLETED",
  "query_id": "1f0703e1-6827-a527-a684-bcadac4da5a5",
  "results": [
    {
      "nft_id": "1",
      "title": "abc1"
    }
  ]
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="/search_metadata" path="?" method="get" summary="search nft metadata" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="word" type="string" required="false" %}
search word
{% endswagger-parameter %}

{% swagger-parameter in="query" name="db_link" type="string" required="false" %}
minerva db link
{% endswagger-parameter %}

{% swagger-parameter in="query" name="field" type="string" required="false" %}
search field
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
  "status": 0,
  "msg": "COMPLETED",
  "query_id": "1f06d849-392d-efdb-29e4-a440fd8d7242",
  "results": [
    {
      "nft_id": "1",
      "title": "abc1"
    }
  ]
}
```
{% endswagger-response %}
{% endswagger %}
