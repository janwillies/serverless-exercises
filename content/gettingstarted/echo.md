+++
title = "Echo Service"
weight = 3
[menu.main]
identifier = "echo-post"
parent="install"
+++

Not a whole lot useful to just trigger functions. We want to hand some data to the function. Let's create a function which handles a `POST`.
#### Create Echo Function
Edit the sourcecode for the function with `vim echo.py`:
```
import json

def handler(context):

    # user_id = context.forms.user_id
    # response_url = context.forms.response_url
    # token = context.forms.token
    # channel_id = context.forms.channel_id
    # team_id = context.forms.team_id
    # command = context.forms.command
    # team_domain = context.forms.team_domain
    # user_name = context.forms.user_name
    # channel_name = context.forms.channel_name
    text = context.forms.text

    # format the response object for mattermost
    response = {"response_type": "in_channel",
                "text": "Echo: " + text}


    # return response to mattermost
    return json.dumps(response)
    
```
Deploy the function to kubeless:
```
kubeless function deploy <TEAM-NAME>-echo --runtime python27 --handler echo.handler --from-file echo.py --trigger-http
```

Now when we call the function, we need to hand over some data:
```
$ curl -X POST -d"text=test" team1-echo.default:8080 -H "Content-Type: application/x-www-form-urlencoded"
{"text": "Echo: test", "response_type": "in_channel"}
```

Not too bad! Head over to the next chapter to see how you can interact with the function via a chatbot.
