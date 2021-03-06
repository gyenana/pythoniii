# chapter1. 파이 맛보기

- 모든 프로그래밍 언어에는 3가지 존재 : 구문, 루프, 함수
- 파이썬에도 마찬가지로 기타 기호들을 통한 규칙들이 존재한다.

- 파이썬에서는,
    - 오프셋 0 이 가장 첫번째 값
    - 리스트는 [], 딕셔너리형태는 {} 임 (딕셔너리 형태는 리스트의 대안으로도 많이 사용됨)
    - 딕셔너리는 키값과 키값에 대응하는 값으로 이루어져 있음 (철수 : 영희야 놀자 → 철수 = 키 , 영희야 놀자 = 대응하는 값)

### 1-2. 파이썬과 다른 언어

- 쉘 프로그램 : 터미널을 이용, 입력한 문자를 읽고 실행하여 그 결과를 보여줌 (윈도우의 쉘은 cmd)
    - 다양한 쉘 프로그램 존재 (배쉬, sh 등)
    - 쉘은 *와 같은 와일드 카드 문자를 사용할 수 있으며, 파일에 명령어를 저장할 수 있음 (쉘 스트립트)
    - 쉘스크립트는 확장성이 떨어지며, 느림
- 정적언어란 ?
    - 컴퓨터에 대한 저수준의 세부사항을 몇가지 정할 필요가 있음 (**변수 타입 선언**)
    - C, C++, 자바
    - 변수 타입을 선언함으로써, 컴퓨터에게 해당 변수가 사용할 메모리 공간 및 용도를 알려줌
    - 또한, 컴퓨터는 해당 타입 정보를 받아, 매우 낮은 저수준의 기계언어로 컴파일 (컴퓨터가 알아들을 수 있는 언어로 해석한단 말)
    - ex. int language = 0
- 동적언어란 ? (스크립트 언어라고도 함)
    - 변수 타입을 선언하도록 강요하지 않음
    - x=5라고 선언 시, 자동으로 정수로 인식, 따라서 적은 코드로 많은 일 수행 가능
    - 컴파일 대신 인터프리터 라는 프로그램으로 코드를 해석함
    - 대표적으로 파이썬
    - 그외 펄, 루비 , php 등이 있음
    - 그러나 동적언어의 경우 정적언어보다 속도가 느림 → 인터프리터의 발전에 따라 차이는 좁혀지는 중

### 1-3. 왜 파이썬인가?

- 파이썬은 범용의 고수준 언어며 코드를 아주 읽기 쉬우며, 작성하기도 쉬움
- 또한, 같은 동작을 수행하는 프로그램을 정적언어로 작성했을 때보다, 파이썬 이용시 코드가 상대적으로 훨씬 간결해짐

### 1-4. 파이썬을 쓰면 안될 때

- 계산작업을 많이 하는 경우 파이썬을 쓰면 안됨
- 계산작업을 많이 하는 경우, 정적 언어로 작업하는 것이 동적언어보다 빠르다 (항상 그런건 아님)
    - 왜냐면, 정적언어는 이미 변수 타입 선언도 해주기 때문에 컴퓨터가 바로 뭔지 알아먹고 계산하는 반면, 동적언어는 컴퓨터가 스스로 이게 뭔지 알아야하기 때문에, 계산이 많은 경우 느릴 수 있음

### 1-5. 파이썬 2와 파이썬 3

- 파이썬2와 파이썬3는 서로 호환 안됨
- 파이썬2와 파이썬3의 가장 큰 변화는 유니코드 문자 처리와 print문의 호출방법임

### 1-7. 파이썬 실행하기

1. 대화식 인터프리터 사용하기 
    - $는 터미널창에서 python과 같은 명령을 입력할 수 있는 시스템 프롬프트
2. 파이썬 파일 사용하기 
    - 텍스트 편집기를 통해 실행시키고자 하는 코드를 입력하고, ~.py 로 저장
    - 터미널창을 열어 저장한 .py 파일 로드 (ex. $python ~.py)
3. 위 2개를 제외하고 통합 개발 환경 (IDE)가 존재
