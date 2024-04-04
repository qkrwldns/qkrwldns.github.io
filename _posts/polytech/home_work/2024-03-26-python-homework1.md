---
title: python 과제 2024.03.26
author: cotes
date: 2024-03-26 17:33:00 +0800
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

# 연습문제

## for문 합계 출력  
3333부터 9999수 중 1234배수이고 현재 합계가 100000미만이라면 계속더하고 그 합계 출력

```python
# 변수 초기화
num = 0
# 3333부터 9999까지 반복
for i in range(3333, 10000):
    # 만약 현재 숫자가 1234의 배수가 아니고, 현재까지의 합계가 100000을 넘지 않는다면
    if i % 1234 != 0 and num + i < 100000:
        num += i  # 현재 숫자를 합계에 더함
        # for 반복문 처음으로 돌아감 
        continue
    else:
        break  # 100000을 넘기거나 1234의 배수를 만나면 반복 중단

print(num)  # 계산된 합계 출력
```

## 소수 구하기

```py
# 빈 리스트를 초기화. 이 리스트는 찾은 소수들을 저장하기 위해 사용.
list1 = []

# 3부터 100까지의 수에 대해 반복.
# 여기서 i는 현재 검사하고 있는 숫자.
for i in range(3,101):
    # num을 1로 초기화. num은 i가 소수인지 아닌지를 나타내는 플래그 변수.
    # num이 1이면 소수로 간주하고, 0이면 소수가 아니라고 간주.
    num = 1
    
    # 2부터 (i-1)까지의 수에 대해 반복하여 i가 나누어 떨어지는지 검사.
    # 여기서 j는 i를 나눌 수 있는 후보
    for j in range(2,i):
        # i가 j로 나누어 떨어지면, i는 소수가 아님.
        if i % j == 0:
            # num을 0으로 설정하여 i가 소수가 아님을 표시.
            num = 0 
    
    # 내부 반복문이 끝난 후, num이 여전히 1이면 i는 소수.
    if num != 0:
        # i를 소수 목록에 추가.
        list1.append(i)

# 리스트에 저장된 소수들을 공백으로 구분하여 하나의 문자열로 변환하고 출력.
# map 함수는 리스트의 각 요소를 문자열로 변환하고, join 함수는 이를 공백으로 연결.
print(' '.join(map(str,list1)))  
```

## 문자 형 개수 
```py
input_data = input()
a = ""
b = ""
c = ""
d = ""
e = ""

for i in input_data:
    if ord(i) >= 65 and ord(i) <= 90:
        a += i
    elif ord(i) >= 97 and ord(i) <= 122:
        b += i
    elif ord(i) >= 48 and ord(i) <= 57:
        c += i
    else:
        if ord(i) >= 127:
            d += i
        elif ord(i) == 32:
            continue
        else:
            e += i
print("대문자: %s \n소문자: %s \n숫자: %s \n한글: %s \n기타: %s" %(a, b, c, d, e))
```
# 응용예제

## 1. 윤년 계산
```python
## 변수 선언 부분 ##
year = 0

## 메인 코드 부분 ## 
if __name__ =="__main__":
    year = int(input("연도를 입력하세요 : "))
    # year이 4와 나눠서 0이면서 100으로 나눠서 0이 아니거나 400으로 나눠서 0이라면 그것은 윤년
    if ((year % 4 == 0) and (year % 100 != 0)) or (year % 400 == 0):
        print("%d년은 윤년입니다." %year) 
    else:
        print("%d년은 윤년이 아닙니다." %year)
```

## 2. 하트모양출력

```python
# 변수 선언 부분
i, k, heartNum = 0, 0, 0
numStr, ch, heartStr = "", "", ""

# 메인 코드 부분
if __name__ == "__main__":
    # 숫자를 여러 개 입력받음
    numStr = input("숫자를 여러 개 입력하세요: ")
    print("")

    i = 0
    ch = numStr[i]

    while True:
        # 입력받은 숫자를 int형으로 변환
        heartNum = int(ch)

        # 하트 문자열 초기화
        heartStr = ""

        # 입력받은 숫자만큼 하트 문자열에 추가
        for k in range(0, heartNum):
            heartStr += "\u2665"

        # 하트 문자열 출력
        print(heartStr)

        # 다음 숫자로 이동
        i += 1

        # 입력받은 숫자열의 끝에 도달하면 종료
        if (i > len(numStr) - 1):
            break

        # 다음 숫자를 가져옴
        ch = numStr[i]
```

## 3. 숫자정렬(?)1

```python
import random

# ## 변수 선언 부분 ##
data = []
i, k = 0, 0

# ## 메인 코드 부분 ##
if __name__ == "__main__":
    for i in range(0, 10):  # 원본의 데이터 10개 생성
        tmp = hex(random.randrange(0, 100000))
        data.append(tmp)

    print('정렬 전 데이터 : ', end='')
    [print(num, end=' ') for num in data]

    for i in range(0, len(data) - 1):
        for k in range(i + 1, len(data)):
            if int(data[i], 16) > int(data[k], 16):
                tmp = data[i]
                data[i] = data[k]
                data[k] = tmp

    print('\n정렬 후 데이터 : ', end='')
    [print(num, end=' ') for num in data]
```


## 4. 숫자정렬(?)2
```python
import random

# ## 함수 선언 부분 ##
def getNumber(strData):
    numStr = ''
    for ch in strData:
        if ch.isdigit():
            numStr += ch
    return int(numStr)

# ## 정렬 부분 선언 부분 ##
data = []
i, k = 0, 0

# ## 메인 코드 부분 ##
if __name__ == "__main__":
    for i in range(0, 10):  # 원본의 데이터를 10개 생성
        tmp = hex(random.randrange(0, 100000))
        tmp = tmp[2:]  # 앞의 '0x'를 제거
        data.append(tmp)

    print('정렬 전 데이터 : ', end='')
    [print(num, end=' ') for num in data]

    for i in range(0, len(data) - 1):
        for k in range(i + 1, len(data)):
            if getNumber(data[i]) > getNumber(data[k]):
                tmp = data[i]
                data[i] = data[k]
                data[k] = tmp

    print('\n정렬 후 데이터 : ', end='')
    [print(num, end=' ') for num in data]ㄴ
```