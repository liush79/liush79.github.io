---
layout: post
title: "git-my-setting"
tags: git
date: "2018-07-23 14:05:23 +0900"
---

## My Alias
* my alias
```sh
git config --global alias.st status
git config --global alias.ci commit
git config --global alias.df diff
git config --global alias.co checkout
git config --global alias.br branch
```

## Git clone 할때 ID 넣기
* git clone 할때 @ 를 넣으면 push 를 제대로 못할 때가 있다.
* 그럴때 @ 대신 %40을 넣어라.
```sh
git clone https://liush79%40gmail.com@github.com/liush79/liush79.github.io.git
````

## Commit 했을때 프로필에 초록색 박스가 채워지지 않는다면
* 회사같은데서 사용할때는 global을 회사용으로 사용하므로 개인이 쓰는 메일로 덮어써야한다.
* 개인프로젝트를 받은 경우는 다음처럼 개인 email로 commit 되도록 수정해야한다.
```sh
git config --local user.email "liush79@gmail.com"
git config --local user.name "seungho.ryu"
# --list 로 확인 가능.
git config --list
``` 

## Control Remote branch
* 원격 브랜치 삭제
```sh
git push --delete upstream feature/BRANCH-1234
```
* 원격 브랜치에 생성
```sh
git push upstream master:feature/BRANCH-1234
# master 기준으로 feature/BRANCH-1234 생성해라.
```

## git identity file 지정
* 기본 파일이 아닌 다른 파일명으로 지정하는방법
* File: ~/.ssh/config
```sh
Host {{HostName}}
    HostName {{HostName}}
    User seungho.ryu
    IdentityFile /home/ubuntu/.ssh/id_rsa_my_git
    IdentitiesOnly yes
```

## git setting
* git color 입히기
```sh
git config --global color.ui auto
```
* git user 설정 (이 값은 ~/.gitconfig 에서 확인 가능)
```sh
git config --global user.email "seungho.ryu@MYMAIL.com"
git config --global user.name "Seungho Ryu"
```

## git 잘못 올라간 파일 삭제
```shell script
# 원격에 있는 파일을 삭제한다.
# 로컬에 있는 파일은 삭제하지 않는다.
$ git rm --cached [File Name]
```

## git stash
* git stash 명령어들

```sh
git stash save
# 현재 작업을 저장해두고 branch를 head로 돌린다.(git reset –hard)

git stash list
# 저장되어 있는 stash들 보기

git stash pop
# stash들은 stack에 저장된다. 따라서 가장 최근에 save한 stash가 현재 branch에 적용된다.

git stash apply
# git stash pop 과 비슷한 명령어지만 stash list에서 삭제하지 않는다는 점이 다르다.

git stash drop
# 필요 없는 stash를 삭제

git stash clear
# 전체 stash list를 삭제
```

## Support git https
* 우분투 경우 (14.04) 기본 http만 지원으로 되어 있었던것 같음.
* 소스 받아서 설치필요.

```sh
sudo apt-get install libcurl4-openssl-dev

wget https://www.kernel.org/pub/software/scm/git/git-2.12.0.tar.gz
tar xvf git-2.12.0.tar.gz
cd git-2.12.0
 ./configure
make -j8
sudo make install
```

## git https 사용시 캐시하는법
```
git config --global credential.helper 'cache --timeout=3600'
```
* 윈도우에서는 winstore 라는 것을 설치해야한다고 함. (해보진 않음)
* https://github.com/anurse/git-credential-winstore/downloads
* 설치 후 위 명령어 다시 실행.
