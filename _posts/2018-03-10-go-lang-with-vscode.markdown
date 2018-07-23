---
layout: post
title: "go lang with vscode"
tags: golang vscode
date: "2018-03-10 20:22:49 +0900"
---

### golang 설치
* 우분투 16.04에서 apt-get 으로 설치하니 버전1.6이 설치된다.
* golang homepage로 가서 최신버전 받음. (https://golang.org/dl/)

### VSCode 설치
* homepage에서 받아서 설치 (https://code.visualstudio.com/Download)

### VSCode 설정
* 메뉴 > file > view > extention > go 입력 > Go 'Rich Go language support for Visual Studio Code'
* ![](/assets/images/vscode-go.png)
* 적당한 위치에 폴더 생성 (/home/seunghoryu/dev/golang)
  * 그리고 해당 폴더에 bin, pkg, src 3개폴더 생성
  * (참고로 /home/seunghoryu/dev/golang 위치는 python의 venv 폴더 같은 부분을 지정하는 것 같다.)
  * 나중에 hello_world 프로젝트를 만들면 /home/seunghoryu/dev/golang/src/hello_world 에 만들면 될듯.
  * 아무튼.. 생성한 폴더를 GOPATH로 지정
    * $ export GOPATH=/home/seunghoryu/dev/golang
    * go env 명령으로 GOPATH 설정된 것 확인할 수 있음.
* vscode 에서 해당 폴더를 오픈 (/home/seunghoryu/dev/golang) > src/hello_world 폴더를 생성 >  src/hello_world/hello.go 파일 생성
{% highlight go %}
    package main

    import "fmt"

    func main() {
        fmt.Println("hello world")
    }
{% endhighlight %}

* go path 설정
  * 설정 창 오픈 (ctrl+,) '사용자 설정'(user setting)말고 '작업 영역 설정' 탭 눌러서 거기에 추가
    {% highlight json %}
    {
       "go.gopath": "/home/seunghoryu/dev/golang"
    }
    {% endhighlight %}

## VSCode 패키지 설치
* hello.go 파일을 다시 와보면 (혹은 저장해보면)
* 오른쪽 아래에 Analysis Tool Missing 글씨가 보임 클릭하면 화면위에 install 할거냐고 물어봄.. 클릭(install All로 했음)
* ![](/assets/images/vscode-tool.png)
  * 그러면 뭔가 필요한 파일 들 설치함. 꽤 오래걸림  *
  * 여기서 만약 실패한다면 지우고 다시 시도해보길바람. (터미널에서 go env 했을때 GOPATH랑 설정의 go.gopath가 일치해야함)  
    * 또한 실패를 한두개만 한다면 go version 을 해서 버전을 확인할것 버전이 1.6 이면 1.9 이상으로 올려야함.
  * ![](/assets/images/vscode-tool2.png)
  * build는 저장하면 자동으로 되는거 같고 메뉴중 디버깅 시작 하면 디버깅 할수 있음.
