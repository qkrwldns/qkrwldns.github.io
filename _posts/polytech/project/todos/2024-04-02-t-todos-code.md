---
title: t_todos project (구현)
author: cotes
date: 2024-04-02 06:33:00 +0800
categories: [project, personal]
tags: [personal]
pin: true
math: true
mermaid: true
image:
  path: ./assets/img/project/t_todos/t_todos_main.png
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt: t_todos_main img
---

## server

- 도구들 : 
    1. flask
    2. telegram
    3. mysql 
    4. socket.io
    5. html, css, js 
    6. git(롤백)

## client

- 도구들 : 
    1. html
    2. css 
    3. js
    4. Bootstrap 

## 구현

- login구축. 일단 먼저 web에 접속시 username 과 password를 입력하는 칸이 있음 username이 없으면 유저 등록하라는 msg를 줌

![UI](./assets/img/project/t_todos/t_todos_blog_img1.png)

- 비번 틀릴시 비번 확인하라는 msg를 줌 만약 생성하기를 원하면 생성이 가능

![UI](./assets/img/project/t_todos/t_todos_blog_img2.png)

- 생성후 로그인시 팀원이 아니고 관리자가 아니라면 todo 도 chat도 못봄

![UI](./assets/img/project/t_todos/t_todos_blog_img3.png)

- 팀원이라면 todo와 chat을 볼 수 있고 체크는 가능 하지만 생성이나, 변경, 삭제는 불가능

![UI](./assets/img/project/t_todos/t_todos_blog_img4.png)

- 팀페이지에 가면 팀원은 수정 삭제 불가능  

![UI](./assets/img/project/t_todos/t_todos_blog_img5.png) 

**오류 발생**
1. **url_for**   
처음에 로그인, 로그아웃 구현할때 로그아웃하고 다시 home으로 가기위해서  url_for(’/’) 이렇게 했는데 오류가 났다. 검색해보니 로그아웃 함수 내에서 리디렉션을 정확히 처리하려면, 라우트 함수 이름을 `url_for`에 인자로 전달해야 한다고한다. `/` 경로는 이미 `login_or_register` 함수에 매핑되어 있으므로, 다음과 같이 수정하니까 정상 작동되었다

```python
@app.route('/logout')
def logout():
    logout_user()  # 사용자 로그아웃 처리
    return redirect(url_for('login_or_register'))  # login_or_register 함수로 리디렉션

```

2. **jinja 조건문**  
원래는 사용자 ID가 1인 사람만(관리자) 버튼을 볼 수 있게 하려고 했다. 그런데 관리자인데 (ID가 1인) 버튼을 못 보는 문제가 생겼다. Flask에서 print로 찍어보고 Jinja에서도 p 태그에 current_user.id를 출력해봤는데, 분명 1이 나왔다. 그런데도 {{ current_user.id == 1 }} 하니까 False가 나왔다.
형변환이 문제인 것 같아서 이리저리 찾아봤는데, 딱히 마땅한 답을 못 찾았다. 그래서 Flask에서 Jinja로 형변환을 시도해보려고 했는데, 오류가 떴다. 결국 Jinja 문법 내에서 형변환을 시도해보기로 했고, Jinja에서는 정수를 처리할 때 int 필터를 쓸 수 있다길래, 그 방법을 써서 조건문을걸었더니 해결이 됐다: {% if current_user.id|int == 1%}.

- 관리자관점의 팀멤버 페이지

![UI](./assets/img/project/t_todos/t_todos_blog_img6.png) 


- 일반유저관점의 팀멤버 페이지

![UI](./assets/img/project/t_todos/t_todos_blog_img7.png) 

- chat 링크를 타고 들어가면 실시간으로 채팅이 가능하다

![UI](./assets/img/project/t_todos/t_todos_blog_img8.png)   
![UI](./assets/img/project/t_todos/t_todos_blog_img9.png) 

- 관리자는 팀원을 삭제하거나 추가가 가능하고

추가 :  
![UI](./assets/img/project/t_todos/t_todos_blog_img10.png)  
![UI](./assets/img/project/t_todos/t_todos_blog_img11.png) 

  
삭제 :  
![UI](./assets/img/project/t_todos/t_todos_blog_img12.png)  
![UI](./assets/img/project/t_todos/t_todos_blog_img13.png) 

편집도 가능하다 이름을.. 이미지 url을 수정하는건 차차 구현할 생각이다

![UI](./assets/img/project/t_todos/t_todos_blog_img13.png) 

