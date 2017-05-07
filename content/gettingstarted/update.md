+++
title = "Update a Function"
weight = 2
[menu.main]
identifier = "01-update"
parent="install"
+++
Let's make our example a bit more specific. Edit the sourcecode in `hello.py` and replace _World_ with _Frankfurt_. Then re-upload to kubeless:
```
kubeless function update <TEAM-NAME>-hello --runtime python27 --handler hello.handler --from-file hello.py 
```
Watch the new function getting deployed:
```
watch kubectl get pods
<ctrl>-c
```
We can also list all functions:
```
$ kubeless function list
+----------+-----------+---------------+----------+------+-------+--------------+
|   NAME   | NAMESPACE |   HANDLER     | RUNTIME  | TYPE | TOPIC | DEPENDENCIES |
+----------+-----------+---------------+----------+------+-------+--------------+
| hello    | default   | hello.handler | python27 | HTTP |       |              |
+----------+-----------+---------------+----------+------+-------+--------------+
```
Did our update work?
```
$ curl <TEAM-NAME>-hello.default:8080
{"text": "Hello, Frankfurt"}

```