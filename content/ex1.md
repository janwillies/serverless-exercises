+++
title = "Exercise 1"
weight = 3
[menu.main]
identifier = "ex1"
+++

Parse input from mattermost chat and query a REST API:

```sh
kubeless function deploy <TEAM-NAME>-yoda --runtime python27 --handler yoda.handler --from-file yoda.py --trigger-http
```

```
kubeless function update <TEAM-NAME>-yoda --runtime python27 --handler yoda.handler --from-file yoda.py
```

And then return with whatever the API responds to the chatroom.

