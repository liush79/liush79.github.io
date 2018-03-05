---
layout: post
title: Install Atom with jekyll
date: 2018-02-21
tags: jekyll atom
comments: true
---
## atom.io 설치
* 홈페이지 가서 받으면 됨
* https://atom.io 설치는 별거 없으니 패스

## atom 설정
* Edit > preferences > 왼쪽 install 탭 에서
* language-liquid 와 Jekyll 찾아서 설치
* 추가로 다음 플러그인도 설치 (나중에 깔아도 되고 안 깔아도 됨.)
  * Markdown-preview-enhanced
  * preview 기본으로 제공하는데 좀 더 강화된 플러그인 임.

## project open
* open project -> 블로그 경로 선택.. 프로젝트 loading 됨

## jekyll 시작
* View > Toggle Command Palette (Shift+Ctrl+P) > jekyll: Toggle Server 하면 빌드 성공...
* (혹시 빌드가 실패하면  Edit > preferences > package > jekyll > setting 에서 환경을 맞춰줘야함.)
* localhost:3000 으로 접속하면 blog 뜸

## 블로그 포스팅 해보기
* \_post 경로에 YYYY-MM-DD-[POST NAME].md 파일 생성해도 되지만
* View > Toggle Command Palette (Shift+Ctrl+P) > jekyll: New Post 해서 블로그 제목만 입력하면 자동으로 위 포멧으로 파일을 생성해준다.
* 생성한 파일 오픈 해보면 창이 좌우로 나뉘어 뜸 (.md 파일은 자동으로 프리뷰 화면이 뜨는 것 같다.)
![setup-atom](/assets/images/setup-atom.png)
* 왼쪽에서 수정하면 바로 오른쪽 에서 결과를 볼 수 있으니 매우 편함.
* 이미지는 clip-board 에서 바로 올리는 것은 안되는 것 같고
  * assets/images 에 이미지 저장하고  *\![Filename\](/assets/images/filename.png)* 처럼 저장하면 됨.

## 설치 후 겪은 문제점.
* Terminal에서 jekyll을 띄우면(포트: 4000) 아무 문제 없이 잘 되는데 Atom에 포함된? jekyll을 띄우면(포트: 3000) 포스팅 된 글을 클릭했을때 404 오류가 발생했다.
* 404 오류가 발생하는 원인을 보니 링크가 http://localhost:3000/2018/02/install-atom-with-jekyll.html 처럼 맨뒤에 html 이 붙은 파일을 찾고 있었다.
* \_config.yml 파일의 permalink 부분을 보면 html이 없는데에도 html을 찾고 있었음.
  * permalink: /:year/:month/:title
* .html 없이 하려고 했지만 방법을 찾지 못하고 .html을 추가하는 것으로 해결함.
  * permalink: /:year/:month/:title.html
* 다행히 Terminal에서 띄운 jekyll과 github는 .html을 추가해도 잘 동작한다.

## Reference
* http://futurecreator.github.io/2016/06/14/atom-as-markdown-editor/
* https://www.clien.net/service/board/lecture/8870683
