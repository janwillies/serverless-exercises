
+++
title = "Debugging"

[menu.main]
identifier = "debugging"
parent="gettingstarted"
+++
Calling the `kubeless` binary without any parameters prints out the available options:
```
function command allows user to list, deploy, edit, delete functions running on Kubeless

Usage:
  kubeless function SUBCOMMAND [flags]
  kubeless function [command]

Available Commands:
  call        call function from cli
  delete      delete a function from Kubeless
  deploy      deploy a function to Kubeless
  describe    describe a function deployed to Kubeless
  list        list all functions deployed to Kubeless
  logs        get logs from a running function
  update      update a function on Kubeless

Flags:
  -h, --help   help for function

Use "kubeless function [command] --help" for more information about a command.
```

Here are some useful commands to debug your function:
```
kubeless function logs
kubeless function list
kubectl get pods
kubectl get svc
```