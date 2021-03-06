# chapter3.파이 채우기 : 리스트, 튜플, 딕셔너리, 셋 

### 3-1. 리스트와 튜플

- 파이썬의 문자열은 문자의 시퀀스
- 파이썬에는 2가지 다른 시퀀스가 존재하는데 바로 튜플과 리스트임
    - 문자열과는 달리 이 2가지는 다른 타입이 될 수 있음
    - 각 요소는 어떤 객체도 될 수 있음
- 파이썬은 왜 리스트와 튜플을 모두 포함하고 있는가
    - 튜플은 불변, 항목 할당 후 바꿀 수 없음
    - 리스트는 변경 가능 , 항목 할당 후 자유롭게 수정, 삭제가 가능

### 3-2. 리스트

- 리스트는 순차적으로 데이터를 파악하는데 유용하며 내용의 순서가 바뀔 수 있음 (문자열과달리)
- **리스트는 현재 위치에서 새로운 요소를 추가하고나, 삭제, 혹은 기존 요소를 덮어쓸 수 있음 + 동일한 값 여러번 사용 가능**

- 3.2.1 리스트 생성하기 : [] 또는 list()
    - 리스트는 콤마로 구분하고 대괄호로 둘러싸여 있음
    - 또한 list() 함수로 빈 리스트 할당 가능 ⇒ emptylist=list()

- 3.2.2 다른 데이터 타입을 리스트로 변환하기 : list()
    - list() 함수는 다른 데이터 타입을 리스트로 변환함
    - list(변환할 변수명 혹은 문자열)
    - 2.3.9에서 확인한 split()함수의 경우 문자열을 구분자로 나누어 리스트로 변환함
        - 변수명.split(구분자) ⇒ 구분자로 나눠진 리스트로 반환

- 3.2.3 [오프셋] 으로 항목 얻기
    - 문자열과 마찬가지로 리스트는 오프셋을 통해 하나의 특정 값을 추출할 수 있음
        - 리스트명[오프셋]
        - 문자열과 마찬가지로 음수의 인덱스는 끝에서 거꾸로 값을 추출함
        - 리스트의 오프셋도 마찬가지로 오프셋의 범위를 넘어가는 숫자 대입 시 에러남

- 3.2.4 리스트의 리스트
    - 리스트는 리스트 뿐만 아니라 다른 타입의 요소도 포함할 수 있음
    - 리스트 안에 리스트가 있을 때 출력 예시 → all_birds[1][0] = all_birds 리스트의 두번째 값(리스트)의 첫번째 값 호출

- 3.2.5 [오프셋] 으로 항목 바꾸기
    - 오프셋으로 항목을 얻어 바꿀 수 있음
    - marxes[3]=새로운 값 → marxes[3]의 값이 새로운 값으로 변경됨
    - 단, 리스트의 오프셋이 리스트에서 유효한 위치여야 함
    - 문자열은 이러한 방식으로 변경할 수 없음 (불변이기 때문에)
    - 리스트는 가변이기때문에 항목 수와 항목 내용을 바꿀 수 있음

- 3.2.6 슬라이스로 항목 추출하기
    - 슬라이스를 사용해서 리스트의 서브시퀀스 추출 가능
    - 리스트명[0:2]
    - 리스트의 슬라이스 또한 리스트, 문자열과 동일하게 스텝 이용 가능
    - 리스트명[0:4:2] → 0,2,4 출력
    - **리스트명[::-1] ⇒ 역방향 출력**

- 3.2.7 리스트 끝에 항목 추가하기 : append()
    - append() 함수는 리스트의 끝에 새 항목을 추가함
    - 리스트명.append(추가할 문자열)
    - 리스트는 변경 가능하기 때문에 추가 가능

- 3.2.8 리스트 병합하기 : extend() 또는 +=
    - 리스트명.extend(병합할 리스트명)
    - 리스트명 += 병합할 리스트명
    - append() 사용 시, 항목 병합이 아니라 병합할 리스트가 '리스트' 로 항목 추가됨
    - 병합함수는 리스트가 다른 타입의 요소를 포함할 수 있다는 것을 보여줌

- 3.2.9 오프셋과 insert()로 항목 추가하기
    - append() 함수가 그냥 맨 끝에 항목 추가라면, insert()함수는 원하는 위치에 항목 추가할 수 있음
    - insert(오프셋,삽입할 문자열)
    - insert 함수 내 오프셋 위치에 오프셋 범위가 넘어가는 숫자를 넣게 되면 에러는 나지 않고 그냥 맨 끝에 삽입됨

- 3.2.10 오프셋으로 항목 삭제하기 :del
    - del 리스트명[오프셋]
    - 오프셋으로 리스트의 특정 항목 삭제 시, 삭제된 항목 이후의 항목들이 한칸씩 앞댕겨짐, 그리고 리스트의 길이가 1 감소
    - **del 은 리스트 함수가 아닌 파이썬 구문이므로 객체명과 별도로 사용해야 함**
        - **따라서 함수 사용 방법이 리스트명.del(오프셋) 이 아니라 del 리스트명[오프셋] 인 것임**
        - del 은 할당(=) 의 반대, 객체로부터 이름을 분리하고 객체의 메모리를 비워줌

- 3.2.11 값으로 항목 삭제하기 : remove()
    - 리스트에서 삭제할 항목의 위치는 모르는데 삭제할 값은 아는 경우 사용
    - 리스트명.remove(삭제할 문자열)

- 3.2.12 오프셋으로 항목을 얻은 후 삭제하기 : pop()
    - pop()은 리스트에서 항목을 가져오는 동시에 그 항목을 원래의 리스트에서 삭제함
    - 오프셋 지정 안할 시, 자동으로 오프셋 -1 지정 → pop(-1)
    - pop(0)은 가장 첫번째 값을 반환함
    - 만약 append() 로 항목 추가 후
        - pop() 으로 다시 마지막 항목 제거 → 후입 선출 형태
        - pop(0)으로 항목 삭제 → 선입 선출 형태
- 3.2.13 값으로 항목 오프셋 찾기 : index()
    - 항목값의 리스트 오프셋을 알고싶다면 해당함수 사용
    - 리스트명.index(오프셋을 알고싶은 문자열)

- 3.2.14 존재 여부 확인하기 : in
    - 리스트에서 어떤 값의 존재를 확인하려면 in 사용
    - 확인하고자 하는 문자열 in 리스트명
    - 리스트에 값이 적어도 하나 이상 존재 시 TRUE  반환 (T/F 로 반환함)
    - 항목에 순서와 상관없이 리스트의 존재 여부만 확인하고자 한다면 set 은 유일한 값을 저장하고 조회하는데 있어 리스트보다 더 좋은 방법임

- 3.2.15 값 세기 : count()
    - 리스트에 특정 값이 얼마나 있는지 세기 위해서 사용
    - 리스트명.count(세고자 하는 문자열)

- 3.2.16 문자열로 변환하기 : join()
    - join() 은 문자열 메소드, 리스트 메소드가 아님, 따라서 리스트명.join() 의 형태로 사용할 수 없음
    - 리스트에서 사용할 때에는
        - 문자열에서와 동일하게 구분자.join(리스트명) 으로 사용
        - join 이 만약 리스트 메소드였다면 튜플과 문자열같은 다른 반복가능한 개체와 사용 못할것
    - join의 인자는 문자열 혹은 반복가능한 문자열의 시퀀스(리스트 포함) 임
    - 결과로 반환되는 값은 '문자열'

- 3.2.17 정렬하기 : sort()
    - sort() : 리스트 자체를 내부적으로 정렬 → 리스트 자체 변경됨
    - sorted() : 리스트의 정렬된 복사본을 반환 → 복사본의 반환이기 때문에 원래 리스트는 변화하지 않음
    - **리스트명.sort() , sorted(리스트명)**
    - 리스트의 항목이 숫자인 경우 기본적으로 오름차순, 문자열인 경우 알파벳 순으로 정렬함
    - sort() 는 리스트 내 모든 요소들이 모두 같은 타입일 경우 제대로 동작, 정수와 부동소수점수의 경우 같이 혼합되어 있어도 내부 정렬이 가능하다 ( 파이썬이 자동으로 형변환하여 항목들을 정렬하기 때문)
    - 내림차순으로 정렬하고 싶다면, reverse=True 를 인자로 추가

- 3.2.18 항목 갯수 얻기 : len()
    - len() 은 리스트의 항목 수를 반환
    - len(리스트명)

- 3.2.19 할당 : = / 복사 : copy()
    - 한 리스트를 변수 두곳에 할당하였을 경우, 변수 2개 모두 하나의 리스트를 참조하고 있기 때문에 리스트에 변경사항이 생긴다면 둘다 반영됨 (변수 할당이란, 그냥 값에 이름을 붙였다의 의미이기 때문에 같이 영향 받는 것 )
    - 또한 하기 3가지 방법으로 한 리스트를 새로운 리스트에 복사 할 수 있음
        - copy() → 복제
        - list() → 리스트로 변환
        - 슬라이스[:] → 항목 추출
        - **각 변수에 해당 함수들을 이용하여 값 할당 시, 복사본이기 때문에 원본 리스트에 변경사항이 생기더라도 복사본의 값은 변하지 않는다 (참조하는 값이 아무것도 없기 때문 / 복사본이란 그냥 새로운 객체임)**
        - 또한 반대로 복사본을 고치더라도 원본에는 영향이 없음

### 3-3. 튜플

- 리스트와 마찬가지로 튜플은 임의적인 항목의 시퀀스
- 튜플은 불변하며, 정의 후 추가, 삭제, 수정을 할 수 없음 → 즉 상수의 리스트 라고 할 수 있음

- 3.3.1 튜플 생성하기 : ()
    - 튜플의 구문은 리스트와 조금 다름 → emptytuple=()
    - 하나 이상의 요소가 있는 튜플을 만들기 위해서는 각 요소 뒤에 콤마를 붙임
        - 하나의 요소 저장 시, ⇒ newtuple = "gusta"**,** (마지막 콤마 중요, 값이 하나라서 콤마 있는 채로 튜플에 저장)
        - 두개 이상의 요소가 있을 경우 마지막 요소에는 콤마를 붙이지 않는다 ⇒ newtuple = "a","b","v"
    - 파이썬은 튜플을 출력할 때 괄호() 를 포함, 그러나 튜플을 정의할 때에는 () 필요 없음
    - 뒤에 콤마가 붙는다는 것이 튜플을 정의하는 의미, 그러나 애초에 괄호로 묶어서 정의하면 좀 더 알아보기 쉽다
    - 튜플은 한번에 여러 변수에 할당이 가능 ⇒ "튜플 언패킹"

            >>> numbers = 1, 2, 3, 4, 5  # 패킹
            >>> a, b, c, d, e = numbers  # 언패킹

    - 튜플은 한 문장에서 값을 교환하기 위해 임시 변수를 사용하지 않아도 된다
    - tuple() 은 다른 객체를 튜플로 만들어 줌
        - tuple(리스트)

- 3.3.2 튜플과 리스트
    - 리스트를 대신하여 튜플을 사용할 수 있음, 그러나 튜플은 리스트의 append() , insert() 등과 같은 함수를 사용할 수 없고, 튜플에 사용할 수 있는 함수의 수가 매우 적음
    - 근데 왜 튜플을 사용하는가 ?
        - 튜플은 리스트보다 더 적은 공간을 사용
        - 실수로 튜플의 항목이 손상될 염려가 없다 (튜플은 불변)
        - 튜플을 딕셔너리 키로 사용할 수 있다
        - 네임드 튜플은 객체의 단순한 대안이 될 수 있다 (?)
        - 함수의 인자들은 튜플로 전달된다
    - 사실 근데 딕셔너리랑 리스트를 거의 많이 씀 !

### 3.4 딕셔너리

- 딕셔너리는 리스트와 비슷
    - 리스트와 다른점이라면, 항목의 순서를 따지지 않으며 오프셋으로 값을 선택할 수 없다.
    - 대신 값에 상응하는 고유한 키를 지정함
    - 이 키는 대부분 문자열이지만, 불변하는 파이썬의 어느 타입(상수, 튜플, 문자열 등) 이 될 수도 있다.
- 딕셔너리는 가변, 키-값 요소를 추가, 삭제, 수정할 수 있음
- 딕셔너리를 다른 데에서는 연관 배열, 해시, 해시맵이라고도 부르고 파이썬에서는 '딕트' 라고도 함

- 3.4.1 딕셔너리 생성하기 : {}
    - 딕셔너리를 생성하기 위해서는 **중괄호({}) 안에 콤마로 구분된 키:값** 쌍을 지정
    - emptydict = {}

- 3.4.2 딕셔너리로 변환하기 : dict()
    - dict()함수를 사용해서 두 값으로 이루어진 시퀀스를 딕셔너리로 변환할 수 있음
    - 각 시퀀스의 첫번째 항목은 '키' , 두번째 항목은 '값' 으로 사용
    - 딕셔너리에는 순서가 없으므로, 키 할당 시 순서가 임의대로임
    - 예시

        ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c7f327b8-f84f-4aef-bac8-9df5fdd0aa2e/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c7f327b8-f84f-4aef-bac8-9df5fdd0aa2e/Untitled.png)

- 3.4.3 항목 추가/ 변경하기 : [key]
    - 딕셔너리에 항목을 추가하려면, 키에 의해 참조되는 항목에 값을 할당하면 됨
    - 키가 이미 딕셔너리에 존재하는 경우 기존의 값이 새값으로 대체되며 새로운 키인 경우 새값과 키가 딕셔너리에 추가됨
    - 딕셔너리 할당 시, 리스트와 달리 인덱스의 범위 지정이 벗어났다는 에러 걱정 안해도 됨
    - **딕셔너리명[키값]**
    - 딕셔너리의 키는 반드시 유일해야 함, 만일 같은 키를 두번 이상 사용 시, 마지막 값이 살아남는다. (페이지 91,92 참조)

- 3.4.4 딕셔너리 결합하기 : update()
    - update() 함수는 한 딕셔너리의 키와 값들을 복사해서 다른 딕셔너리에 붙여준다
    - **딕셔너리.update(추가할 딕셔너리**)
    - **만일 추가하려는 딕셔너리에 있는 키가 이미 기존 딕셔너리에 존재한다면, 추가하려는 딕셔너리의 키와 값이 살아남는다.**

- 3.4.5 키와 del 로 항목 삭제하기
    - del 딕셔너리[삭제할 항목] → '키' 로 지정 시 키와 값이 같이 삭제된다

- 3.4.6 모든 항목 삭제하기 : clear()
    - 딕셔너리에 있는 모든 키와 값을 삭제하려면 clear()를 사용하거나 해당 딕셔너리명에 빈 딕셔너리를 할당한다
    - 딕셔너리.clear()

- 3.4.7 in 으로 키 멤버십 테스트 하기
    - 딕셔너리에 키가 존재하는지 확인하고 싶다면 'in' 사용
    - '찾을 키' in 딕셔너리명 → T/F 로 반환

- 3.4.8 항목 얻기 : [key]
    - 딕셔너리에 키를 지정하여 상응하는 값을 얻음
    - 딕셔너리[키값] → 그 키에 상응하는 값 반환
    - 만일 키가 존재하지 않으면 에러남, 에러가 나기 싫으면 in으로 멤버십 테스트 실행하는 방법이 있음
        - 딕셔너리.get(키) → 딕셔너리, 키, 옵션값 사용 → 키 값 존재 시 상응하는 값 호출/ 아니면 옵션값 반환
        - 만약 딕셔너리.get(키, 옵션 지정) 하면 키 값이 없더라도 옵션값이 반환됨
        - 옵션값 지정하지 않을 시, None 을 얻어서, 출력창에 아무것도 나타나지 않음

- 3.4.9 모든 키 얻기 : keys()
    - 딕셔너리의 모든 키를 가져오는 함수
    - 딕셔너리.keys()
    - 파이썬2의 keys() 함수는 단지 리스트를 반환
        - 파이썬 3에서는 순회 가능한 키들을 보여주는 dict_keys() 를 반환함
        - 이러한 방법은 아주 큰 딕셔너리에 유용함 → 사용되지 않을 리스트를 생성,저장하는 메모리와 시간을 소비하지 않기 때문
        - 그러나 불러낸 키값을 리스트로 사용하고 싶다면, → list(딕셔너리.keys()) 하여 리스트로 변환시켜주면 됨

- 3.4.10 모든 값 얻기 : values()
    - 딕셔너리의 모든 값을 가져오는 함수
    - 딕셔너리.values()
    - 결과물을 리스트로 반환하기 위해 list() 와 함께 사용 → list(딕셔너리.values())

- 3.4.11 모든 쌍의 키 - 값 얻기 : items()
    - 딕셔너리의 모든 쌍의 키와 값을 얻기 위해서는 items() 를 사용
    - 딕셔너리.items() → list(딕셔너리.items())
    - 각 키와 값은 '튜플' 로 반환됨 (각 키와 값이 튜플로 이루어진 리스트로 최종 결과 반환)

- 3.4.12 할당 : = / 복사 : copy()
    - 리스트와 마찬가지로 딕셔너리를 할당한 후 변경 시, 딕셔너리를 참조하는 모든 이름에 변경된 딕셔너리를 반영
    - 그러므로 안바뀌게 하려면 copy() 함수를 이용해 또다른 딕셔너리로 복사, 새로운 이름 할당
    - 딕셔너리.copy()

### 3-5. 셋 (set)

- 셋은 값은 버리고 키만 남은 딕셔너리와 같음
- 각 키는 유일해야하며, 어떤 것이 존재하는지의 여부만 확인할 때에는 셋을 이용한다.
- 키에 첨부하여 어떤 상응하는 값을 얻고 싶을 때에는 딕셔너리를 사용한다.

- 3.5.1 셋 생성하기 : set()
    - 셋을 생성할 때에는 set() 혹은 중괄호({}) 안에 콤마로 구분된 하나 이상의 값을 넣는다.
    - emptyset=set()
        - **셋의 공백은 왜 set() 인가? → {} 은 빈 딕셔너리를 생성함, 왜냐면 딕셔너리가 셋보다 파이썬에 먼저 나타나서 {} 를 차지하고 있었기 때문, 따라서 공백의 셋을 생성하고 싶다면 set() 을 사용**
    - evennumbers={1,2,3,4,5}
    - 딕셔너리와 마찬가지로 셋은 순서가 없음

- 3.5.2 데이터 타입 변환하기 : set()
    - 리스트, 문자열, 튜플, 딕셔너리로 부터 중복된 값을 버린 셋을 생성할 수 있음
    - set(바꿀 항목) → set(리스트 or 문자열 or 튜플 or 딕셔너리)

- 3.5.3 in 으로 값 멤버십 테스트 하기
    - 이는 일반적으로 사용되는 셋의 용도
    - 예시

- 3.5.4 콤비네이션과 연산자
    - 교집합 : & or intersection() → a&b or a.intersection(b)
    - 합집합 : | or union() → a|b or a.union(b)
    - 차집합 : - or difference() → a-b or a.difference(b)
    - 대칭차집합 : ^ or symmetric_difference() → a^b or a.symmetric_difference(b)
        - 서로 겹치는 값을 제외하고 양쪽의 나머지 값
    - 부분집합 : ≤ or issubset() → a≤b or a.issubset(b)
        - 첫번째 셋이 두번째 셋의 포함되는가
        - 모든 셋은 자신의 서브셋임 (자기자신은 자기를 포함하니까)
    - 진부분집합( 프로퍼 서브셋) : < → a<b
        - 첫번째 셋이 두번째 셋의 포함되는데, 단 두번째 셋이 첫번째 셋을 포함하고 그 이상의 멤버가 있어야 함
        - 그렇다면 자기 자신이 프로퍼 서브셋인가? → 프로퍼 서브셋의 경우 모두 포함 + 그 이상의 것  이어야 하기 때문에 자기자신이 프로퍼 서브셋이 되지 못함
    - 슈퍼셋 → 서브셋의 반대 ⇒ a≥b or a.issuperset(b)
        - 모든 셋은 자신의 슈퍼셋
    - 프로퍼 슈퍼셋 : a>b
        - 프로퍼 슈퍼셋의 경우 프로퍼 서브셋의 반대방향 개념
        - 프로퍼 서브셋과 마찬가지로, 첫번째 셋이 두번째 셋을 모두 포함하되 그 이상의 항목을 갖고 있어야 함
        - 따라서 자기 자신은 프로퍼 슈퍼셋이 되지 못함

### 3-6. 자료 구조 비교하기

- 간단하게 말하면
    - 리스트는 []
    - 콤마(,) 사용해서 튜플
    - {} 이용해서 딕셔너리를 만들 수 있음
    - 각각의 경우 대괄호를 이용하여 하나의 요소에 접근할 수 있음
- 리스트와 튜플의 경우 대괄호에 들어가는 값이 정수 오프셋, 딕셔너리의 경우 키값임
    - 이 세가지에 대한 결과 값은 각 오프셋, 키에 대응하는 '값' 임

### 3-7. 자료 구조를 더 크게

- 자료구조를 키우는데 제한 사항이 있다면 '데이터 타입' 그 자체임
- 예를 들어 딕셔너리의 키는 불변, 유일하기 때문에 리스트, 딕셔너리, 셋은 다른 딕셔너리의 키가 될 수 없다
- 그러나 튜플은 딕셔너리의 키가 될 수 있다.

### 3-8. 연습문제

    #연습문제1
    
    yearlist=['1994','1995','1996','1997','1998']
    print(yearlist[2])
    print(sorted(yearlist,reverse=True)[0])
    
    #연습문제2
    things=["mozzarella","cinderella","salmonella"]
    things=[things[0].title(),things[1].title(),things[2].title()]
    print(things)
    things=[things[0].upper(),things[1],things[2]]
    print(things)
    del things[2]
    print(things)
    
    #연습문제3
    surprise=["Groucho","Chico","Harpo"]
    surprise2=["Groucho","Chico",''.join(reversed(surprise[-1].lower())).capitalize()]
    #모범답안 
    surprise[-1] = surprise[-1].lower() #마지막값 전부 소문자화 
    surprise[-1] = surprise[-1][::-1] # 소문자화된 마지막값 역순 
    surprise[-1].capitalize() #역순된 마지막값 첫번째 글자 대문자화 
    print(surprise2)
    
    #연습문제4
    e2f={"dog":"Chien","cat":"chat","walrus":"morse"}
    print(e2f)
    print(e2f["walrus"])
    f2e={v:k for k,v in e2f.items()} #구글링해서 찾음 
    #모범답안 
    f2e={} #빈 딕셔너리 만들고 
    for english,french in e2f.items() : #e2f 의 모든 키와 값을 호출 (키 : 영어 / 값 : 불어) 
    	f2e[french]=english #불러낸 키와 값을 바꿈 
    
    print(f2e)
    print(f2e["Chien"])
    print(e2f.keys())
    
    
    life={'animal':
          {'cats':'Henri','octopi':'Grumpy','emus':'Lucy'},
      'plants':'',
      'other':''
      }
    print(life)
    print(life.keys())
    print(life['animal'].keys())
    print(life['animal']['cats'])
