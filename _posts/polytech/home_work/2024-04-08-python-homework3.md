---
title: python 과제 2024.04.08
author: cotes
date: 2024-04-08 17:33:00 +0800
categories: [폴리텍, python]
tags: [home work]
pin: true
math: true
mermaid: true
image:
  path: ./assets/img/posts/post_main/python-logo.jpg
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt: 파이썬 로고 img 
---

## 과제코드

[home work python git code](https://github.com/qkrwldns/polyteck/tree/main/04-08_파이썬과제/)

## 에러

과제를 하다가 책에 있는 코드를 따라쳤는데 에러가 났다.  

![ai_img1](./assets/poly/python/2024-04-08/스크린샷-2024-04-29-212619.png)

아래가 위 사진의 코드(책)에서 에러가 발생하는 원인일 수 있음.

1. **변수 이름**:
    - 책 속 코드에서는 루프 변수 이름이 **`value`** 인 반면, 고친 코드에서는 **`rel`**로 사용. **`org_slide.part.rels`**는 관계 객체의 사전과 같은 객체를 반환하기 때문에, **`rel`**이라는 이름이 더 의미적으로 정확.
2. **관계 객체 순회**:
    - 사진의 코드에서는 **`org_slide.part.rels`**를 직접 for 루프에서 사용하는데, 이는 올바르지 않음. 왜냐하면 **`rels`**는 사전과 같은 객체이기 때문에, 그 값을 순회하기 위해서는 **`.values()`**를 사용해야 함. 
3. **관계 접근**:
    - 책의 코드에서는 **`value.rels.get_or_add`**를 사용하는데, 이는 맞지 않음. 왜냐하면 **`value`** (정확히는 **`rel`**이어야 합니다)는 단일 관계 객체이며, **`rels`** 속성이 없다.
4. **노트 슬라이드 제외**:
    - 책의 코드에서는 조건문을 잘못된 방식으로 사용하고 있다. **`if "notesSlide" not in value.relytpe:`**라는 부분이 잘못되었는데, 이것은 **`value`**가 사전의 값들을 순회하며 가져오는 객체라면 정확한 표현이 아님.고친 코드는 **`if "notesSlide" not in rel.reltype:`**로 올바르게 사용되고 있음.