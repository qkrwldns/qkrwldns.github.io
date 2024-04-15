---
title: git과 github를 활용한 팀 협업 방법
author: cotes
date: 2024-04-15 08:33:00 +0800
categories: [technology, guide]
tags: [git&github]
pin: true
math: true
mermaid: true
image:
  path: https://miro.medium.com/v2/resize:fit:1400/format:webp/1*mtsk3fQ_BRemFidhkel3dA.png
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt: arc logo img 
---

## git과 github를 활용한 팀 협업 방법

<iframe width="560" height="315" src="https://www.youtube.com/embed/tkkbYCajCjM?si=m5sHH3-6-6vEz8J9" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

### 팀리더

- 저장소를 생성한다.   
   
<img src="https://i.ibb.co/Xzg5g57/image.png" alt="image" border="0">  

- 팀원 초대를 한다.(Add collaborators ... > Add people > 팀원 이름이나 이메일 입력)
  
<img src="https://i.ibb.co/JrGxr54/image.png" alt="image" border="0">    
<img src="https://i.ibb.co/jGP9ChL/image.png" alt="image" border="0">

- 로컬에서 프로젝트를 만든다. (폴더 생성 > git init > git add . > git commit -m "first commit" > git remote add origin [저장소 주소] > git branch -M main > git push origin main)  

<img src="https://i.ibb.co/0Kt0Gtg/image.png" alt="image" border="0">

그러면 이제 push 된 파일인 index.html이 보인다.

- 브랜치를 하나 더 만든다. (main의 복사본, main은 실제 돌아가는 웹이라면 다른 브랜치는 이제 리더가 코드들을 확인하고 병합시켜주는 용도, main은 완벽한 코드만 올려야함)

git checkout -b dev 
   
<img src="https://i.ibb.co/Cz4y1v6/image.png" alt="image" border="0">  
  
새로운 branch로 변경이 된다.  

git push --set-upstream origin dev 

로컬에서 만든 branch를 github에 올려준다.

<img src="https://i.ibb.co/RyDVqzL/image.png" alt="image" border="0">  
  
그럼 github에도 브랜치가 하나 더 생긴다.  
main브랜치에 코드를 막 push하고 수정 할 수 없도록 막아야한다.

<img src="https://i.ibb.co/9G6yvGh/image.png" alt="image" border="0">  

사진의 체크 박스 두개를 체크한다.

- actions 옆의 projects를 클릭 

<img src="https://i.ibb.co/H4CkDGF/image.png" alt="image" border="0">  

프로젝트 클릭해서 들어가면 테마 선택이 가능 일단 심플한 보드 테마를 선택하면 위의 사진 처럼 todo, in progress, done이 보인다.  
todo아래에 add item버튼이 존재함 클릭하고 글 적고 엔터 누르면 아래 사진처럼 추가됨  
<img src="https://i.ibb.co/3sfchCN/image.png" alt="image" border="0">

todo에 있는걸 in progress로 드래그앤드롬해서 feature A이거를 옮김   
<img src="https://i.ibb.co/P9KBGrR/image.png" alt="image" border="0">  

그리고 feature A를 클릭하면 
<img src="https://i.ibb.co/Yp4bDdP/image.png" alt="image" border="0">  
사진과 같이됨 그럼 저기에 컨벌트 투 이슈 클릭하고 리포지토리 클릭하면 깃 이슈로 넘어감 

<img src="https://i.ibb.co/gzzxThF/image.png" alt="image" border="0">  

제목 옆의 #1을 클릭하면 

<img src="https://i.ibb.co/WnsmzFn/image.png" alt="image" border="0">

위의 사진 같은 창으로 넘어감.  
그럼 오른쪽의 Development의 create a branch를 클릭 > 브랜치 생성가능   
<img src="https://i.ibb.co/ypRQc6z/image.png" alt="image" border="0">  

해야하는 개발에 따라 브랜치 생성을 할 수 있음. 각각의 개발 리스트가 어떤 브랜치랑 연결되어있는지 확인이 가능.  

<img src="https://i.ibb.co/7gSH3J5/image.png" alt="image" border="0"> 
feature A의 브랜치는 개인 연습장이라고 생각하면 됨 
<img src="https://i.ibb.co/NCskMNN/image.png" alt="image" border="0">  

개인연습장에(feature A) 쓴 뒤 dev브랜치로 옮기고 dev가 완벽해지면 main브랜치로 옮김.
copy아이콘 밑에 change branch source를 클릭 > main이 아닌 dev에서 가져오기 (가장 최신이기때문, 사람들이 다 여기로 올릴거니까)
<img src="https://i.ibb.co/GnV5Hzv/image.png" alt="image" border="0">  

생성해주면  
<img src="https://i.ibb.co/6sJ9P1h/image.png" alt="image" border="0">  

명령어가 나옴 이걸 그대로 복붙 

<img src="https://i.ibb.co/kyvdjGD/image.png" alt="image" border="0">  

그럼 feature A 로 변경이 됨 브랜치가.  
이렇게까지하면 스크럼 마스터로 기초세팅이 완료된거. A기능을 만들어야함 

### 팀원

- 팀리더의 저장소를 clone해옴.  
(git clone https://github.com/qkrwldns/team.git)

- 열면 main 브랜치 코드가 그대로 존재.

- 저장소의 프로젝트에 가서 feature B를 클릭하고 컨벌트 한뒤 위의 순서대로 브랜치 하나 생성 feature B 로. (dev로부터 가져오기)

- 명령어 복사해서 clone 한 프로젝트의 터미널에 붙여넣기 

- 그럼 이제 브랜치가 feature B라는 브랜치가 되고 거기서 작업이 가능 

- 코드를 고치고 작업올리기.(git add . > git commit -m "feature B" > git push)

- 깃허브의 저장소로 가서 브랜치를 보면 main, dev, feature A, feature B가 존재함.  
feature B로 변경하고 파일을 클릭하면 방금 팀원이 push한 코드가 들어있음 

- 이제 방금 push한걸 dev브랜치로 보낼거임 (풀리퀘스트(PR) 만들기)

<img src="https://i.ibb.co/ng75Tpj/image.png" alt="image" border="0">  
여기 오른쪽 초록 버튼 클릭

<img src="https://i.ibb.co/fSpKVJh/image.png" alt="image" border="0">  

feature A로 되어있지만 feature B라는 가정. 위에 B에서 dev로 보낸다고 compare에 A이고 base는 dev브랜치로 설정하고 create pull request 버튼 클릭 

<img src="https://i.ibb.co/Qd7tqjc/image.png" alt="image" border="0">  
메시지 적고 (무슨 작업을 했는지 등등) 초록 버튼 클릭  

<img src="https://i.ibb.co/ZGRpnxn/image.png" alt="image" border="0">  

리퀘스트 요청했음.   


### 팀리더 

- 이제 스크럼 마스터가 저기 checks옆에 files changed를 클릭해서 뭐가 바뀌었는지 확인 
<img src="https://i.ibb.co/F4TRPXX/image.png" alt="image" border="0">    
<img src="https://i.ibb.co/t81KSMT/image.png" alt="image" border="0">  
파란 버튼 클릭후 메세지 작성 후 초록버튼 
<img src="https://i.ibb.co/PTKYwmN/image.png" alt="image" border="0">  
코드가 괜찮다면 오른쪽에 피니쉬 리뷰 클릭후 approve체크 후 submit하기(이 코드는 문제없다 dev보내자) 만약 request changes를 체크하고 submit하면 이 코드 좀 아닌것같아 처음부터 다시해 이런거   이렇게 되면 그 코드는 dev에 보낼 수 없음 막은 팀장이나 팀원한테 가서 사정사정해야함   
<img src="https://i.ibb.co/f0xNySt/image.png" alt="image" border="0">

- 팀원이 다시 a로 바꿔서 add . > commit -m > push 했음 
<img src="https://i.ibb.co/C9V0x9v/image.png" alt="image" border="0">
그럼 다시 코드가 바뀌게 (리뷰했던것도 사라짐. 코드가 바꼈기 때문)
<img src="https://i.ibb.co/4sh44xY/image.png" alt="image" border="0">
승인을 하면  
<img src="https://i.ibb.co/L0PVFKm/image.png" alt="image" border="0">
이런식으로 승인했다고 됨(팀원들(팀리더)이 코드 리뷰)  

- 승인 받은 코드 팀원이 병합하기
<img src="https://i.ibb.co/RvxQ4M8/image.png" alt="image" border="0">
그럼 이렇게 병합됐다고 뜸 보라색으로.
다시 프로젝트 저장소에 가서 dev로 감  
<img src="https://i.ibb.co/RBcFgHM/image.png" alt="image" border="0">  
<img src="https://i.ibb.co/r02QVPZ/image.png" alt="image" border="0">  
그럼 저기 코드가 보임 dev에. lower a로 마지막으로 한거.

### 충돌

- 팀원1이 feature A를 컨펌받아서 dev 브랜치에 병합하고 팀원2가 feature B를 만들고 push 하면 feature B 브랜치에! 그럼 또 PR을 하고 승인을 받으면 dev에 가겠구나 했음.

- 근데 conflicting files 가 뜸. 왜냐?
이미 팀원1이 dev에 병합했기때문에 팀원2는 업데이트 되지 않은 dev 브랜치에 병합하려고 해서 그럼.

- 그래서 해결방안을 제시하는것중에 github에서 고치던가 CL에서 고치던가하라고 되어있음 CL에서 하는게 나음 그거 클릭시 명령어들을 보여줌
<img src="https://i.ibb.co/LvDM7ZT/image.png" alt="image" border="0">

- dev브랜치의 최신코드를 가져와서 충돌해결하기   
(git checkout dev > git pull origin dev > git checkou - (마이너스로 하면 dev직전의 브랜치로 감) > git merge dev(새로받은 dev브랜치와 내 브랜치랑 합치는 작업하기 로컬에서 정리된 코드를 다시 dev로 올리기))  
<img src="https://i.ibb.co/54bWDG5/image.png" alt="image" border="0">
merge하면 이제 뭐가 먼저가 될지를 정할 수 있음, 팀원이랑 뭐가 먼저 올지 의논하기.  
둘 다 ok면 
<img src="https://i.ibb.co/1rs34cX/image.png" alt="image" border="0">  
최종 버전이 이거라고 생각하고 npm start나 반드시 실행을 한 번 해서 코드가 잘 돌아가는지 확인.  
컨펌이 됏다면 다시 그 코드를 git add . > commit -m > push 해주기  

- 다시 리뷰 한 번 하고 승인 후(팀원이) 마스터가 승인됐네? 병합한다? 병합 dev하기 

- 그럼 a와 b가 모두 들어간 최종버전의 dev가 완성됨. 

- 다시 프로젝트로 가서 in progress 에서 done으로 드래그 앤 드롭 해주기.

- 전부 완성됐으면 main브랜치로 올림(보통 회사에서 2주 단위로 하게 됨).   
이것도 배포를 담당하는 사람이 PR(dev에서 main)로 하는거임. 

- dev에서 main으로 올리는 코드 리뷰 필수로 하고 승인 > 병합 

- 유저는 이제 최종본인 main을 볼 수 있게됨 

### 충돌 최대한 피하는 방법

<iframe width="560" height="315" src="https://www.youtube.com/embed/PGQIJE4tHAs?si=K57qVc9uHBjP9zai" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>