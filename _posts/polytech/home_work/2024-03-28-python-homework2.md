---
title: python 과제 2024.03.28
author: cotes
date: 2024-03-28 17:33:00 +0800
categories: [폴리텍, python]
tags: [python]
pin: true
math: true
mermaid: true
image:
  path: ./assets/img/posts/python-logo.jpg
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt: 파이썬 로고 img 
---

# 확인문제

## 숫자 크기 비교

```python
a = int(input("> 1번째 숫자: ")) # 사용자로부터 첫 번째 숫자를 입력받음
b = int(input("> 2번째 숫자: ")) # 사용자로부터 두 번째 숫자를 입력받음
print() # 줄바꿈

if a > b: # 만약 a가 b보다 크다면
    print(f"{a}는 {b}보다 큽니다.") # a가 b보다 크다고 출력

if a < b: # 만약 a가 b보다 작다면
    print(f"{a}는 {b}보다 작습니다.") # a가 b보다 작다고 출력
```

## 띠 출력

```py
```python
str_input = input("태어난 해를 입력해 주세요 ")
birth_year = int(str_input)

animal_cycle = (current_year - birth_year) % 12

if animal_cycle == 0:
    print("원숭이 띠입니다.")
elif animal_cycle == 1:
    print("닭 띠입니다.")
elif animal_cycle == 2:
    print("개 띠입니다.")
elif animal_cycle == 3:
    print("돼지 띠입니다.")
elif animal_cycle == 4:
    print("쥐 띠입니다.")
elif animal_cycle == 5:
    print("소 띠입니다.")
elif animal_cycle == 6:
    print("범 띠입니다.")
elif animal_cycle == 7:
    print("토끼 띠입니다.")
elif animal_cycle == 8:
    print("용 띠입니다.")
elif animal_cycle == 9:
    print("뱀 띠입니다.")
elif animal_cycle == 10:
    print("말 띠입니다.")
elif animal_cycle == 11:
    print("양 띠입니다.")
```
## 100이상의 수 

```python
numbers = [273, 103, 5, 32, 65, 9, 72, 800, 99]

for number in numbers:
    if number >= 100:
        print("- 100 이상의 수:", number)
```
## 홀짝구별

```python
numbers = [273, 103, 5, 32, 65, 9, 72, 800, 99]

for number in numbers:
    if number % 2 == 0:
        print(f"{number} 는 짝수 입니다.")
    else:
        print(f"{number} 는 홀수 입니다.")
```

## 자릿수 출력

```python
numbers = [273, 103, 5, 32, 65, 9, 72, 800, 99]

for number in numbers:
    print(f"{number} 는 {len(str(number))} 자릿수입니다.")
```

## arr 나누기 3

```python
numbers = [i for i in range(1,10)]
output = [[] for i in range(3)]

for num in numbers:
    output[(num % 3)-1].append(num)
print(output)
```


## 1,3,5,7 만들기

```python
numbers = [1,2,3,4,5,6,7,8,9]
# 1 ,3, 5 ,7 
# i가 처음 0임 * 2를 하면 0인덱스라서 1의 값을 가져오고 1 * 2 는 3의 값 ----
for i in range(0, len(numbers) // 2):
    j = numbers[i * 2]
    print(f"i = {i}, j = {j}")
    numbers[j] = numbers[j] ** 2
    
print(numbers)
```

## dict 다루기
(1) dict_a 값 : {} /  dict_a에 적용할 코드 : dict_a["name"] = "구름" / dict_a 결과 : {'name': '구름'}  
(2) dict_a 값 : {'name': '구름'} /  dict_a에 적용할 코드 : dict_a.clear() / dict_a 결과 : {}  

```md
clear() 메서드와 딕셔너리에 새로운 딕셔너리를 할당하는 것(={})은 비슷해 보이지만, 실제로는 다른 동작을 수행.  
  
clear() 메서드 사용: 이 메서드는 딕셔너리 내의 모든 항목을 제거합니다. 딕셔너리의 구조와 메모리 위치는 그대로 유지되지만, 내용만 비워짐. dict_a.clear()를 호출하면 dict_a는 여전히 동일한 딕셔너리 객체를 참조하지만, 그 내용이 비워진 상태가 됨.  
  
새로운 딕셔너리 할당 (={}): 이 경우에는 기존의 딕셔너리 객체를 버리고 완전히 새로운 빈 딕셔너리 객체를 생성하여 dict_a에 할당. 이전 딕셔너리 객체와는 다른 새로운 메모리 위치에 저장된 새로운 딕셔너리 객체가 dict_a에 연결. 이 방법은 기존 딕셔너리의 참조가 다른 곳에서 사용되고 있지 않은 경우에 적합.
  
두 방법의 차이점을 이해하는 것은 특히 딕셔너리 객체가 여러 곳에서 참조되고 있을 때 중요. clear()를 사용하면, 해당 딕셔너리를 참조하는 모든 변수에 영향을 미쳐 딕셔너리의 내용이 모두 비워지지만, 새로운 딕셔너리를 할당하는 경우에는 그 할당을 받은 변수에만 영향을 미치고 다른 변수들은 여전히 원래의 딕셔너리 객체를 참조하게 됨.
```
## dict 출력하기
```py
pets = [
    {"name": "구름" , "age": 5},
    {"name": "초코" , "age": 3},
    {"name": "아지" , "age": 1},
    {"name": "호랑이" , "age": 1}
]

print("# 우리 동네 애완 동물들")
for i in range(len(pets)):
    print(pets[i]["name"],pets[i]["age"], end="살\n")
```
## dict wount하기
```py
numbers = [1,2,6,8,4,3,2,1,9,5,4,9,7,2,1,3,5,4,8,9,7,2,3]
# x : x의 횟수 // 그걸 connt해서 딕셔너리 변수에 저장 // Counter 이라는 라이브러리도 존재하긴함
counter = {x:numbers.count(x) for x in numbers}
print(counter)
```

## for문으로 타입에 맞게 출력하기

```py
character = {
    "name": "기사",
    "level" : 12,
    "items": {
        "sword": "불꽃의 검",
        "armor": "풀플레이트"
    },
    "skill" : ["베기", "세게 베기", "아주 세게 베기"]
}

for key in character:
    if type(character[key]) == list:
        for i in character[key]:
            print(f"{key} : "+i)
    elif type(character[key]) == dict:
        for i in character[key]:
            print(f"{i} : {character[key][i]} ")
    else:
        print(f"{key} : {character[key]} ")
```

## dict 두개의 변수 섞어서 합치기
```py
key_list = ["name", "hp", "mp", "level"]
value_list = ["기사", 200, 30, 5]
character = {}

for i in range(4):
    character[key_list[i]] = value_list[i]
print(character)
```

## 10000넘는값찾기
```py
limit = 10000
i = 1

sum_v = 0
while sum_v <= limit:
    sum_v += i
    i += 1

print("{}를 더할 때 {}를 넘으며 그때의 값은 {}입니다.".format(i-1, limit, sum_v))
```
## 1부터 100 에서 최대값이 나오는 값 찾기
```py
max_v = 0  
a = 0  
b = 0 

# i는 1부터 99까지 반복
for i in range(1, 100):
    j = 100 - i  # i와 j의 합이 항상 100이 되도록 설정

    # 현재 i와 j의 곱이 이전 최대값보다 큰지 확인
    if i * j > max_v:
        max_v = i * j  # 최대값 업데이트
        a = i  # 최대값을 만드는 i 값 저장
        b = j  # 최대값을 만드는 j 값 저장

# 최대값과 이를 만드는 a, b 값 출력
print("최대가 되는 경우: {} * {} = {}".format(a, b, max_v))
```
## 진수

파이썬에서 format()함수를 이용하면 10진수를 2진수, 8진수, 16진수로 간단하게 변환 할 수 있습니다.  

2진수는 Binary format의 'b'  

8진수는 Octal format의 'o'  

16진수는 Hexadecimal format의 'x'  

를 사용하면 됩니다.  

n = 8  

b = format(n,'b') #Binary format  
o = format(n,'o') #Octal format  
x = format(n,'x') #Hexadecimal format  

print(b)  
print(o)  
print(x)  
1000  
10  
8  

## 진수 변환
```py
output = []
# 2진수 b / 8진수 o / 16진수 x
# value = 60
# b = format(value, 'b')
# o = format(value, 'o')
# h = format(value, 'x')
for i in range(1,101):
    num = format(i, 'b')
    # 숫자를 str으로 형변환뒤 0이 1과 같다면 output애 2진수를 10진수로 변환한 수를 넣고
    if str(num).count("0") == 1:
        output.append(int(num, 2))
        print("{} : {}".format(i, "{:b}".format(i)))
# 더해서 출력
print("합계:", sum(output))
```

# 도전문제

## 간단한 대화 프로그램

```python
from datetime import datetime as dt

current_time = dt.now()

# 시간을 문자열로 포맷.
formatted_time = current_time.strftime("%H")

user_input = input("(C입력시 종료) 입력: ")
while user_input != "C":
    if "안녕" in user_input:
        print("안녕하세요")
    elif "몇 시"in user_input :
        print("지금은 %s시입니다." %formatted_time)
    user_input = input("(C입력시 종료) 입력: ")
```

## 나누어 떨어지는 숫자

```python
# 주어진 숫자
number = int(input("정수를 입력해주세요: "))

# 2, 3, 4, 5로 나누어 보고 결과에 따라 출력
if number % 2 == 0:
    print("273은 2로 나누어 떨어지는 숫자입니다.")
else:
    print("273은 2로 나누어 떨어지는 숫자가 아닙니다.")

if number % 3 == 0:
    print("273은 3으로 나누어 떨어지는 숫자입니다.")
else:
    print("273은 3으로 나누어 떨어지는 숫자가 아닙니다.")

if number % 4 == 0:
    print("273은 4로 나누어 떨어지는 숫자입니다.")
else:
    print("273은 4로 나누어 떨어지는 숫자가 아닙니다.")

if number % 5 == 0:
    print("273은 5로 나누어 떨어지는 숫자입니다.")
else:
    print("273은 5로 나누어 떨어지는 숫자가 아닙니다.")
```

## 사용된 숫자의 종류 수 찾기
```py
arr = [1, 2, 3, 4, 1, 2, 3, 1, 4, 2, 3]
dic = {x: arr.count(x) for x in arr}
print(f"사용된 숫자의 종류는 {len(dic)}개입니다.")
```

## 염기의 개수
```py
user = list(input("염기 서열을 입력해주세요: "))

dic = {x: user.count(x) for x in user}
for i in dic:
    print(f"{i}의 개수: ",dic[i])
```

## 염기 코돈 개수
```py
user = input("염기 서열을 입력해주세요: ")
sli = [user[i:i+3] for i in range(0, len(user),3)]
dic = {x: sli.count(x) for x in sli}
# ctacaatatcagtatacccatthcattagccgg
print(dic)
```

## 2차원 리스트 평탄화
```py
arr = [1,2, [3,4], 5, [6,7], [8,9]]

print(f"{arr}를 평탄화하면")
arr2 = []
for i in arr:
    if type(i) == list:
        for z in i:
            arr2.append(z)
    else:
        arr2.append(i)
print(f"{arr2}입니다.")
```