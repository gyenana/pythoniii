# chapter 6. 객체와 클래스

### 6.1 객체란 무엇인가? 

- 숫자에서 모듈까지 파이썬의 모든 것은 객체
- 그러나 파이썬은 특수 구문을 이용해 대부분의 객체를 숨김
- 객체는 데이터(변수, 속성이라고 부름) 와 코드 (함수, 메서드라고 부름)를 모두 포함
- 객체는 어떤 구체적인 것의 유일한 인스턴스를 나타낸다.
- 아무도 생성하지 않은 새로운 객체를 생성할 때에는 무엇을 포함하고 있는지 가리키는 클래스를 생성해야 한다.
- 객체를 명사, 메서드를 동사라고 했을 때, 객체는 각각의 사물을 나타내고 메서드는 다른 사물과 어떻게 상호작용하는지 정의한다.
- 객체는 각자 다른 값을 가진 속성의 객체를 동시에 여러개 생성할 수 있다.

### 6.2 클래스 선언하기 : class

[https://www.youtube.com/watch?v=vrhIxBWSJ04](https://www.youtube.com/watch?v=vrhIxBWSJ04)

- 클래스는 박스를 만드는 틀에 비유할 수 있다.
    - 파이썬은 리스트, 딕셔너리를 포함한 다른 표준 데이터 타입을 생성하는 많은 내장 클래스가 있다.
- 클래스 선언하는 부분 예시 :

    [클래스와 객체 이해 예제 ](https://www.notion.so/2b52e1ba55524a95898958d2c113b35c)

    - 빈 클래스를 나타내고 싶을 때에는 클래스 선언 후 내부에 pass 를 사용한다. (이것은 객체를 생성하기 위한 최소한의 정의 이다)
- '__init__' 메서드는 특별한 파이썬 객체 초기화 메서드로써, '생성자' 이며, 첫번째 매개변수는 self , 즉 자기 자신이다.
    - 클래스 내에서 '__init__' 메서드 정의 시, 메서드 내 할당된 인스턴스 변수에 값이 저장된다
- 모든 클래스 정의에서 '__init__' 메서드를 가질 필요는 없다.

### 6.3 상속

- '상속' 을 이용하면 기존 클래스를 수정하거나 변경해야하는 일이 있을 때, 불필요한 복제 없이 기존 클래스의 모든 코드를 새로운 클래스에서 사용할 수 있다.
- 필요한 것만 추가/변경하여 새 클라스를 정의 → 기존 클래스의 행동을 '오버라이드' 하는 것
- 기존 클래스는 → 부모클래스, 슈퍼클래스, 베이스클래스 라고 불리며
- 새 클래스는 → 자식클래스. 서브클래스, 파생된 클래스라고 불린다.
    - 이 용어들은 객체지향 프로그래밍에서 다르게 사용될 수 있다.
- 자식클래스는 부모 클래스를 '구체화' 한 것이다. 자식클래스는 자식 클래스만의 기능이 별도로 생길 수 있으며 부모 클래스의 모든 기능을 상속받는다.

### 6.4 메서드 오버라이드

- 자식 클래스는 부모클래스로부터 모든 것을 상속받는다. 좀 더 나아가 부모 클래스에서 정의된 메서드를 상속받아 자식 클래스에서 수정 즉, 오버라이드 할 수 있다.

### 6.5 메서드 추가하기

- 자식클래스는 부모클래스에 없는 메서드를 추가할 수 있다.
- 이러한 기능을 통해 부모클래스와의 차이를 생성할 수 있다.

### 6.6 부모에게 도움받기 : super

- 만일 자식클래스에서 부모 클래스의 메서드를 호출하고 싶다면 , super() 메서드를 사용하면 된다.
- 슈퍼 메서드 사용 시, 부모 클래스의 메서드 정의가 바뀌면 자식 클래스에서 호출한 부모 클래스의 메서드에도 변경사항이 반영된다.

### 6.7 자신 : self

- 앞서 말한 것 처럼 인스턴스메서드의 첫번째 인자는 self 이다.
- 파이썬은 적절한 객체의 속성과 메서드를 찾기위해 self 인자를 사용한다.

### 6.8 get/set 속성값과 프로퍼티

- 어떤 객체지향 언어에서는 외부로부터 바로 접근할 수 없는 private 객체 속성을 지원
- 프로그래머는 private 속성의 값을 읽고 쓰기위해 getter 메서드와 setter 메서드를 사용한다.
- 파이썬에서는 getter 와 setter 메서드가 필요없다. → 왜냐면 모든 속성과 메서드가 퍼블릭이고, 우리가 예상한대로 쉽게 동작하기 때문이다.
    - 변수에는 3가지가 있는데 아래와 같이 접근 가능함
        - private : 나만 접근 가능
        - protected: 혼자 + 상속받은 클래스
        - public : 다같이
- 그러나 만일 변수에 직접 접근하기 부담스럽다면 getter와 setter 메서드를 굳이 작성할 수 있으며, 사용하고 싶다면 프로퍼티를 이용하라
    - 참고
        - 변수명 앞 _ 언더스코어 하나 : 내부적으로 사용하는 변수일 떄
        - 변수명 앞 __ 언더스코어 두개 : 클래스 외부에서 접근할 수 없음
- 프로퍼티 property() 의 첫번째 인자는 getter 메서드, 두번째 인자는 setter 메서드다.
    - 쉽게 말하면, getter() 는 호출 , setter() 는 오버라이드
- 프로퍼티를 정의하는 방법 중 하나는 데커레이터를 사용하는 것
    - getter메서드 앞에선 @property 를, setter 메서드 앞에서는 @name.setter 데커레이터를 쓴다.
- 프로퍼티는 계산된 값을 참조할 수 있음
    - 변수에 대한 setter 프로퍼티를 명시하지 않는다면 외부로부터 이 변수를 설정할 수 없고, '읽기 전용' 만 가능하다
- 직접 속성 (변수) 에 접근하는 것 보다 프로퍼티를 통햇서 접근하면 큰 이점이 있는데,
    - 만일 속성(변수) 의 정의를 바꾸려면 모든 호출자를 수정할 필요 없이 클래스 정의에 있는 코드만 수정하면 된다.

### 6.9 private 네임 맹글링

- 파이썬은 클래스 정의 외부에서 볼수 없도록 하는 속성(변수)에 대해 네이밍 컨벤션이 있다.
- 변수명 앞에 언더스코어(__) 두개를 붙이면 된다.
- 변수명앞에 언더스코어 두개를 붙인다고해서 속성이 private 로 변하는 것은 아니지만, 우연히 외부 코드에서 발견할 수 없도록 '맹글링' 해준 것
- 해당 처리가 변수를 완벽하게 보호할 수 는 없지만, 속성의 의도적인 직접 접근을 어렵게 만든다.

### 6.10 메서드 타입

- 어떤 데이터(속성,변수) 와 함수(메서드) 는 클래스 자신의 일부이고, 어떤 것은 클래스로부터 생성된 객체의 일부다.
- 인스턴스 메서드 : 클래스 정의에서 메서드의 첫번째 인자가 self, 일반적인 클래스를 생성할 때의 메서드 타입
    - 인스턴스 메서드의 첫번째 매개변수는 self 고, 파이썬은 이 메서드를 호출할 때 객체를 전달한다.

- 클래스 메서드 : 클래스 전체에 영향을 미치며, 클래스에 대한 어떤 변화는 모든 객체에 영향을 미친다.
    - 클래스 정의에서 함수에 @classmethod 데커레이터가 있다면 이것은 클래스 메서드
    - 이 메서드의 첫번째 매개변수는 클래스 자신이며, cls 로 쓴다.
- 정적 메서드 : @staticmethod 데커레이터가 붙어있고, 첫번째 매개변수로 self나 cls 가 없다.
    - 정적 메서드는 클래스가 메모리에 올라갈 때, 정적 메서드가 자동으로 생성되며, 그렇기에 별도 인스턴스(객체) 생성 없이 클래스만으로 메서드에 접근할 수 있다.
    - 원래는 객체 생성 후, 객체.메서드() 로 클래스 내 메서드를 호출하는데, 정적 메서드는 별도의 객체 생성이 필요없기 때문에 그냥 클래스.메서드() 로 호출하면 됨

### 6.11 덕 타이핑

- 파이썬은 다형성을 느슨하게 구현했다. → 이는 클래스에 상관 없이 같은 동작을 다른 객체에 적용할 수 있다는 것을 의미한다. → 오버라이드가 가능하다.
- 컴퓨터 프로그래밍 분야에서 덕 타이핑(duck typing)은 동적 타이핑의 한 종류로, **객체의 변수 및 메소드의 집합이 객체의 타입을 결정하는 것**을 말한다. 클래스 상속이나 인터페이스 구현으로 타입을 구분하는 대신, 덕 타이핑은 객체가 어떤 타입에 걸맞은 변수와 메소드를 지니면 객체를 해당 타입에 속하는 것으로 간주한다
- 덕 타이핑에서는, 객체의 타입보다 객체가 사용되는 양상이 더 중요하다. 예를 들면, 덕 타이핑이 없는 프로그래밍 언어로는 오리 타입의 객체를 인자로 받아 객체의 걷기 메소드와 꽥꽥거리기 메소드를 차례로 호출하는 함수를 만들 수 있다. 반면에**, 같은 함수를 덕 타이핑이 지원되는 언어에서는 인자로 받는 객체의 타입을 검사하지 않도록 만들 수 있다. 걷기 메소드나 꽥꽥거리기 메소드를 호출 할 시점에서 객체에 두 메소드가 없다면 런타임 에러가 발생하고, 두 메소드가 제대로 구현되어 있다면 함수는 정상적으로 작동한다**. 여기에는 인자로 받은 객체가 걷기 메소드와 꽥꽥거리기 메소드를 갖고 있다면 객체를 오리 타입으로 간주하겠다는 암시가 깔려있다. 바로 이 점이 앞에서 인용한 덕 테스트의 사상과 일치하기 때문에 덕 타이핑이라는 이름이 붙었다.

## Q & A

**덕 타이핑이란 무엇인가요?**

덕 타이핑은 실제 타입(클래스)은 상관하지 않고, 구현된 메서드로만 판단하는 방식입니다. 덕 타이핑은 "만약 어떤 새가 오리처럼 걷고, 헤엄치고, 꽥꽥거리는 소리를 낸다면 나는 그 새를 오리라 부르겠다."라는 덕 테스트(오리 테스트)에서 유래한 말입니다.

### 6.12 특수 메서드

- 특수 메서드 = 매직 메서드
- 클래스안에 정의할 수 있는 스페셜 메소드이며 클래스를 int, str, list등의 **파이썬의 빌트인 타입**(built-in type)과 같은 작동을 하게 해준다.
- +, -, >, < 등의 오퍼레이터에 대해서 각각의 데이터 타입에 맞는 메소드로 오버로딩하여 백그라운드에서 연산을 한다.
- __init__이나 __str__과 같이 메소드 이름 앞뒤에 더블 언더스코어("__")를 붙인다.
- 종류

        * 비교 연산을 위한 마법 메서드 
        __eq__(self,other) : self == other 
        __ne__(self,other) : self != other
        __lt__(self,other) : self < other 
        __gt__(self,other) : self > other
        __le__(self,other) : self <= other
        __ge__(self,other) : self >= other
        
        * 산술 연산을 위한 마법 메서드 
        __add__(self,other) : self + other
        __sub__(self,other) : self - other
        __mul__(self,other) : self * other
        __floordiv__(self,other) : self // other
        __truediv__(self,other) : self / other
        __mod__(self,other) : self % other
        __pow__(self,other) : self ** other
        
        *기타 마법 메서드 
        __str__(self) : str(self) -> 사람이 읽을 수 있는 출력 ha 
        __repr__(self) : repr(self) -> 기계가 읽을 수 있는 출력 "ha" (공식적인 형태) https://sshkim.tistory.com/189
        __len__(self) : len(self)

### 6.13 컴포지션

- 상속은 좋은 기능이지만, 때때로 컴포지션의 사용이 더 적절한 경우가 있음
- 상속 사용 시, 부모 클래스의 기능에 맞춰 확장할 수밖에 없기 때문에, 상위 클래스 구현에 의존적일 수 밖에 없음
- 그러나 컴포지션 이용 시, 클래스를 확장(상속)하는 대신 기존 클래스의 인스턴스를 참조하는 private 필드를 새로운 클래스에 두는 컴포지션(composition) 으로 상속의 문제점들을 해결할 수 있다.

### 6.14 클래스와 객체, 그리고 모듈은 언제 사용할까 ?

- 코드에서 클래스와 모듈의 사용기준은 다음과 같음
    - 유사한 메서드를 실행하지만, 속성(변수)이 다른 개별 인스턴스가 필요할 때, 객체는 매우 유용
    - 클래스는 상속을 지원, 모듈은 상속을 지원하지 않음
    - 한가지 일만 수행한다면 모듈이 가장 좋은 선택임
    - 여러 함수에 인자로 전달될 수 있는 여러 값을 포함한 여러 변수가 있다면 클래스를 정의하느 것이 더 좋음
    - 가장 간단한 문제 해결 방법을 사용, 딕셔너리, 리스트, 튜플은 모듈보다 더 작고, 간단하며, 빠름 그리고 일반적으로 모듈은 클래스보다 더 간단함

### 6.15 네임드 튜플

- 네임드 튜플은 튜플의 서브클래스 → 이름 (.name) 과 위치([offset]) 로 값에 접근할 수 있음
- 네임드 튜플을 사용하기 전에는 모듈을 불러와야 함 (import namedtuple)
- 네임드 튜플은 불변
- 특징은 아래와 같음
    - 불변하는 객체처럼 행동
    - 객체보다 공간 효율성과 시간 효율성이 더 좋음
    - 딕셔너리 형식의 괄호([]) 대신 점(.) 표기법으로 속성 접근 가능
    - 네임드 튜플을 딕셔너리의 키처럼 쓸 수 있음
