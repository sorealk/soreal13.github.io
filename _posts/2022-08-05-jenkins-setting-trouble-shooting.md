---
layout: post
title: windows 서버 jenkins 쉘 스크립트 설정
date: 2022-08-05
Author: soreal
tags: [jenkins, windows]
comments: true
toc : true
---



### Shell executable 설정


```
    java.io.IOException: Cannot run program "sh" (in directory "C:\Users\Markus\.hudson\jobs\Test1 Unit TEst\workspace"): CreateProcess error=2, Das System kann die angegebene Datei nicht finden
    at java.lang.ProcessBuilder.start(Unknown Source)

    Caused: java.io.IOException: Cannot run program "sh"

```

젠킨스 대시보드 - 환경설정 - Shell - Shell executable에서 `C:\Windows\system32\cmd.exe` 을 설정한다 라고 stackoverflow 등에 해결책이 나와있다.



근데 그래도 나는 안 됐는데...



### windows cmd에서 젠킨스 명령어 sh 실행 안되는 현상 (Suceess로 뜸)

```
    [store-front-dev] $ C:\Windows\system32\cmd.exe -xe C:\Windows\TEMP\jenkins5964363487789764350.sh 
    Microsoft Windows [Version 10.0.14393] 
    (c) 2016 Microsoft Corporation. All rights reserved. 
    C:\ProgramData\Jenkins\.jenkins\workspace\store-front-dev>Finished: SUCCESS
```


Dashboard - 프로젝트 - 설정 - Execute Shell의 command에 `npm run build:development` 명령어를 쳤지만 위와 같이 아무런 반응 없는데 SUCCESS로 리턴 되며 빌드가 되지 않았다.


문제는 cmd.exe에 해당 명령어를 치면 똑같이 나온다는 점이다. 
즉 windows cmd는 저 명령어를 못알아 먹는다. 


해결방법은 간단한데 -xe sh 명령어를 알아먹는 프로그램 경로를 Shell executable에 잡아주는 것이다. 


````
    C:\Program Files\Git\bin\sh.exe

````

처음에 bash.exe 로 잡아 줬지만 제대로 실행이 되지 않아 아예 sh.exe로 경로를 잡아줬더니 명령어 인식을 잘 한다.

해결.


***
- 자체 tags

#우당탕탕트러블슈팅 #jenkins


