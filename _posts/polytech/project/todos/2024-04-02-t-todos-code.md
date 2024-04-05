---
title: "t_todos project 구현"
author: cotes
date: 2024-04-02 06:33:00 +0800
categories: [project, personal]
tags: [personal]
pin: true
math: true
mermaid: true
image:
  path: "./assets/img/project/t_todos/t_todos_main.png"
  lqip: "data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA"
  alt: "t_todos_main img"
---

## server

- 도구들: 
    1. Flask
    2. Telegram
    3. MySQL
    4. Socket.IO
    5. HTML, CSS, JS
    6. Git (롤백)

## client

- 도구들: 
    1. HTML
    2. CSS
    3. JS
    4. Bootstrap

## 구현

- 로그인 구축. 웹에 접속 시 username과 password를 입력하는 칸이 있음. username이 없으면 유저 등록하라는 메시지를 줌.

![UI](./assets/img/project/t_todos/t_todos_blog_img1.png)

- 비밀번호를 틀릴 경우 비밀번호 확인 메시지를 줌. 만약 계정 생성을 원하면 생성 가능.

![UI](./assets/img/project/t_todos/t_todos_blog_img2.png)

- 계정 생성 후 로그인 시, 팀원이 아니고 관리자도 아니라면 todo와 chat을 볼 수 없음.

![UI](./assets/img/project/t_todos/t_todos_blog_img3.png)

- 팀원일 경우 todo와 chat을 볼 수 있지만, 체크는 가능하나 생성, 변경, 삭제는 불가능.

![UI](./assets/img/project/t_todos/t_todos_blog_img4.png)

- 팀 페이지에서 팀원은 수정 및 삭제 불가능.

![UI](./assets/img/project/t_todos/t_todos_blog_img5.png)

**오류 발생**

1. **url_for**  
    > 로그인, 로그아웃 구현 시, 로그아웃하고 다시 홈으로 가기 위해 `url_for('/')`를 사용했는데 오류 발생. 로그아웃 함수 내에서 리디렉션을 정확히 처리하려면, 라우트 함수 이름을 `url_for`에 인자로 전달해야 함. `/` 경로는 이미 `login_or_register` 함수에 매핑되어 있으므로, 다음과 같이 수정하니 정상 작동됨.

    ```python
    @app.route('/logout')
    def logout():
        logout_user()  # 사용자 로그아웃 처리
        return redirect(url_for('login_or_register'))  # login_or_register 함수로 리디렉션
    ```

2. **Jinja 조건문**  
    > 사용자 ID가 1인 사람만(관리자) 버튼을 볼 수 있게 하려고 했으나, 관리자(ID 1)도 버튼을 볼 수 없는 문제 발생. Flask에서 `print`로 확인 및 Jinja에서 `<p>` 태그로 `current_user.id` 출력 시, 1이 정상적으로 나옴에도 불구하고 `{{ current_user.id == 1 }}` 사용 시 `False` 반환.
    형변환 문제로 추정, Jinja에서 정수 처리 시 `int` 필터 사용이 가능하여 이를 적용한 조건문 사용으로 문제 해결: `{% if current_user.id|int == 1 %}`.

- 관리자 관점의 팀 멤버 페이지

![UI](./assets/img/project/t_todos/t_todos_blog_img6.png)

- 일반 유저 관점의 팀 멤버 페이지

![UI](./assets/img/project/t_todos/t_todos_blog_img7.png)

- 채팅 링크를 통해 들어가면 실시간으로 채팅 가능

![UI](./assets/img/project/t_todos/t_todos_blog_img8.png)   
![UI](./assets/img/project/t_todos/t_todos_blog_img9.png)

- 관리자는 팀원을 삭제하거나 추가 가능

추가:  
![UI](./assets/img/project/t_todos/t_todos_blog_img10.png)  
![UI](./assets/img/project/t_todos/t_todos_blog_img11.png) 

삭제:  
![UI](./assets/img/project/t_todos/t_todos_blog_img12.png)  
![UI](./assets/img/project/t_todos/t_todos_blog_img13.png)

편집도 가능. 이름이나 이미지 URL 수정과 알림 기능은 차차 구현할 예정.

![UI](./assets/img/project/t_todos/t_todos_blog_img14.png)
