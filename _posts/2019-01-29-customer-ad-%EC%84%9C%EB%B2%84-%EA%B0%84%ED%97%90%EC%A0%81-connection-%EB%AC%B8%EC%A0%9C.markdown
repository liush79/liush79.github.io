---
layout: post
title: "Customer AD 서버(Windows) 간헐적 connection 문제"
date: "2019-01-29 15:12:43 +0900"
---

## Introduce
* 앞으로 또 Customer AD를 쓸 일이 있을지는 모르겠지만 일단 적어 두는게 좋을 것 같아서 적어둠.

## Cause
* client 쪽에서 필요할 때마다 connection 하고 볼일 다 봤을 때 disconnection 하도록 했을 때 100 번에 1~2 회 정도 connection fail 이 발생함.
* MS 아닌 (우리 꺼 최고) 라이브러리 사용 시 발생할 수 있다고 함. 

## Resolution
* https://blogs.technet.microsoft.com/keithab/2016/11/11/transport-layer-security-tls-handshake-failing-schannel-error-36888/
* 간단히 요약하면
* HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Cryptography\Configuration\Local\SSL\00010002
* HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Cryptography\Configuration\SSL\00010002
* 위 registry 둘 중 하나에 따라 ssl 통신 순서가 결정되는데 이 순서를 바꿔줌으로 해결 된다 함.
* TLS_RSA_WITH_AES_xxxxxx로 시작하는 애들 6개 있는데 이들의 순서를 맨 위로 올리면 해결.
