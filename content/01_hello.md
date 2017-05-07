+++
title = "First Function"
weight = 1
[menu.main]
identifier = "10-hello-overview"
parent="gettingstarted"
+++
In this exercise we will write a simple function in python and upload it to kubeless. It can be triggered by an HTTP-Call afterwards

#### Create Function
Edit the sourcecode for the function with `vim hello.py`:
```
import json

def handler():

    # create the response json 
    response = {"text": "Hello, World"}

    return json.dumps(response)
```
It's a simple function which responds with **Hello, World** when called.

Now deploy the function to kubeless, replace _\<TEAM-NAME\>_ with something meaningful:
```
kubeless function deploy <TEAM-NAME>-hello --runtime python27 --handler hello.handler --from-file hello.py --trigger-http
```
Don't worry about the parameters for now, we will dive into them later.

After a few seconds we can call the http-endpoint to trigger the function:
```
$ curl <TEAM-NAME>-hello.default:8080
{"text": "Hello, World"}
```
On your own laptop this works:
```
kubeless function call <TEAM-NAME>-hello
```



