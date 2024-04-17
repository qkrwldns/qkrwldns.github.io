---
title: t_todos project (개요)
author: cotes
date: 2024-04-02 06:33:00 +0800
categories: [project, personal]
tags: [personal project]
pin: true
math: true
mermaid: true
image:
  path: ./assets/img/project/t_todos/t_todos_main.png
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt: t_todos_main img
---

# T_Todos 프로젝트 

## 만드는 이유

개인프로젝트를 생각하다가 ict멘토링 팀 프로젝트도 있고 해서 팀원끼리 사용할 수 있으면 좋겠다고 생각이 들어서 팀 관련 웹을 만들려고 하다가 이걸 선택하게 되었다.   

## **팀원 간 협업을 위한 To-Do 리스트 애플리케이션 요구사항 명세서**

### **1. 개요**

- **목적**: 팀원 간의 효율적인 협업과 업무 진행 상황의 실시간 추적을 가능하게 하는 웹 기반 To-Do 리스트 애플리케이션 개발
- **대상 사용자**: 협업이 필요한 그룹

### **2. 기능 요구사항**

### 2.1 사용자 관리

- 사용자는 닉네임을 통해 애플리케이션에 접근할 수 있음

### 2.2 To-Do 리스트 관리

- 관리자는 To-Do 항목을 생성, 수정, 삭제할 수 있음
- 각 To-Do 항목에는 제목과 상세 설명이 포함됨
- 관리자는 To-Do 항목의 완료 상태를 체크할 수 있음
- To-Do 항목은 팀원 모두에게 실시간으로 공유됨

### 2.3 실시간 채팅 기능

- 팀원 간 실시간 채팅을 통해 의사소통 가능
- 채팅은 Socket.IO를 활용하여 구현하며, 사용자가 온라인 상태일 때 실시간 메시지 교환이 가능함

### 3.4 호환성 요구사항

- 주요 웹 브라우저(Chrome, Firefox, Safari, Edge)에서 문제없이 작동해야 함


## **기능정의서**

### **1. 사용자 관리**

### 1.1 로그인

- **기능 설명**: 사용자는 닉네임(ID)과 년도(비밀번호)를 사용하여 애플리케이션에 로그인.
- **입력**: 사용자의 닉네임과 년도
- **처리**: 시스템은 입력된 닉네임과 년도를 검증하여, 해당하는 사용자 정보와 일치할 경우 접근을 허용.
- **출력**: 로그인 성공 시, 사용자는 애플리케이션의 메인 페이지로 이동.
- **예외 처리**: 닉네임 또는 년도가 일치하지 않을 경우, 사용자에게 오류 메시지를 표시.

### 1.2 팀원 관리 (관리자 기능)

- **기능 설명**: 관리자는 팀원을 추가하고, 팀원의 액세스 권한을 설정할 수 있음.
- **입력**: 추가할 팀원의 닉네임
- **처리**: 시스템은 팀원을 팀에 추가하고, 해당 팀원에게 읽기 전용 권한을 부여.
- **출력**: 새로운 팀원이 팀 목록에 추가.

### **2. To-Do 리스트 관리**

### 2.1 To-Do 항목 생성 (관리자 기능)

- **기능 설명**: 관리자는 새로운 To-Do 항목을 생성할 수 있다. 항목에는 제목만 포함.
- **입력**: To-Do 항목의 제목
- **처리**: 시스템은 새 To-Do 항목을 데이터베이스에 저장하고, 해당 팀원과 관련된 모든 세션에 실시간으로 공유.
- **출력**: 생성된 To-Do 항목이 팀원의 To-Do 리스트에 표시.

### 2.2 To-Do 항목 완료 처리 (팀원 기능)

- **기능 설명**: 팀원은 To-Do 항목을 완료로 표시할 수 있음.
- **입력**: 완료로 표시할 To-Do 항목 선택
- **처리**: 시스템은 해당 항목의 완료 상태를 업데이트하고, 변경 사항을 실시간으로 반영.

### **3. 알림 기능**

- **알림**: 관리자나 팀원이 체크 할 시 완료 알림이 telegram msg로 간다.

### **4. 실시간 채팅 기능**

### 3.1 실시간 채팅 (관리자 및 팀원 기능)

- **기능 설명**: 로그인한 사용자는 팀원 간 실시간으로 메시지를 주고받을 수 있습니다. 
- **입력**: 사용자가 입력하는 메시지 텍스트.
- **처리**: 시스템은 Socket.IO를 사용하여 메시지를 실시간으로 전송하고, 해당 사용자의 팀 채팅 인터페이스에 메시지를 표시.
- **출력**: 사용자의 메시지가 채팅창에 실시간으로 나타남.


## **기술스택**

1. html, css, js
2. flask 
3. Sokcet.io

## **DB**
### **1. Users Table**

| Field Name | Data Type | Constraints | Description |
| --- | --- | --- | --- |
| UserID | INT | PK, Auto Increment | 사용자 고유 식별자 |
| Username | VARCHAR(50) | Unique, Not Null | 사용자 이름 |
| Password | VARCHAR(255) | Not Null | 사용자 비밀번호 (암호화 권장) |
| ProfilePic | VARCHAR(255) |  | 프로필 사진 URL |
| TeamID | INT | FK to Teams.TeamID | 사용자가 속한 팀 ID |

### **2. Teams Table**

| Field Name | Data Type | Constraints | Description |
| --- | --- | --- | --- |
| TeamID | INT | PK, Auto Increment | 팀 고유 식별자 |
| TeamName | VARCHAR(50) | Not Null | 팀 이름 |

### **3. Messages Table**

| Field Name | Data Type | Constraints | Description |
| --- | --- | --- | --- |
| MessageID | INT | PK, Auto Increment | 메시지 고유 식별자 |
| UserID | INT | FK to Users.UserID | 메시지를 보낸 사용자 ID |
| Content | TEXT | Not Null | 메시지 내용 |
| Timestamp | DATETIME | Not Null | 메시지 전송 시간 |

### **4. Todos Table**

| Field Name | Data Type | Constraints | Description |
| --- | --- | --- | --- |
| TodoID | INT | PK, Auto Increment | 할일 고유 식별자 |
| Title | VARCHAR(255) | Not Null | 할일 제목 |
| IsCompleted | BOOLEAN | Not Null | 완료 여부 |
| UserID | INT | FK to Users.UserID | 할일을 만든 사용자 ID |

## **예상 UI**

![UI](./assets/img/project/t_todos/t_todos_ui.png)

## 과정

1. 요구분석, 기능, db명세서 작성
2. Mysql download 후 db만들고 table 만들고 column 만들기
> 사용법 : [MySQL Workbench 사용방법](https://velog.io/@coreminw/MySQL-Workbench-%EC%82%AC%EC%9A%A9%EB%B0%A9%EB%B2%95)  
처음에 Schema랑 Administration을 선택하는 창을 못보고 db만들고나서  한참 해맸음 
3. [figma](https://www.figma.com/)에 가서 ui작성함 
> 사용법 : [[Figma] 툴 사용법 기초 정리](https://tkayyoo.tistory.com/20) 


