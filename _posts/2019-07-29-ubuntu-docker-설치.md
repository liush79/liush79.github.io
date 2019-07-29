---
layout: post
title: "ubuntu-docker-설치"
date: 2019-07-29 15:36:06
description: docker 설치 자꾸 까먹음. 
tags: 
 - ubuntu, docker
---

### 설치 (스크립트가 편함)
* script 
```{.bash}
$ curl -fsSL https://get.docker.com/ | sudo sh
```
### sudo 없이 하기
```{.bash}
# sudo usermod -aG docker $USER
# 하고 docker 재시작 만으로 안되서 재부팅 하니 됨.
```

### check
```{.bash}
$ docker version
Client: Docker Engine - Community
 Version:           19.03.1
 API version:       1.40
 Go version:        go1.12.5
 Git commit:        74b1e89
 Built:             Thu Jul 25 21:21:05 2019
 OS/Arch:           linux/amd64
 Experimental:      false
Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get http://%2Fvar%2Frun%2Fdocker.sock/v1.40/version: dial unix /var/run/docker.sock: connect: permission denied
# 위처럼 permission 문제 나면 아직 제대로 안된것.

```
