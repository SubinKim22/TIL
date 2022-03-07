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



## 22.02.08 

### 코사인 유사도 (추천 시스템)

```
from sklearn.metrics.pairwise import cosine_similarity

item_sim = cosine_similarity(ratings_matrix_T, ratings_matrix_T)
```



### 협업 필터링

#### 최근접 이웃 기반

* 사용자 기반 : 특정 **사용자**와 비슷한 고객들을 기반으로 그들이 선호하는 다른 상품을 추천

* 아이템 기반 : 특정 **상품**과 유사한 좋은 평가를 받은 다른 비슷한 상품을 추천

  * 아이템 기반 협업 필터링이 더 선호되는 방법

  * 구현 순서

    1. 사용자-아이템 행렬 데이터를 아이템-사용자 행렬 데이터로 변환(전치)

    2. 아이템간의 코사인 유사도로 아이템 유사도 산출

    3. 사용자가 구매하지 않은 아이템들 중에서 아이템간 유사도를 반영한 예측 점수 계산

       ```
       def predict_rating(ratings_arr, item_sim_arr):
           ratings_pred = ratings_arr.dot(item_sim_arr)/ np.array([np.abs(item_sim_arr).sum(axis=1)])
           return ratings_pred
           
          
       # 원본 값 ratings * 코사인유사도값 
       ratings_pred = predict_rating(ratings_matrix.values , item_sim_df.values)
       ```

       

    4. 예측 점수가 가장 높은 순으로 아이템 추천



## 22.02.15

### 취업특강

* 자세한 내용은 노션, 메모장 확인



## 22.02.16

### 알고리즘 특강 1일차

#### 효율적인 알고리즘 작성

1. **for - if**

```
houses = [0, 0, 0, 0, 0, 0, 0, 1, 0, 0]

ready = True  # 기본 가정 : 

for house in houses:
    if house == 1:
        ready = False
        break  # if문에도 break 가능! => 바로 끝나버리기 때문에 효율적이다.

print(ready)
```



2. **min 함수 만들기**

```
nums = [1, 5 ,77, 26, 33, 2, 6, 16, 55]

min_num = nums[0] # 리스트 속 처음 숫자를 시작으로 잡음.

for num in nums:
    if num <= min_num:
        min_num = num

print(min_num)


-------------------------------
# 조금 더 효율적으로 ( 등호 제거, 첫 요소 뽑았으므로 비교 안해도 됨)

nums = [1, 5 ,77, 26, 33, 2, 6, 16, 55]

min_num = nums[0] # 리스트 속 처음 숫자를 시작으로 잡음.

for num in nums[1:]:
    if num < min_num:
        min_num = num

print(min_num)
```





## 22.02.17

### 알고리즘 특강 2일차

1. **map 함수 + input**

```
nums_list = list(map(int, input().split()))

nums_list
```

* str타입의 띄어쓰기를 포함한 input을 줄 때, 이를 리스트화 하는 방법 
  * ex)  1 2 3 4 5     =>     [1,2,3,4,5]



#### swea 문제

1. **min-max**

```
T = int(input())

for rep in range(T) :
    
    N = int(input())

    nums_list = list(map(int, input().split()))

    max_num = nums_list[0]
    min_num = nums_list[0]


    for num in nums_list[1:] :
        if num > max_num :
            max_num = num

        if num < min_num :
            min_num = num

    print('#{} {}'.format(rep + 1, max_num - min_num))
```



2. **숫자카드**

```
T = int(input())

for rep in range(T) :
    
    N = int(input())

    card_list = list(map(int,input()))

    card_count = [0] * 10

    for num in card_list:
        card_count[num] += 1


    max_card_index = 0
    max_card_num = 0

    for idx, value in enumerate(card_count) :
        if value >= max_card_num :
            max_card_num = value
            max_card_index = idx
    print('#{} {} {}'.format(rep + 1, max_card_index, max_card_num))
```



3. **구간합**

````
T = int(input())

for rep in range(T) :
    
    N , M = map(int,input().split())   # map함수 써서 동시에 주기

    nums_list = list(map(int, input().split()))

    max_num_sum = 0                    # 처음 합으로 줘도 되지만 그냥 0으로 줌
    min_num_sum = sum(nums_list[:M])  # 0주면 안되서 처음 합으로 줌

    for i in range(len(nums_list)-M+1) :  # 구간 때문에 길이 계산
        
        selection_sum = sum(nums_list[i:i+M])
        
        if selection_sum > max_num_sum :
            max_num_sum = selection_sum  

        if selection_sum < min_num_sum :
            min_num_sum = selection_sum

    print('#{} {}'.format(rep + 1, max_num_sum - min_num_sum))
````







## 22.02.18

#### 알고리즘 특강 3일차

1. 구슬치기 게임

```
T = int(input())

for rep in range(T) :
   
    num_list = list(map(int,input().split()))
    
    count_dict = dict()

    for num in num_list:
        if not count_dict.get(num) :     # not none  =>  True !!!
            count_dict[num] = 1
        else :
            count_dict[num] += 1

    Kkakdugi = 0

    for key, _ in count_dict.items() :   # value는 필요없으므로 _ 처리
        if count_dict[key] == 1 :
            Kkakdugi = key

    print('#{} {}'.format(rep + 1, Kkakdugi))
```



2. 세로로 말해요

```
T = int(input())

for rep in range(T):
    
    string = []
    vertical_string = ""
    
    for i in range(5):
        input_str = input()
        string.append(input_str)

    max_len = 0
    
    for k in string:
        if len(k) > max_len:
            max_len = len(k)

    for c in range(max_len):
        for r in range(len(string)):
            try:
                vertical_string += string[r][c]
            except:
                pass

    print("#{} {}".format(rep + 1, vertical_string))
```

```
# 리스트 컴프리헨션
string = [input() for i in range(5)]
vertical_string = ""
max_len = max(len(k) for k in string)

for c in range(max_len):
    for r in range(len(string)):
        try:
            vertical_string += string[r][c]
        except:
            pass

print(vertical_string)
```

```
# try-except 없이 코드짜기 => 애초에 if문으로 길이가 짧은 문자열은 아예 추가가 안되게함.
T = int(input())

for rep in range(T):
    words = [input() for _ in range(5)]
    max_len = max(len(word) for word in words)  # 가장 긴 문자열을 기준으로 설정
    vertical_string = ""

    for i in range(max_len):
        for word in words:
            if i < len(word):  # 길이가 짧은 문자열에 대해 에러 방지
                vertical_string += word[i]

    print(f"#{rep+1} {vertical_string}")
```





## 22.02.22

### 딥러닝의 이해

```
import tensorflow as tf
import keras

# 딥러닝에 필요한 케라스 함수 호출
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

import numpy as np
import tensorflow as tf

np.random.seed(1)
tf.random.set_seed(1)

Data_set = np.loadtxt('dataset/ThoraricSurgery.csv', delimiter = ",")
Data_set.shape

X = Data_set[:,0:17]
Y = Data_set[:,17]

# 딥러닝 모델 구조 설정(2개층, 속성(독립변수,피처)이 17개 input값, 
#                      relu와 sigmoid 활성화 함수 이용)
model = Sequential()
model.add(Dense(30, input_dim = 17, activation = 'relu'))
model.add(Dense(1, activation = 'sigmoid'))

# 딥러닝 실행(오차함수는 교차엔트로피, 최적화함수는 adam)
# 교차엔트로피 : 이진분류에서 사용
model.compile(loss = 'binary_crossentropy', optimizer = 'adam', metrics = ['accuracy'])
model.fit(X,Y, epochs = 100, batch_size = 10)

------------------------------------------------------------------------------------------------------------

# 만들어진 모델 저장
model.save('predict_model.h5')

# 케라스 함수 호출
from keras.models import load_model

# test 데이터 호출
Dataset_test = np.loadtxt('text.csv', delimiter = ",")
X_test = Dataset_test[:,0:17]
Y_result = []

# 모델 불러오기
model = load_model('predict_model.h5')

# 모델 적합  =>  모델 저장 안하고 변수 지정 후 사용할 수 있을듯?
Y_result = model.predict_classes(X_test)
```



#### 역전파 (Back-propagation)

![image-20220222154142755](https://user-images.githubusercontent.com/98443426/155079281-94563081-8c83-48df-8247-85f5cb1c8e21.png)





## 22.02.23

### 딥러닝의 이해

#### 과적합

![image](https://user-images.githubusercontent.com/98443426/155302272-836ad410-003f-49a5-af1c-903c38dc04f0.png)



* 과적합은 층이 너무 많을 때, 변수가 복잡할 때, 테스트셋과 학습셋이 중복될 때 생기기도 함
* 예제는 project -> rice/wine 예제 -> 02.23 커밋 확인





## 22.02.24

### 딥러닝을 이용한 자연어 처리

#### 토큰화

> 입력된 텍스트를 잘게 나누는 과정, 텍스트(문장)를 단어별, 문장별, 형태소별로 나눌 수 있는데, 나누어져서 의미가 있는 단위로 만듬

```
from tensorflow.keras.preprocessing.text import text_to_word_sequence
 
text = '해보지 않으면 해낼 수 없다'

result = text_to_word_sequence(text)
print("\n원문:\n", text)
print("\n토큰화:\n", result) 

---------------------------------

원문:
 해보지 않으면 해낼 수 없다

토큰화:
 ['해보지', '않으면', '해낼', '수', '없다']
```





## 22.02.25

### 딥러닝을 이용한 자연어 처리

#### 워드 임베딩

* one-hot-encoding을 사용하면 벡터의 길이가 너무 길어지는 단점
* 공간적 낭비를 해결하기 위해 등장한 것이 **워드 임베딩**
  * 워드 임베딩으로 얻은 결과는 밀집된 정보를 가짐
  * 각 단어간의 유사도 계산 가능
  * `Embedding(16, 4, input_length=2)` : 총 입력되는 단어 수는 16개, 임베딩 후 출력되는 벡터 크기는 4,
                                                                            단어를 매번 2개씩 집어 넣겠다는 뜻



#### 패딩(padding)

* 문장의 단어 수를 똑같이 맞추는 작업

  * `pad_sequence(x, n)` : 원하는 길이보다 짧은 부분은 숫자 0, 긴 데이터는 자름

    ​                                          서로 다른 길이의 데이터 x를 길이 4로 맞춰줌 





## 22.03.02

#### 정규표현식

* Sublime Text에서 사용
* 다시 한번 복습
* 파이썬에서 사용하는 방법은 project - fifa22 확인

![11](https://user-images.githubusercontent.com/98443426/156312269-05bb0c26-27a7-4412-a5f2-b95a9e4ce3eb.png)

* 카드번호 16자리 인식

  ^[0-9]{4}\ㅡ[0-9]{4}\ㅡ[0-9]{4}\ㅡ[0-9]{4}$





## 22.03.07

### SQL 기본문법

```
show databases;

show databases like "s%";
show databases like "%s";
show databases like "%a%";

use world;

select database();

show tables;

SELECT name FROM country;
SELECT name, gnp FROM country;

SELECT * FROM country;

SELECT name, continent FROM country ORDER BY name;

# 중복 제거
SELECT DISTINCT Isofficial FROM countrylanguage;

SELECT count(code) FROM country;
SELECT count(code), count(name) FROM country;

SELECT count(DISTINCT IsOfficial) AS counting FROM countrylanguage;

#조건
SELECT name, continent, population FROM country
WHERE continent='Asia' AND name='South Korea';

#조건 + 상위10개
select name, continent, surfacearea/population as surareapop from country
where continent='Asia' order by surareapop desc
limit 10;

#if-else문
CASE WHEN [조건1] THEN [결과1]
     WHEN [조건2] THEN [결과2]
     ELSE [결과3]
END AS 새로운컬럼명
```

