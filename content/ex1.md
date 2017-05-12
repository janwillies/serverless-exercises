+++
title = "Exercise 1"
weight = 3
[menu.main]
identifier = "ex1"
+++

Parse input from mattermost chat and query a REST API. In our particular example, we'll query the `ycombinator` API:

```
import httplib, urllib
import xml.etree.ElementTree
import json

def handler():

    conn = httplib.HTTPSConnection("news.ycombinator.com")
    conn.request("GET", "/rss")

    r1 = conn.getresponse()

    # print r1.status, r1.reason
    data = r1.read()

    e = xml.etree.ElementTree.fromstring(data)

    channel = e.findall("channel/item")

    response = ""

    for child in channel:

        title = child.find("title")
        url = child.find("link")
        response = response + title.text + "\n"

    conn.close()

    # format the response object for mattermost
    return json.dumps({"response_type": "in_channel", "text": response})
```

Then create a mattermost `slash`-command to call the function.