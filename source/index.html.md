---
title: Semantic Search (Beta)

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>

includes:
  - errors

search: false
---

# What is Semantic Search? 
 
Semantic Search as a service can process raw, unstructured digital texts (“plain text”). 

At its core it uses Latent Semantic Analysis to discover semantic structure of documents by examining statistical co-occurrence patterns of the words within a corpus of training documents. LSA is unsupervised, which means no human input is necessary – you only need a corpus of plain text documents. Once these statistical patterns are found, any plain text documents can be succinctly expressed in the new, semantic representation. The representation via Index can then be queried for topical similarity against other documents. 

The semantic Search service functions are available via API EndPoints.

We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('your_generated_key')
```

```python
import kittn

api = kittn.authorize('your_generated_key')
```

```shell
# With shell, you can just pass the correct header with each request
curl -X POST 
  {Server_URL}
  -H 'cache-control: no-cache' 
  -H 'content-type: application/json' 
  -H 'postman-token: 339767b1-088c-6a42-e491-dce52b16e4e3' 
  -H 'x-api-key: CowP0hsIke3SYXHdFCauR9WxwYJSzOK6dL9Fr1k5' 
  -d '{"query": "film unit with lens", "lsi_top": 1000}'

```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('your_generated_key');
```

> Make sure to replace `your_generated_key` with your API key.

API keys are required to allow access to the API. You can register a new Semantic search API key at our [developer portal](http://lsi.fortheta.com/developers).

Search search API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: your_generated_key`

<aside class="notice">
You must replace <code>your_generated_key</code> with your personal API key.
</aside>


# Semantic Search on Wikipedia  

## Fetch Semantically Similar Documents

```ruby

require 'uri'
require 'net/http'

url = URI("http://lsi.foretheta.com/")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'application/json'
request["x-api-key"] = 'your generated key'
request.body = "{\n \"query\": \"a musical instrument is an instrument created or adapted to make musical sounds. in principle, any object that produces sound can be considered a musical instrumentit is through purpose that the object becomes a musical instrument. the history of musical instruments dates to the beginnings of human culture. early musical instruments may have been used for ritual, such as a trumpet to signal success on the hunt, or a drum in a religious ceremony. cultures eventually developed composition and performance of melodies for entertainment.\"\n}"

response = http.request(request)
puts response.read_body

```

```python
import requests

url = "http://lsi.foretheta.com/"

payload = "{\n    \"query\": \"a musical instrument is an instrument created or adapted to make musical sounds. in principle, any object that produces sound can be considered a musical instrumentit is through purpose that the object becomes a musical instrument. the history of musical instruments dates to the beginnings of human culture. early musical instruments may have been used for ritual, such as a trumpet to signal success on the hunt, or a drum in a religious ceremony. cultures eventually developed composition and performance of melodies for entertainment.\"\n}"
headers = {
    'content-type': "application/json",
    'x-api-key': "your_generated_key"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl -X POST \
  http://lsi.foretheta.com/ \
  -H 'content-type: application/json' \
  -H 'x-api-key: your generated key' \
  -d '{
    "query": "a musical instrument is an instrument created or adapted to make musical sounds. in principle, any object that produces sound can be considered a musical instrumentit is through purpose that the object becomes a musical instrument. the history of musical instruments dates to the beginnings of human culture. early musical instruments may have been used for ritual, such as a trumpet to signal success on the hunt, or a drum in a religious ceremony. cultures eventually developed composition and performance of melodies for entertainment."
}'
```

```javascript

var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://lsi.foretheta.com/",
  "method": "POST",
  "headers": {
    "content-type": "application/json",
    "x-api-key": "your generated key"
  },
  "processData": false,
  "data": "{\n    \"query\": \"a musical instrument is an instrument created or adapted to make musical sounds. in principle, any object that produces sound can be considered a musical instrumentit is through purpose that the object becomes a musical instrument. the history of musical instruments dates to the beginnings of human culture. early musical instruments may have been used for ritual, such as a trumpet to signal success on the hunt, or a drum in a religious ceremony. cultures eventually developed composition and performance of melodies for entertainment.\"\n}"
}

$.ajax(settings).done(function (response) {
  console.log(response);
});

```

> The above command returns JSON structured like this:

```json
[
    {
        "url": [
            "https://en.wikipedia.org/wiki?curid=37001823"
        ],
        "score": 0.66654103994369507,
        "title": [
            "list of astronomical instruments"
        ]
    },
    {
        "url": [
            "https://en.wikipedia.org/wiki?curid=209519"
        ],
        "score": 0.71585583686828613,
        "title": [
            "bandoneon"
        ]
    }
]
```

Description: This endpoint retrieves all Documents that are semantically similar to the given query 

### HTTP Request

`GET http://lsi.foretheta.com/api/search`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
Query | "" | The Query String.
Top_N | 1000 | Return the top N most relevent documents.

<aside class="success">
Remember — you will receive a 200 upon succeful authentication!
</aside>