---
layout: post
title: windows 서버 jenkins 세팅 가이드
date: 2022-08-05
Author: soreal
tags: [jenkins, windows]
comments: true
toc : true
---


### Jenkins 세팅 가이드 

* node.js, java, git 설치 필요. 시스템 환경변수로 해당 경로 잡아줘야함. 

1. 젠킨스 설치. 포트 18080.  

2. localhost:18080 접속시 젠킨스 초기 화면 뜸. 어드민 초기 비밀번호 설정.  
플러그인 기본 설치. 
설치 안되면 proxy 설정 잡아줌. 

3. 대시보드 - jenkins 관리 - 시스템 설정 에서 기본 설정 확인. 

4. 대시보드 - jenkins 관리 - Manage Credentials - store scoped에서 jenkins 선택  
- Global credentials - Add credentials에 깃 아이디 토큰(비밀번호에 입력) 넣고 생성. 

5. 대시보드 - 새로운 Item에서 프로젝트 이름 설정하고 git repository 및 branch 설정. 
이때 credential 4번에서 생성한 걸로 선택. 빌드 명령어 shell script 선택하고 입력. 

6. 초기 빌드 실패 시 실제 워크스페이스 들어가서 명령어 하나씩 쳐주기. ex) npm install, npm config 등 
(C:\ProgramData\Jenkins\.jenkins\workspace\)


***
- 자체 tags

#jenkins