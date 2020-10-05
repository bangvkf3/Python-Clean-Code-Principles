# Python-Clean-Code-Principles

Clean code principles for Python



## PEP-8(summary)

> Coding conventions for the Python



### Code layouts

- Use **4 spaces** per indentation level

  - Tab과 Space의 조합은 문법적 오류를 야기하기 때문에 함께 사용하지 말 것

- Limit all lines to a maximum of **79 characters**

  - 에디터에서 여러 창 동시작업 시 가독성 향상

- Surround top-level function and class definitions with **two blank lines**

  - Method definitions inside a class are surrounded by a **single blank line**

- 소스파일 엔코딩 : UTF-8

- Imports should usually be on separate lines

  ```python
  # Correct:
  import os
  import sys
  ```

  ```python
  # Wrong:
  import sys, os
  ```

  - 아래의 경우는 괜찮다

    ```python
    # Correct:
    from subprocess import Popen, PIPE
    ```

- 공백

  - 다음과 같은 상황에서 여분의 공백 문자을 피한다

    - 괄호, 중괄호, 대괄호

    ```python
    # Correct:
    spam(ham[1], {eggs: 2})
    ```

    ```python
    # Wrong:
    spam( ham[ 1 ], { eggs: 2 } )
    ```

    - 콤마와 괄호 사이

    ```python
    # Correct:
    foo = (0,)
    ```

    ```python
    # Wrong:
    bar = (0, )
    ```

    - 콤마, 세미콜론, 콜론 직전

    ```python
    # Correct:
    if x == 4: print x, y; x, y = y, x
    ```

    ```python
    # Wrong:
    if x == 4 : print x , y ; x , y = y , x
    ```

    - 항상 이진연산자 양 옆에 한 개의 공백을 넣는다

    ```python
    # Correct:
    i = i + 1
    submitted += 1
    x = x*2 - 1
    hypot2 = x*x + y*y
    c = (a+b) * (a-b)
    ```

    ```python
    # Wrong:
    i=i+1
    submitted +=1
    x = x * 2 - 1
    hypot2 = x * x + y * y
    c = (a + b) * (a - b)
    ```

    - 키워드 인수 혹은 기본 매개변수의 경우 `=` 양 옆에 공백을 사용하지 않는다

    ```python
    # Correct:
    def complex(real, imag=0.0):
        return magic(r=real, i=imag)
    ```

    ```python
    # Wrong:
    def complex(real, imag = 0.0):
        return magic(r = real, i = imag)
    ```

    

### Comment

- 코드와 반대되는 주석은 없는 편이 낫다.

- 항상 최신 상태 유지

- 주석은 완전한 문장이어야하며, 첫 번째 단어를 대문자로 적는다.

- Python coders from non-English speaking countries: please write your comments in English, unless you are 120% sure that the code will never be read by people who don't speak your language.

- 인라인 주석

  - 최대한 자제(뻔한 내용 등 사용하지 말 것)

  ```python
  x = x + 1  # Increment x (bad)
  
  x = x + 1  # Compensate for border (Sometimes, this is useful)
  ```

  - 코드라인 끝에 두 개의 스페이스를 사용



### Naming conventions

- 패키지와 모듈
  - **짧은 소문자**인 이름을 가져야한다
  - 언더스코어 사용 가능
- 클래스, 예외
  - CamelCase
- 함수, 변수
  - lowercase_underscore
- Non-public 메서드, Non-public 인스턴스 변수
  - \_leading_underscore
- 모듈 레벨 상수
  - ALL_CAPS



### Programming Recommendations

- None에 대한 비교는 비교 연산자가 아니라 반드시  `is `, `is not` 을 이용한다.

- boolean 값을 `==` 를 사용해 비교하지 않는다.

  ```python
  # Correct:
  if greeting:
  ```

  ```python
  # Wrong:
  if greeting == True:
  ```

  ```python
  # Worse:
  if greeting is True:
  ```

- `return` 구문에서 일관성을 유지한다

  - 반환 값이 없으면 `return None` 명시
  - 함수의 끝에 도달할 수 있다면 explicit return 구문 표기

  ```python
  # Correct:
  
  def foo(x):
      if x >= 0:
          return math.sqrt(x)
      else:
          return None
  
  def bar(x):
      if x < 0:
          return None
      return math.sqrt(x)
  ```

  ```python
  # Wrong:
  
  def foo(x):
      if x >= 0:
          return math.sqrt(x)
  
  def bar(x):
      if x < 0:
          return
      return math.sqrt(x)
  ```

- 항상 파일의 맨 위에 import 문을 놓는다.

- import 구문은 다음 순서에 따라 기술

  > 각 그룹 사이에는 빈 줄을 넣는 것이 좋다

  - 표준 라이브러리
  - 관련된 서드파티
  - 로컬 어플리케이션, 자체 라이브러리

- 모듈의 import는 절대 경로 방식이 권장된다.