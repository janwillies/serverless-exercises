+++
title = "Exercise 4"
weight = 4
[menu.main]
identifier = "ex4"
+++

Query the Kubernetes API!

Here's a hint:
```python
from kubernetes import client, config

config.load_incluster_config()

v1=client.CoreV1Api()
```

An important factor is how to bring dependencies. In python this is done via a file called `requirements.txt`. Let's create a file with `vim requirements.txt`:
```
kubernetes
```

and then deploy with `--dependencies`:
```
kubeless function deploy [...] --trigger-http --dependencies requirements.txt
```