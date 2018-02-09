---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the LastMile real time API! You can use our API to access Last Mile Real Time API endpoint, which can get information on route of specific track id in our database.

You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Last Mile Real Time API

## Get route

```shell
curl "https://dev-realtime-wsapi-au.localz.io/v2/projects/{replace_with_valid_project_id}/tracks/{replace_with_valid_track_id}/route?apikey={replace_with_valid_api_key}"
```

```ruby
require 'json'
require 'net/http'

url = 'https://dev-realtime-wsapi-au.localz.io/v2/projects/{replace_with_valid_project_id}/tracks/ABCdef/route?apikey={replace_with_valid_api_key}'
uri = URI(url)
routeDetails = Net::HTTP.get(uri)

JSON.parse(routeDetails)
```

```python
import json
import requests

url = 'https://dev-realtime-wsapi-au.localz.io/v2/projects/{replace_with_valid_project_id}/tracks/ABCdef/route?apikey={replace_with_valid_api_key}'
response = requests.get(url)
if(response.ok):
  routeDetails = json.loads(response.content)
  print(routeDetails)
else:
  routeDetails.raise_for_status()
```

```javascript
const axios = require('axios');

axios.get('https://dev-realtime-wsapi-au.localz.io/v2/projects/{replace_with_valid_project_id}/tracks/ABCdef/route', {
    headers: {'Content-Type': 'application/json'},
    params: {
      apikey: {replace_with_valid_api_key}
    }
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

> The above command returns JSON structured like this:

```json
{
    "trackId": "ABCdef",
    "points": [
        {
            "duration": 2300,
            "altitude": 25.799999237060547,
            "timestamp": "2018-02-07T06:39:30.036Z",
            "horizontalAccuracy": 50.104,
            "bearing": 252.2151629429456,
            "distance": 3,
            "geoJson": {
                "coordinates": [
                    114.7471511250558,
                    -35.8709393916107
                ],
                "type": "Point"
            }
        }
    ],
    "status": "active",
    "destinations": [
        {
            "geoJson": {
                "coordinates": [
                    144.9632325,
                    -35.8059473
                ],
                "type": "Point"
            },
            "eta": 1819
        }
    ],
    "eta": 1819
}
```

This endpoint retrieves the route of specific track id.

### HTTP Request

`GET /v2/projects/{projectId}/tracks/{trackId}/route?apikey={apikey}`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
projectId | true | The project id
trackId | true | Job track id
apikey | true | Request for Developer API key

<aside class="success">
Route & the destination points
</aside>

<aside class="warning"><code>apikey</code> must be added in query string or header, otherwise the API will return error code 401 (Unauthorized).</aside>
<aside class="info">The example code is using development base url. To obtain production base url, please contact Localz.</aside>
