---
title: 파워쉘 ssh 접속 & vscode remote ssh 접속 오류 해결
author: cotes
date: 2024-09-01 01:33:00 +0800
categories: [technology, guide]
tags: [ssh]
pin: true
math: true
mermaid: true
image:
  path: "./assets/img/posts/post_main/ssh접속.png"
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt: ssh 접속 img 
---

# 문제

1. vscode remote ssh 접속 오류 (없는 프로세스 파이프에 쓰려고 했습니다...)
2. powershell ssh 접속 오류

어제까지 되던게 갑자기 여러 프로그램 받고 이것저것 해서 그런지 vscode ssh remote가 오류가 났다.  
그래서 powershell 도 안되나 싶어서 해봤더니  
```
Could not create directory '/home/user123/.ssh'.
no hostkey alg
```
라는 메시지가 출력..

# 해결

우선 powershell 접속부터 해결.

ssh -v 보니까 OpenSSH 버전이 매우 오래된 버전(OpenSSH_5.4p1)이라는 점이 문제의 주요 원인 중 하나인듯. 이 버전은 현대적인 호스트 키 알고리즘이나 기타 보안 기능을 지원하지 않아 AWS EC2 인스턴스와의 연결에서 문제가 발생할 수 있다는 정보를 얻었음.
그래서 버전 바꾸고 다시 해보려 했음.

## powershell 순서
 
1. [OpenSSH-win64.zip](https://github.com/PowerShell/Win32-OpenSSH/releases)를 받아서 압축풀기 
2. 압축 푼 폴더를  C:\Program Files에 이동
3. 파워쉘을 관리자 권한으로 실행 후 (Set-ExecutionPolicy RemoteSigned -Scope CurrentUser) 명령어 입력해서 정책 바꾸기 A 선택. 다음으로 폴더이동 (cd "C:\Program Files\OpenSSH-Win64") 그리고 실행시키기 (.\install-sshd.ps1) R선택해서 한 번 실행
4. (Start-Service sshd) 명령어로 서비스 시작시키기 
5. (ssh -V) 명령어로 버전이 업데이트 되었는지 확인, 안되었다면? 환경변수로 가서 방금 실행시킨게 환경변수에 들어가있을텐데 맨위로 옮기고 예전버전의 OPENSSH 환경변수 삭제후 다시 파워쉘 관리자 모드로 실행하고 ssh -v 확인.
6. (ssh -i "C:\Users\user\.ssh\팸키.pem" ubuntu@ip) 명령어 입력. 한번했을때 그냥 꺼졌는데 다시 명령어 치니까 됐음

   
다음으로 vscode ssh remote 해결.

## vscode ssh 순서

1. 컨트롤+, 눌러서 환경설정이동 setting.json 파일 편집. 코드의 맨 아래에 코드 추가 (위 코드에 , 찍어줘야함)
   ```
    // 추가된 부분: Remote-SSH 관련 설정
    "remote.SSH.path": "C:\\Program Files\\OpenSSH-Win64\\ssh.exe", // SSH 경로 지정
    "remote.SSH.configFile": "C:\\Users\\user123\\.ssh\\config" // SSH config 파일 경로 지정
   ```
2. 재실행 vscode 그리고 다시 커넥트 (config파일은 아래와 같음)
   ```
   Host (host이름입력)
    HostName (ip입력)
    User ubuntu
    IdentityFile "C:\Users\user\.ssh\팸키.pem"
   ``` 
3. 성공
   ![완료사진](./assets/img/posts/guide/remoteSshDone.png)