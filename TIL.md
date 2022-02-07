# 깃허브 특강

## 1일차



### CLI

- git bash 열 때 홈 폴더(계정 폴더) 꼭 확인하기 : ~(틸드) 뒤에 아무것도 없는지 확인

- bash 명령어 

  touch => 파일 생성, 여러개도 한번에 가능

  mkdir => 폴더 생성

  ls => 현재 작업 중인 디렉토리 내의 파일 / 폴더 다 보여줌

  ​		ls -a : 숨김파일까지 

  ​		ls -al : 수정날짜 등 정보까지

  cd => 홈 폴더로 이동
  cd 폴더명 => 그 폴더로 이동 
  cd .. => 현재 폴더 기준 하나 상위로 이동
  mv => 이름바꾸기 (a.txt -> b.txt)
             이동하기 (b.txt를 test2로)
  
  rm => 폴더/파일 지우는 명령어
  
  ​			*(asterisk, wildcard)를 사용해서 rm *.txt처럼 파일 전체 삭제



### 마크다운(Markdown) 문법



#### #의 사용

> 주피터노트북처럼 #을 사용할 수 있음. 다만 글씨 크기만을 위해 사용하는 것이 아닌 목차를  표시하는 용도로 사용.



#### 인용구

> `>`  + 문자 : 인용구 (설명 쓸때 사용하면 좋을 듯)



#### list (순서 표시)

1. 순서가 있는 목록

​	`1.` 누르면 바로 가능 / 줄바꾸면 자동 넘버링

2. 순서가 없는 목록

* (별 + 스페이스)
  * ( -   +  스페이스)도 가능



#### 글 블럭화

> `백틱으로 감싸면 인라인 블럭`
>
> ``백틱 세개 + python` 하면 블럭안에 코드 넣기 가능

```python
for i in range(10):
    print(i)
```



#### 링크 및 이미지 삽입

* 이미지 넣기
  * `![]()`  -> [이미지 파일의 이름] (이미지 주소)
  * 복붙해서 넣기

- 링크 넣기
  - [링크 이름] (링크 사이트)
  - [네이버](http://naver.com/)



#### 줄 바꿈 및 글자 

- 수평선
  -  `---` 하면 생김

---

* 이탤릭체
  * ` * 또는 _ ` 로 감싸준다
  * 이것은 *이탤릭체*  입니다.
* 보드체 ( 굵게 )
  * `** 또는 __` 로 감싸준다
  * 이것은 **보드체** 입니다.
* 취소선
  * `~~` 로 감싸준다.
  * 이것은 ~~취소선~~ 입니다.



#### 테이블 

* `ctrl + t` 로 테이블(표) 만들기 가능

|      |      |
| ---- | ---- |
|      |      |

* `|` (파이프) 사이에 컬럼을 작성 후 엔터
  * `ctrl + /` 로 자세한 내용 확인

| working directory | statging area | remoe repo |
| ----------------- | ------------- | ---------- |
| working tree      | index         | history    |
| working copy      | cache         | tree       |
|                   |               |            |





---


## 2일차



### git 명령어 정리

#### 1.  git init

   > 현재 폴더를 git이 관리하는 폴더로 만들어줘!

   * **홈 디렉토리에서 기입하지 않는다!** (~~홈 디렉토리에서 하면 대참사~~)
   * 최소 1회만 기입
   * vscode 왼쪽 위 파일에 U로 바뀜



#### 2.  git status

   > 현 상황을 알고싶어!

   * 언제든 현 상황을 볼 수 있음
   * 파일 안 올라간 상태면 빨간색
   * 파일 올라간 상태면 초록색



#### 3.  git add

   > 파일을 올려줘!

   * `git add 파일명`   <- 이런 형태로 파일 올림

   * vscode 왼쪽 위 파일에 A로 바뀜

   * `git add .`     <-  디렉토리 내 파일 전부 다 올림

   * `git rm --cached a.txt`   <- add한 것 삭제

     ```
     *참고
     touch .gitignore
     안에 파일명 적어주면 git add . 할 때 그 파일은 안올라감! (개인 정보같은 민감한 정보)
     하지만 이미 add 된 파일엔 해당안되니까 add전에 설정할 것.
     gitignore.io에서 만들 수 있음. 숨겨진 .init 파일과 같이 있으면 됨.(작업 디렉토리 최상단)
     ```

     


#### 4.  git commit -m "메시지"

   > 찰칵! 후 저장소 저장

   * 메시지 부분에 제목을 기입하면 됨

     ```
     *참고
     git commit만 했을 시 뜨는 무시무시한 화면 (VIM editor)
      i눌러서 끼워넣기 모드로 변경 -> 메시지 적기 -> esc -> :wq 후 엔터
     ```

* `git commit --amend` : 메시지 잘못 적었을 시 해결방안, VIM editor에서 동일하게 적용




#### 5.  git log

   > 버전들을 확인할래!

   * 기본 정보들 제공
* `git log --oneline` : 간단하게 한줄로 로그값 요약(앞자리 7개, 이름 정도만)



#### 6.  git checkout

   > 과거로 잠깐 돌아가고 싶어!

   * 과거로 되돌리는 것이 아님
   * `git checkout master` 하면 복구
   * `git checkout head~n` : n만큼 전으로 

   

#### 7. git remote add origin 주소

> 내 컴퓨터 로컬환경과 깃허브 브릿지 잇기!

* `git remote -v` : 연결 주소 확인
* `git remote rm origin` : 연결 주소 지우기 (연결 끊기)



#### 8. git push origin master

> 올리기!



#### 9. git clone 주소

> github의 repository주소를 입력해 작업 디렉토리에 폴더 만들기!

* 타인과 협력 시 먼저 만들어 놨을 때 이어 받기 유용함
* 홈 디렉토리에서 가능(<-> git init) : 홈 디렉토리에 폴더를 만들고 init하는 과정이므로 결과는 같다.
* 이미 주소가 딸려온다 (git remote add origin 안해도 됨)



#### 10. git pull origin master

> 내용물 받기!

* pull / push로 타인과 협력 가능
* 새로운 폴더에 내용물을 받으려면 먼저 init을 하고 git remote add origin 주소 후 pull하면 된다.



---

## 3일차 



### 충돌 오류

```
error: failed to push some refs to 'https://github.com/SubinKim22/relay.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

* 원인
  * README 파일의 유무
  * github에서 연필 모양 아이콘으로 수정했을 때 vscode에서 git 오류



* 해결 방안
  * `git push -u origin +master` : README.md 파일 삭제해버림. 별로 좋지 않은 것 같다.
  * `git pull origin master` 해서 선택지 선택 후 다시 add - commit - push하는 순.





### branch : 브랜치 명령어 정리

#### 1. git branch

> 브랜치 목록 확인. 



#### 2. git branch 브랜치명

> 브랜치명으로 브랜치 만들기

* master branch 건드리지않고 테스트용 branch 생성
* `git branch -d 브랜치명` : 브랜치 삭제



#### 3. git switch 브랜치명

> 브랜치명으로 이동

* `git switch -c 브랜치명` : 브랜치 새로 만들기 + 이동



#### 4. git merge 브랜치명

> 브랜치 합치기

* 이 과정에서도 충돌 오류 발생할 수 있음.

```
# pull / request
github에서 clone 후 개인 branch에서 새로운 작업을 하고 git push origin master가 아닌 git push origin branch를 통해
merge를 request하고 다시 pull하는 작업
```



# TIL



## 22.02.07

### apply + lambda

```
def black(x):
    if x in ['Midnight Black','Aura Black','Prism Black']:        
        return 'Black'
    else:
        return x    
        
data['color'].apply(lambda x: black(x))
```

* 열에 함수 적용



### 레이블 인코딩(Label Encoding)

* 간단하게 문자열을 숫자형 카테고리로. 
  하지만 숫자끼리의 크고 작음의 특성이 부여되므로 ML알고리즘에서 가중치 부여될 수 있음
  트리계열(Decision / Random)을 제외한 다른 머신러닝 알고리즘에서 사용 조심해야함.
  트리계열은 대소 비교를 통해서 구분하기 때문에 숫자 단위에 크게 영향받지 않는다.



### literal_eval

```
from ast import literal_eval

코드 적용 전
'[{"id": 28, "name": "Action"}, {"id": 12, "name": "Adventure"}, {"id": 14, "name": "Fantasy"}, {"id": 878, "name": "Science Fiction"}]'

코드 적용
movies_df['genres'] = movies_df['genres'].apply(literal_eval)

코드 적용 후
[{'id': 28, 'name': 'Action'},
 {'id': 12, 'name': 'Adventure'},
 {'id': 14, 'name': 'Fantasy'},
 {'id': 878, 'name': 'Science Fiction'}]
```

* 칼럼들의 str 형태(문자형)을 list 형태로 바꿔주기
