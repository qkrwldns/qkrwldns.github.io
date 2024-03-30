---
title: VSCODE에서 C사용
author: cotes
date: 2024-03-30 08:33:00 +0800
categories: [technology, guide]
tags: [vscode]
pin: true
math: true
mermaid: true
image:
  path: ./assets/img/posts/vscode-logo.png
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt: vscode logo img 
---

## 비주얼 스튜디오 코드에서 C/C++ 개발 환경 설정하기

1. **C/C++ 확장 프로그램 설치**:
   먼저 Visual Studio Code용 C/C++ 확장 프로그램을 다운로드.

   ![C/C++ Extension pack](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbflMEx%2FbtrvrhjIpH7%2FsrKzkRweJUxRc8PiPL44lK%2Fimg.png)

2. **코드 러너 다운로드**:
   그런 다음 코드 스니펫과 파일을 매우 쉽게 실행할 수 있는 Code Runner 확장 프로그램을 다운로드.

   ![Code Runner Extension](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FFwlx6%2FbtrJNj21oSi%2F6pmKpBBepWtZQEZzYyOknk%2Fimg.png)

컨트롤 + 알트 + n 누르면 실행가능하게 해줌

3. **C 파일 만들기**:
   C 프로그램의 확장자가 '.c'인 새 파일(예: `helloworld.c`)을 만들기.

4. **GCC 컴파일러 확인**:
   명령 프롬프트에서 `g++ --version`을 실행하여 GCC 컴파일러가 설치되어 있는지 확인.

   - 설치되어 있지 않은 경우 [이 블로그(한국어)](https://m.blog.naver.com/dorergiverny/223032334186)에서 제공되는 설치 가이드를 따르기. 이 가이드는 Windows에만 적용.

5. **설치 확인**을 클릭합니다:
   설치 후 명령 프롬프트에서 `g++ --version`을 다시 실행하여 GCC 컴파일러가 올바르게 설치되었는지 확인. 버전이 표시되지 않는다면 잘못된 경로 설정 때문일 수 있음. 설치 가이드를 다시 참조하여 PATH가 올바르게 설정되었는지 확인.

6. **코드 실행**:
   Visual Studio Code를 재시작하고 `Ctrl + Alt + N`을 눌러 코드를 실행합니다. 하단에 권한을 묻는 파란색 바가 나타나면 '확인'을 클릭하여 계속 진행.

> 다른 블로그 보면 task json 코드를 변경하거나 하는 듯 하는데 그냥 해도 되긴 했음.. 문제가 생길시 다시 블로그 글 업댓예정  
{: .prompt-info }