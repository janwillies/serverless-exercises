+++
title = "Exercise 2"
weight = 3
[menu.main]
identifier = "ex2"
+++

Now that we are python experts, we can move on to JavaScript. The following code implements an echo service in JavaScript:

```javascript
const querystring = require('querystring');

module.exports = {

    handler: function (req, res) {

        var body = []

        req.on('error', (err) =>
            console.error(err)
        ).on('data', (chunk) =>
            body.push(chunk)
        ).on('end', () => {

            body = Buffer.concat(body).toString()
            let qs = querystring.parse(body)

            console.log("querystring: ", qs)

            let resp = {
                "response_type": "in_channel",
                "text": qs.text
            }

            res.end(JSON.stringify(resp))

        })
    }
}
```
{{% notice note %}}
We use the LTS Version of nodejs (`v6.10.2`). 
{{% /notice %}}

We can deploy the function with the already familiar commandline:

```sh
kubeless function deploy <TEAM-NAME>-echojs --runtime nodejs6.10 --handler echo.handler --from-file echo.js --trigger-http
```
And update it:
```sh
kubeless function update <TEAM-NAME>-echojs --runtime nodejs6.10 --handler echo.handler --from-file echo.js
```
Now create a `slash`-command in Mattermost to interact with the function!