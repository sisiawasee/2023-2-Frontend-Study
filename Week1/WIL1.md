1장 자바스크립트의 개요
---
- 프로그래밍 언어로서의 자바스크립트
  - 특징: 인터프리터, 동적 타입 언어/동적 프로토타입 기반(클래스 X) 객체 지향/함수가 일급 객체이자, 클로저를 정의함
  - 기술적 요소: ECMAScript(코어 언어), 클라이언트 측의 고유 기술 요소+서버 측 고유 기술 요소
 
- 자바스크립트의 역사
  - 구글 지도 등 대중적인 언어로 자리잡음 -> 모던 웹 어플리케이션 탄생 기대 가능

2장 프로그램의 작성법과 실행법
---
- 웹브라우저, Node.js 설치 & 텍스트 편집기 필요(이 경우 확장자 표시)
  - 실행: 웹 브라우저의 콘솔 실행/자바스크립트 코드를 HTML 문서에 삽입해 웹 브라우저로 실행/Node.js 대화형 모드 or 파일 로드로 실행
  - 기본 문법(예제 2-1 참조): def 대신 function을 입력하여 함수를 작성하고, 이를 객체로 활용함. 대부분의 경우 C++와 비슷한 문법을 갖고 있는 듯함. 입출력은 다름.
    - 입출력의 경우 console.log로 보여줄 수 있는데, 파어어폭스/크롬/HTML 문서 삽입 등 콘솔마다 출력 양식이 모두 다름.

- 프로그램 작성법(기본적으로 유니코드 사용)
  - 기본 어휘
    - 토큰(어휘): 프로그램을 구성하는 최소 단위 -> 인터프리터를 통해 프로그램을 토큰으로 분해(=어휘 분석)
    - 구문 분석(파싱): 나열 토큰이 올바른 프로그램인지 판정 및 실행
    - 복합문: 문장 여러 개를 중괄호({})로 감싼 코드 (블록문이라고도 함) -> EX) if, while
  - 함수, 세미콜론, 주석문 사용법은 C++과 동일함. 엔터를 칠 경우 세미콜론이 있는 것으로 JS 엔진이 자동으로 처리함.

3장 변수와 값
---
- 변수 선언: 선언자, 변수 이름으로 이루어짐, 값 대입 등 동일
  - var라는 동적 자바스크립트 선언자가 있음
  - 변수를 선언하지 않고 값을 대입할 경우 JS 엔진이 자동으로 전역 변수로 선언함. (->4장, 11장 확인)
  - 변수 선언의 끌어올림(호이스팅, hoisting): 변수 선언이 나중에 되더라도 가장 윗줄에 변수 선언을 한 것처럼 작용. (그림 3-3 참조)
 
- 데이터 타입
  - 정적 타입 언어: 변수에 타입이 있는 언어
  - 원시 타입과 객체 타입: 원시 타입이 일반적인 타입(특수 값, 심벌 포함-심벌은 toString() method(9장) 확인), 객체 타입은 복합 데이터 타입
  - 문자열 리터럴 -> '`', '\' 등 사용/플레이스 홀더도 마찬가지로 ${}를 통해 사용 가능
 
4장 객체와 배열, 함수의 기초
---
- 객체: 복합 데이터, 연관 배열이나 사전이라고도 부름(dictionary를 언급하는 듯함)
  - 객체 리터럴
    - 객체의 프로퍼티 이름 = dictionary key
    - 값을 쓸 때 마침표 연산자(ex: card.suit) 외에도 대괄호 연산자(ex: card["suit"]) 가능
    - 프로퍼티 추가 삭제 존재여부 등 모두 C++과 동일 메소드 사용
    - 객체 타입: 참조 타입 (포인터)
  - 생성자
    - 클래스 제공: new 등으로 생서으 C++과 동일! (this 사용 등)
  - 내장 객체(빌트인 오브젝트): 처음부터 포함된 내장 생성자
    - ex: String, Number, Array, Boolean, Error, Function, Date... 등
 
- 함수 기초: 인수와 반환값으로 이루어짐, function 키워드를 통해 정의
  - return문이 없는 경우 undefined 값이 반환됨
  - 변수 선언문과 마찬가지로 함수 선언문도 호이스팅 됨
  - call by value, call by reference 동작
  - 인수 전달 시 객체 프로퍼티에 담아 전달 가능
  - 지역/전역 변수에 따라 호이스팅, 적용 범위가 달라짐
    - let 선언자(블록 유효범위 지역 번수 선언), const 선언자(상수) 가능
  - 함수 리터럴(=무명 함수, 파이썬의 람다 함수와 유사한 것 같음)
    - ex: var square=function(x){return x*x};
    - 변수에 할당하여 사용
  - 객체 메소드: C++의 클래스와 유사하게 구현할 수 있음.
    - ex: var circle={ center:{x:1,y:2}, radius:2.5, area: function(){return 3.14*this.radius*this.radius;}}
   
- 배열 기초: 인덱스, length, Array 생성자 등 사용 가능, 참조/추가/삭제 동일
  - 희소 배열: 배열에 요소를 추가/제거하여 인덱스가 0이 아닌 배열

5장 표현식과 연산자
---
- 논리/산술(단항, 다항)/비트 연산자 존재 -> 연산자 우선순위를 따름
  - 증가/감소 연산자 또한 가능하지만 연속 사용 시 참조 오류 발생
  - 비트 연산자는 비트끼리 연산함
    - ex: XOR 연산-> 105^(-91)=-52가 됨
 
- 문자열 제어
  - 산술 연산자를 통한 문자열 제어 가능
  - 문자열 조작 메소드(래핑): 원시 값을 객체로 변환하는 행위
    - ex: var msgObj = new String("Everything is practice.")
    - 원시값을 처리할 때는 원시값의 메서드를 바로 호출하고, 객체 등으로 변환해 처리하지 않음. (문자열은 배열으로 사용됨)
   
- 명시적 타입 변환 가능 (ex: 숫자->문자열 변환(toString 사용))
  - 묵시적으로 문자열->숫자 변환도 가능
  - 논리값 변환: !!를 통해 값의 타입을 바꿈+참과 거짓을 바꿀 수 있음을 활용

6장 웹 브라우저에서의 입출력
---
(C++에서 확인할 수 있는 것과 매우 다른 부분)
- 대화상자
  - alert: 경고 대화상자
  - prompt: 입력 대화상자
  - confirm:확인 대화상자

- console
  - 콘솔에 텍스트 출력시: console.log(내용);
  - 타임 측정: time과 timeEnd 사용

- 이벤트 처리기 등록과 타이머
  - 이벤트 처리기: 이벤트가 발생했을 때 실행되는 함수
    - HTML 요소의 속성으로 등록/DOM 요소의 프로퍼티 등록/addEventListener 메소드 사용
    - HTML: 주요 이벤트에 대한 이벤트 처리기 이름이 이미 있음 (표 6-4 참조, 플러터랑 비슷한 뉘앙스)
    - DOM: 특정 id 속성 값을 가진 HTML 요소 객체를 가져와 함수 등록 (HTML보다 어려움, 초기 설정 함수 필요)
  - 타이머: 지정된 시간이 흐른 후 함수 실행(setTimeout), 반복실행(setInterval) 등 가능
 
- HTML 요소를 동적으로 읽고 쓰기
  - 이벤트 처리기, 타이머 사용 (getElementByID+메소드를 주로 사용)
  - innerHTML 프로퍼티로 읽고 쓰기 가능 -> 예제 6.3의 스톱워치 해석(stop, start 타임 등 함수 개별 설정)
  - 폼 컨트롤의 입력값-> input 요소 등 사용자의 입력값을 JS에서 사용 가능

- Canvas를 활용한 컴퓨터그래픽스
  - window.onloadfmf 통해 캔버스 요소 가져오기 -> canvas 객체가 따로 있음.
  - getContext를 통해 캔버스로 그림을 그릴 수 있음
  - python의 turtle이랑 비슷한 듯 -> 다양한 메소드가 내장
    - 둥근모서리 arcTo(x1, y1, x2, y2, radius) 등
  - 이미지 객체 읽어오기도 가능
    - var img = new Image() -> drawImage 메소드 사용

7장 제어 구문
---
- 조건문
  - if/else 문 (다른 언어와 마찬가지로 nested 사용 가능)
  - switch-case-default 문
  - break/return 문으로 분기 처리의 끝을 사용
 
- 반복문
  - while 문 (continue 사용 가능)
  - for문 (C++과 동일)
  - for/in 문 (파이썬과 동일)

- 점프문
  - 라벨문: 라벨이름 : 문장 -> 모든 식별자 사용 가능, break, continue문에서만 사용 가능
    - ex: break loop; //loop라는 라벨로 점프
