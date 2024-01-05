---
sidebar_position: 2
---

# Managing Authorization Headers in Streaming API - Secure Approach

Starting January 9, 2024, access to the V2 APIs will be restricted without the OAuth token.

**Introduction**

In this section we will focus on the secure approach.
Remember that this approach requires more effort to implement. It is suitable for applications with a high risk of token theft or misuse.

The secure approach expects you to programmatically generate an access token using your client ID and client secret of an application.

![client](/img/v2Access/clientid_secret.png)



Below is a code snippet in Python that shows you how to programmatically generate a token, replace the placeholders with actual information.


```
import requests
import json


def oAuth_example():

  url = "https://oauth2.bitquery.io/oauth2/token"

  payload = 'grant_type=client_credentials&client_id=YOUR_ID_HERE&client_secret=YOUR_SECRET_HERE&scope=api'

  headers = {'Content-Type': 'application/x-www-form-urlencoded'}

  response = requests.request("POST", url, headers=headers, data=payload)
  resp = json.loads(response.text)
  print(resp)


oAuth_example()
```

