+++
title = "Mattermost"
weight = 2
[menu.main]
identifier = "slash"
+++

Now we can create a _slash_-command in Mattermost to interact with our function. A _slash_-command allows you to enter a `/` followed by a command, and optionally some arguments, then an HTTP request will be sent to our function.

Login to Mattermost and look for the **Integrations** menu:

![Mattermost Integration](/mm_integrations.png) 

Then click **Slash Command** and **Add Slash Command**.

Fill in the following:

Key | Values
--------|------
Display Name | \<TEAM-NAME>-echo
Description | Echo Bot
Command Trigger Word | \<TEAM-NAME>-echo
Request URL | `http://<TEAM-NAME>-echo.default:8080`
Request Method | POST
Response Username | \<TEAM-NAME>-echo
Response Icon |  URL of a .png or .jpg file at least 128 pixels by 128 pixels
Autocomplete | [x]
Autocomplete Hint | 
Autocomplete Description | Echo service

After you save and return to the main chatroom, your slash command shows up in input bar:
![Mattermost Help](/mm_slash_help.png) 
