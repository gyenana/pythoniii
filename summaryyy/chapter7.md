# chapter7. 데이터 주무르기 

- 컴퓨터는 0과 1만 사용 가능 → 비트 단위
- 8비트 = 1바이트 → 2^8 / 즉 0~ 255까지 데이터 저장 가능
- 컴퓨터는 숫자만 인식 가능, 그렇다면 문자의 경우 어떤 방식으로 인식하는가? ⇒ 아스키 코드
- 아스키코드는 문자를 숫자로 변환, 전달된 숫자를 대상으로 아스키 코드 테이블에서 문자 찾고, 찾은 문자를 그려줌
- 숫자도 아스키코드에 정의되어 있으나, 자음과 모음으로 이루어진 한글이나 중국어같은 언어들은 아스키코드로 변환이 불가 ⇒ 따라서 만들어진 게 유니코드 !

### 7.1 텍스트 문자열

- 텍스트는 가장 친숙한 데이터 타입
- 문자열 : 텍스트 데이터에 사용되는 유니코드 문자의 시퀀스 (파이썬의 문자열은 모두 유니코드 문자열임)
- 바이트와 바이트배열 : 이진데이터에 사용되는 8비트 정수의 시퀀스

**7.11 유니코드** 

- 컴퓨터의 기본 저장단위는 바이트, 바이트는 8비트에 256개의 고유한 값을 저장할 수 있다.
- 여러가지 이유로 아스키코드는 7비트(128개의 고유한 값) 만 사용하며, 각 26개의 대/소문자, 10개의 숫자, 구두문자, 공백문자, 비인쇄제어코드 로 구성되어있다.
- 그러나 비유럽국가의 언어의 경우 8비트로 모든 문자를 표현할 수 없다. → 유니코드는 전세계 언어의 문자를 정의하기위한 국제 표준 코드, 수학 및 기타 분야의 기호들도 포함하고 있다.

    > 유니코드는 플랫폼, 프로그램, 언어에 상관없이 문자마다 고유한 코드값을 제공한다

- 유니코드 문자들은 유니코드 평면이라고 하는 8비트의 세트로 분할된다. 첫번째 256 평면은 기본 다국어 평면이다.

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b1a7bdf0-dc1a-41d5-9640-5b4714c7ee94/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b1a7bdf0-dc1a-41d5-9640-5b4714c7ee94/Untitled.png)

**파이썬 3 유니코드 문자열** 

- 파이썬3의 문자열은 바이트배열이 아닌 유니코드 문자열
- 파이썬3의 유니코드 문자열은 파이썬2로부터의 가장 큰변화로, 파이썬 3는 일반적인 바이트 문자열과 유니코드 문자를 구별한다.
- 유니코드 식별자 (ID) 혹은 문자에 대한 이름을 안다면, 이 문자를 파이썬 문자열에서 사용할 수 있다.
    - 4자리 (\uxxxx) → 유니코드의 기본 평면 256개 중 하나의 문자를 지정
        - \u : 해당 접두사가 붙어있으면 유니코드라는 뜻
        - 앞에 2자리 : 평면번호 (00~FF)
        - 뒤에 2자리 : 평면에 있는 문자의 인덱스
        - ex. 평면 00 은 아스키코드, 평면 안의 문자위치는 아스키코드의 번호와 같음
    - 높은 평면의 문자일수록 비트수가 더 필요하며, 이 때 유니코드의 이스케이프 시퀀스는 \U (대문자 사용)
        - 또한 8자리의 16진수를 이용하여 나타낸다.
    - 모든 문자는 표준이름 \N{name} 으로 지정할 수 있음
- 파이썬의 unicodedata 모듈은 유니코드 식별자와 이름으로 검색할 수 있는 함수를 제공
    - lookup() : 대/소문자를 구분하지 않는 인자를 취하고, 유니코드 문자를 반환
    - name() : 인자로 유니코드 문자를 취하고, 대문자 이름을 반환

        def unicode_test(value) : 
        		import unicodedata
        		name = unicodedata.name(value)
        		value2 = unicodedata.lookup(name)
        		print({},{},{}.format(value,name,value2))
        
        # 결과 
        
        	unicode_test('A')
        
        value : 'A' #입력한 값 
        name = 'LATIN CAPITAL LETTER A' #입력한 값의 표준 이름 
        value2 = 'A' #표준 이름으로 유니코드에서 대상 찾기 
        

- 유니코드에서 한가지 문제가 있다면, 텍스트를 표시하는데 사용하는 글꼴에 한계가 있다는 것 → 모든 글꼴은 유니코드에 대한 이미지를 가지고있지 않으며, 일부 없는 문자에 대해서는 플레이스홀더 문자로 표기할 것
- 문자열 len 함수는 유니코드의 바이트가 아닌 문자 수를 센다.

**UTF-8 인코딩과 디코딩** 

- 파이썬에서 일반 문자열을 처리할 떄는 각 유니코드 문자를 저장하는 방법에 대해 걱정하지 않아도 되나, 외부 데이터를 교환할 때는 다음과정이 필요
- 인코딩 : 문자열을 바이트로 인코딩
- 디코딩 : 바이트를 문자열로 디코딩
- 유니코드에 64,000 미만의 문자가 있다면 2바이트로 된 각 유니코드 문자의 식별자를 저장할 수있음, 그러나 문자가 64,000개 이상 존재하며, 3,4 바이트의 식별자를 인코딩할 수 있지만, 텍스트 문자열에 대한 메모리 및 디스크 저장공간이 3~4배 증가 → 그래서 두명이 개발한게 **UTF-8 / 동적 인코딩 형식**
- 유니코드는 한 문자당 1~4바이트를 사용 (문자당 맞춰서 바이트 사용 / 이모티콘은 3바이트)
    - 1바이트 : 아스키코드
    - 2바이트 : 키릴 문자를 제외한 대부분의 파생된 라틴어
    - 3바이트 : 기본 다국어 평면의 나머지
    - 4바이트 : 아시아 언어 및 기호를 포함한 나머지
- **UTF-8 은 파이썬, 리눅스, HTML 의 표준 텍스트 인코딩** / 빠르고 완전하게 잘 동작함
    - 파이썬3부터 UTF-8 이 표준이 됨, 파이썬2는 바이트 배열이 기본
    - 파이썬2와 파이썬3의 차이 알아야 함

**인코딩**

- 인코딩하는 함수는 encode() → 첫번째 인자는 인코딩 이름
- 인코딩 이름
    - ascii : 7비트의 아스키코드
    - utf-8 : 8비트 가변 길이 인코딩 형식, 거의 대부분의 문자 지원
    - latin-1 : ISO8859-1 로도 알려짐
    - cp-1252 : 윈도우 인코딩 형식
    - unicode-escape : 파이썬 유니코드 리터럴 형식 , \uxxxx or \Uxxxxxxxx
- 유니코드를 utf-8 이외의 다른 인코딩도 할 수 있지만, 해당 방법에서 유니코드 문자를 표현할 수 있는 문자가 없을 경우 에러 발생
- encode() 함수는 인코딩 예외를 피하기 위해 두번째 인자를 취함 → encode(인코딩이름, 예외처리)
    - strict : 기본값 / 예외 처리 안됨
    - ignore :  인코딩 안되면 공백으로 출력
    - replace : 인코딩 안되면 ?로 출력
    - backslashreplace : 인코딩 안되면 유니코드 문자의 문자열로 출력 (\uxxxx 형태)
    - xmlcharrefreplace : 인코딩 안되면 유니코드 이스케이프 시퀀스를 출력할 수 있는 문자열로 출력 (ex. &#9731;)

**디코딩** 

- 바이트문자열을 유니코드 문자열로 변환 → '디코딩'
- 외부소스에서 텍스트를 얻을 때 마다 그것은 바이트 문자열로 인코딩 되어있음 , 이 소스에서 실제 사용된 인코딩을 알기 위해서는 인코딩 과정을 거꾸로 하여 유니코드 문자열을 얻을 수 있음
- 그러나 바이트문자열이 어떻게 인코딩되어있는지 알 수 없으므로, 엥간하면 UTF-8 을 사용
- UTF-8은 모든 유니코드 문자를 표현할 수 있고 어디에서나 지원함

**7.1.2 포맷** 

**옛스타일의 포맷 : %**

- 문자열 포매팅의 옛 스타일은 string % data 형식
- 문자열 안에 끼워넣을 데이터를 표시하는 형식은 보간 시퀀스

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3d414837-b8a6-4266-8d37-b29f7bf76f72/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3d414837-b8a6-4266-8d37-b29f7bf76f72/Untitled.png)

- 여러 데이터 타입을 끼워 넣는 경우 튜플로 묶어야 함

**새로운 스타일의 포매팅 : {} 와 format** 

- 파이썬3를 사용한다면 새로운 스타일의 포매팅을 사용
- 옛스타일의 인자는 문자열에서 % 가 나타난 순서대로 데이터를 제공, 새로운 스타일의 경우 순서를 지정할 수있음

    {2}{0}{1}.format(f,s,n) 

- 인자는 딕셔너리 혹은 이름을 지정한 인자가 될 수 있으며, 지정자는 그들의 이름을 포함할 수 있다.
- 옛스타일은 문자열 내의 % 다음 타입 지정자를 입력하는 반면, 새로운 스타일에서는 :다음이 타입 지정자 입력

    %d -> {:d} 

**7.1.3 정규 표현식** 

- 정규표현식은 임포트할 수 있는 표준모듈 re 로 제공, 원하는 문자열 패턴을 정의하여 소스 문자열과 일치하는지 비교
- re  내 사용가능한 메서드는 아래와 같음
    - match() : 첫번째 일치하는 객체를 반환 → 시작부터 일치하는 패턴 찾기
        - search() : 첫번째 일치하는 패턴 찾기
    - findall() : 중첩에 상관 없이 모두 일치하는 문자열 리스트를 반환
    - split() : 패턴에 맞게 소스를 쪼갠 후 문자열 조각의 리스트를 반환
    - sub() : 대체인자를 하나 더 받아서 패턴과 일치하는 모든 소스 부분을 대체 인자로 변경(replace() 와 유사한 동작)
    - **findall 과 sub 의 탐색 성능에 차이가 있느냐 → 성능 차이 없다. Big-O(알고리즘의 효율성을 나타내는 지표/시간복잡도/**[https://brenden.tistory.com/2](https://brenden.tistory.com/2)**) 기준으로 차이가 없다.**
    - [**https://ko.wikipedia.org/wiki/아호_코라식_알고리즘](https://ko.wikipedia.org/wiki/%EC%95%84%ED%98%B8_%EC%BD%94%EB%9D%BC%EC%8B%9D_%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98) 참고**

        코드를 짤 때는 시간복잡도와 공간복잡도를 생각하면서 짜야 됨

        ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/55690580-ba34-46f9-81d0-78ee5d2ca4fd/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/55690580-ba34-46f9-81d0-78ee5d2ca4fd/Untitled.png)

 **패턴 : 특수문자** 

[https://cupjoo.tistory.com/84](https://cupjoo.tistory.com/84) →정규표현식 관련 참고 링크 

- 정규 표현식은 아주 많은 문장부호를 사용, 상단 기재한 메서드에서 사용할 수 있는 정규표현식의 세부사항 확인
    - 리터럴은 모든 비특수문자와 일치
    - \n 을 제외한 하나의 문자 : .
    - 0회 이상 : *
    - 0 또는 1회 : ?
    - 그 이외 특수문자에 대해서는 상단 링크 참조
    - 정규표현식은 아스키코드 외에 다른것도 사용할 수 있음 → \d 는 아스키 문자 0 ~ 9 뿐만 아니라 유니코드가 정의하는 숫자도 될 수 있음

**패턴 : 지정자** 

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f8a39dc1-b3a9-466e-9ff1-a07ae954fc70/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f8a39dc1-b3a9-466e-9ff1-a07ae954fc70/Untitled.png)

- expr 은 표현식을, prev 는 이전 토큰을 , next 는 다음 토큰을 의미
- ^과 $ 은 앵커라 부르며 ^는 시작 , $는 문자열의 마지막 위치를 나타냄 , 또한 .$ 는 가장 마지막에 있는 한 문자와 .을 매칭함
- 정규 표현식 패턴이 파이썬 문자열 규칙과 충돌하는 경우가 몇가지 있는데, \b 를 사용하는 경우를 예로 들 수 있음
    - \b 는 파이썬에서 백스페이스를 의미하는 이스케이프 문자이나 정규표현식에서는 단어의 시작 부분을 의미
    - 따라서 정규 표현식의 패턴을 입력하기 전에 항상 문자 r 을 입력하라 → 그러면 충돌을 피할 수 있음

**패턴 : 매칭결과 지정하기** 

- match() 나 search() 를 사용할 때 모든 매칭은 m.group() 과 같이 객체 m으로 부터 결과를 반환
- 만약 패턴을 괄호로 둘러싸는 경우, 매칭은 그 괄호만의 그룹으로 저장됨
- 그리고 m.groups()  사용 시, 해당 그룹은 튜플로 출력됨

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7cf72467-ef7a-4909-b356-4a18b99cfc63/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7cf72467-ef7a-4909-b356-4a18b99cfc63/Untitled.png)

- 만일 (?P<name> expr) 패턴 사용 시, 표현식(expr) 이 매칭되고, 그룹 이름에 매칭 내용이 저장된다.

### 7.2 이진 데이터

- 엔디안 : 컴퓨터 프로세서가 데이터를 바이트로 나누는 방법

**7.2.1 바이트와 바이트배열** 

- 파이썬3는 다음 두가지 타입으로 **0~255 범위에서 사용할 수 있는 8비트 정수의 시퀀스**를 소개
    - 바이트 : 바이트의 튜플처럼 불변  → bytes(blist)
    - 바이트배열 : 바이트의 리스트처럼 변경 가능 → bytearray(blist)
    - 바이트 값은 b 로 시작하고 그 다음엔 인용부호가 따라옴 , 인용 부호 안에는 \x02 또는 아스키문자와 같은 16진수 시퀀스가 옴.
        - 파이썬은 16진수 시퀀스나 아스키문자를 작은 정수로 변환, 또한 아스키문자처럼 유효한 아스키 인코딩의 바이트 배열을 보여줌
- 바이트 혹은 바이트 배열 데이터를 출력할 때, 파이썬은 출력할 수 없는 바이트에 대해서는 \xxx를 사용하고, 출력할 수 있는 바이트에 대해서는 아스키코드값을 사용 (\x0a 대신 \n을 사용하는 것 처럼 일부 아스키코드값은 일반적인 이스케이프 문자를 사용 )

**7.2.2 이진데이터 변환하기 : Struct** 

- 파이썬표준 라이브러리는 c와 c++의 구조체 (struct) 와 유사한, 데이터를 처리하는 struct 모듈이 존재
    - struct 를 사용하면 이진데이터를 파이썬 데이터 구조로 바꾸거나, 파이썬 데이터 구조를 이진데이터로 변경할 수 있음
- unpack() : >LL 은 입력한 바이트 시퀀스를 해석하고, 파이썬의 데이터 형식으로 만들어주는 형식 문자열 (format string)임
    - '>' 는 정수가 빅엔디안 형식으로 저장되었다는 것을 의미
    - 각각의 L 은 4바이트의 부호없는 긴 정수를 지정
- 빅엔디안 정수는 왼쪽에서부터 최상위 바이트가 저장
- pack(): 파이썬 데이터를 바이트로 변환 가능

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bcf69685-1334-4bd5-b0a7-f5e2f7236897/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bcf69685-1334-4bd5-b0a7-f5e2f7236897/Untitled.png)

엔디안 지정자 

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/170b8d4d-700e-42be-8a5c-7b360cc6f04a/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/170b8d4d-700e-42be-8a5c-7b360cc6f04a/Untitled.png)

형식지정자 

**7.2.3 기타 이진데이터 도구** 

- 몇몇 서드파티 오픈소스 패키지는 이진데이터를 정의하고 추출하는 서술적인 방법을 제공
    - bitstring
    - construct
    - hachoir
    - binio

**7.2.4 바이트 / 문자열 변환하기 : binascii()**

- 표준 binascii 모듈은 이진데이터와 다양한 문자열 표현 (16진수, 64진수 등) 을 서로 변환할 수 있는 함수를 제공

**7.2.5 비트 연산자** 

- 파이썬은 c언어와 유사한 비트단위 정수 연산을 제공, 이러한 연산자는 3장의 셋 연산자 처럼 동작

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/996cdc36-372f-4380-9b63-304b94bea0af/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/996cdc36-372f-4380-9b63-304b94bea0af/Untitled.png)

- ~ 연산자의 경우 1은 0으로, 0은 1로 비트를 반전 + 부호 반전 → 모든 현대 컴퓨터에서 사용되는 2의 보수연산에서 최상위 비트는 부호(1=음수) 를 나타내기 때문
