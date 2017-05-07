+++
title = "Getting Started"
weight = 1
[menu.main]
identifier = "install"
+++

### Chatroom
Create an account on https://mattermost.containercluster.net if you haven't already. 

### Setting up the IDE
You can either SSH into our lab environment, or use an IDE on your laptop.

{{% notice note %}}
Using your own laptop will only work if you have Linux or OS X available
{{% /notice %}}

#### 1. Use the provided environment
SSH into the lab environment with the credentials provided in the chatroom. You may need to download an SSH-Client like [putty](https://the.earth.li/~sgtatham/putty/latest/w64/putty.exe) for that.

```
$ ssh user@ssh.containercluster.net
Last login: Sat May  6 13:34:10 2017 from 10.2.0.0
 ⌁ user@  ~   

```
Now create a folder for you or your team and cd into it:
```
mkdir <TEAM-NAME> && cd <TEAM-NAME>
```

That's it! You are all set.

#### 2. Use your own laptop
First copy the `config` file from the chatroom to `~/.kube/config`. This is used to authenticate yourself.

```
mkdir ~/.kube
mv ~/DOWNLOADED-CONFIG ~/.kube/config
```
Next download the client binaries depending on your platform. For linux choose `linux`, for OSX choose `darwin`:

```
export PLATFORM=darwin
```
kubectl:

```
curl -O https://storage.googleapis.com/kubernetes-release/release/v1.5.7/bin/$PLATFORM/amd64/kubectl \
    && chmod 755 kubectl \
    && mv kubectl /usr/local/bin/kubectl
```

kubeless:

```
curl -LO https://github.com/bitnami/kubeless/releases/download/0.0.11/kubeless_$PLATFORM-amd64.zip \
    && unzip kubeless_$PLATFORM-amd64.zip \
    && rm kubeless_$PLATFORM-amd64.zip \
    && mv kubeless_$PLATFORM-amd64/kubeless /usr/local/bin/kubeless \
    && rm -fr kubeless_$PLATFORM-amd64
```
That's it. `kubectl cluster-info` and `kubeless function list` should respond with something meaningful now.