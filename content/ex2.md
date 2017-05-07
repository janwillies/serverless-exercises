+++
title = "Exercise 2"
weight = 3
[menu.main]
identifier = "ex2"
+++


yoda api? https://market.mashape.com/ismaelc/yoda-speak

something like (but without async/await since we only have node-6.10)
```
'use strict';

const rp = require('request-promise-native');

module.exports = async function (context) {

    const body = context.request.body;

    // no parameters given, respond to user with help
    if (!body.text || body.text === 'help') {
        return {
            status: 200,
            body: {
                "response_type": "ephemeral",
                "text": "Example: `/yoda You have to go a long way`",
                "username": "Yoda",
                "icon_url": "https://d30y9cdsu7xlg0.cloudfront.net/png/32434-200.png"
            }
        };
    }

    // build the request object
    try {
        var options = {
            uri: 'https://yoda.p.mashape.com/yoda',
            qs: {
                sentence: body.text
            },
            headers: {
                'X-Mashape-Key': 'WXe3GAMpzmmshaDHEa8oS0QBOTzWp1JMiW2jsn1Uj4B5oIeYQ4',
                'Accept': 'text/plain'
            }
        };

        // query mashape api and wait for the repsonse
        const response = await rp(options);

        // respond to mattermost channel
        return {
            status: 200,
            body: {
                "response_type": "in_channel",
                "text": response,
                "username": "Yoda",
                "icon_url": "https://d30y9cdsu7xlg0.cloudfront.net/png/32434-200.png"
            }
        };
    } catch (e) {
        console.error(e);
        return {
            status: 500,
            body: e
        };
    }
}
```