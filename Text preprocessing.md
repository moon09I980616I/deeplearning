# 2. 텍스트 전처리

풀고자 하는 문제의 용도에 맞게 텍스트를 사전에 처리하는 작업

자연어 처리에서 크롤링으로 얻어낸 코퍼스 데이터가 필요에 맞게 전처리 되지 않은 상태라면, 해당 데이터를 사용하고자하는 용도에 맞게 토큰화 & 정제 & 정규화 한다.

# 토큰화

주어진 코퍼스에서 토큰이라 불리는 단위로 나누는 작업을 토큰화라고 한다. 토큰의 단위가 상황에 따라 다르지만, 보통 의미있는 단위로 토큰 정의

### 단어 토큰화

토큰의 기준을 단어로 하는 경우

단어는 단어 단위 외에도 단어구, 의미를 갖는 문자열로 간주되기도 함

[구두점을 지운 뒤 띄어쓰기를 기준으로 잘라 낸 토큰화 작업]

<aside>
💡 입력: **Time is an illusion. Lunchtime double so!**

출력 : "Time", "is", "an", "illustion", "Lunchtime", "double", "so”

</aside>

### 토큰화에서 고려해야 할 사항

1. 구두점이나 특수 문자를 단순 제외하면 안된다.
2. 줄임말과 단어 내에 띄어쓰기가 있는 경우
3. 표준 토큰화 예제 찾아보기

# 정제, 정규화

토큰화 작업 전, 후에 텍스트 데이터를 용도에 맞게 정제 및 정규화

정제 : 보유하고 있는 코퍼스로부터 노이즈 데이터 제거

정규화 : 표현 방법이 다른 단어들을 통합시켜 같은 단어로 제공

1. 규칙에 기반한 표기가 다른 단어들의 통합
2. 불필요한 단어의 제거
    
    등장 빈도가 적은 단어 - 분류에 도움이 되지 않음
    
3. 정규 표현식

# 표제어 추출, 어간 추출

1. 표제어(기본 사전형 단어) 추출
    
    단어의 형태학적 파싱을 먼저 진행
    

<aside>
💡 형태소
어간 : 단어의 의미를 담고 있는 단어의 핵심 부분
접사 : 단어에 추가적인 의미를 주는 부분

</aside>

1. 어간 추출
    
    형태학적 분석을 단순화한 버전
    정해진 규칙만 보고 단어의 어미를 자르는 어림짐작의 작업
    

## 한국어 어간 추출

5언 9품사의 구조를 가진 한국어

| 언 | 품사 |
| --- | --- |
| 체언 | 명사, 대명사, 수사 |
| 수식언 | 관형사, 부사 |
| 관계언 | 조사 |
| 독립언 | 감탄사 |
| 용언 | 동사, 형용사 |

이 중 용언에 해당되는 동사와 형용사는 어간과 어미의 결합으로 구성

### 활용

어간(stem)이 어미(ending)를 가지는 일

**어간(stem)**
 : 용언(동사, 형용사)을 활용할 때, 원칙적으로 모양이 변하지 않는 부분. 활용에서 어미에 선행하는 부분. 때론 어간의 모양도 바뀔 수 있음(예: 긋다, 긋고, 그어서, 그어라).

**어미(ending)**
: 용언의 어간 뒤에 붙어서 활용하면서 변하는 부분이며, 여러 문법적 기능을 수행

활용은 어간이 어미를 취할 때, 어간의 모습이 일정하다면 규칙 활용, 어간이나 어미의 모습이 변하는 불규칙 활용

### 규칙 활용

어간이 어미를 취할 때, 어간의 모습이 일정하다.

잡/어간 +다/어미

### 불규칙 활용

불규칙 활용은 어간이 어미를 취할 때 어간의 모습이 바뀌거나 취하는 어미가 특수한 어미일 경우

예를 들어 ‘듣-, 돕-, 곱-, 잇-, 오르-, 노랗-’ 등이 ‘듣/들-, 돕/도우-, 곱/고우-, 잇/이-, 올/올-, 노랗/노라-’와 같이 어간의 형식이 달라지는 일이 있거나 ‘오르+ 아/어→올라, 하+아/어→하여, 이르+아/어→이르러, 푸르+아/어→푸르러’와 같이 일반적인 어미가 아닌 특수한 어미를 취하는 경우 불규칙활용을 하는 예

# 불용어

갖고 있는 데이터에서 유의미한 단어 토큰만을 선별하기 위해서는 큰 의미가 없는 단어 토큰을 제거하는 작업

# ****정규 표현식****

# 정수 인코딩

단어 등장 빈도수를 기준으로 정렬 한 뒤 가지고 있는 텍스트에 숫자 부여

https://wikidocs.net/31766

# 패딩

각 문장은 서로 길이가 다를 수 있다.

기계는 길이가 전부 동일한 문서들에 대해서는 하나의 행렬로 보고 한꺼번에 묶어서 처리 할 수 있다.

병렬 연산을 위해서 여러 문장의 길이를 임의로 동일하게 맞춰주는 작업이 필요하다.

https://wikidocs.net/83544

# One-Hot Encoding

원-핫 인코딩(One-Hot Encoding)

- 단어 집합의 크기를 벡터의 차원으로 하고 표현하고 싶은 단어의 인덱스에 1의 값을 부여하고 다른 인덱스에는 0을 부여하는 단어의 벡터 표현 방식
1. 정수 인코딩 수행 - 각 단어에 고유한 정수 부여
2. 표현하고 싶은 단어의 고유한 정수를 인덱스로 간주하고 해당 위치에 1, 다른 단어의 인덱스 위치에는 0을 부여

```jsx
from konlpy.tag import Okt  

okt = Okt()  
tokens = okt.morphs("나는 자연어 처리를 배운다")  
print(tokens)
```

`['나', '는', '자연어', '처리', '를', '배운다']`

```jsx
word_to_index = {word : index for index, word in enumerate(tokens)}
print('단어 집합 :',word_to_index)
```

`단어 집합 : {'나': 0, '는': 1, '자연어': 2, '처리': 3, '를': 4, '배운다': 5}`

```jsx
def one_hot_encoding(word, word_to_index):
  one_hot_vector = [0]*(len(word_to_index))
  index = word_to_index[word]
  one_hot_vector[index] = 1
  return one_hot_vector

one_hot_encoding("자연어", word_to_index)
```

`[0, 0, 1, 0, 0, 0]`
