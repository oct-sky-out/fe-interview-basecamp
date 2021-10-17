# 실행 컨텍스트 배경

## 결론

- 자바스크립트 실행 컨텍스트란 자바스크립트 코드가 실행되기 위한 환경과 조건이라는 의미를 가지고 있다.

## 설명


자바스크립트의 실행환경 단위. ⇒ es6 이전 함수, es6 이후 블록 스코프라는 것도 생김. 하지만 여전히 기본 실행 단위는 함수임에는 변함이 없다!

함수 단위로 실행환경을 가지고 있으므로 각 함수에는 자신만이 가지고 있는 실행환경을 가지고 있을 것이다.

자바스크립트가 실행되기위한 조건 ⇒ 각 실행컨텍스트에 변수, 함수, this, 스코프의 정보를 참조하고 있는가를 따짐. 그리고 이 정보들을 자바스크립트 엔진이 읽을 수 있게 객체화 시켜놓음.

엔진이 참조할 수 있는 객체(각 컨텍스트의 참조 객체) : VariableEnviorment, LexicalEnviorment, thisValue

VariableEnviorment에는 해당 실행 컨텍스트의 변수와 함수들의 정보를 가지고있다. 그리고 내부의 참조 변수, 함수들의 값을 추적하지 않는다. 즉 최초의 정보만 고정적으로 유지한다.

LexicalEnviorment에는 해당 실행 컨텍스트의 변수, 함수를 참조하고 상위 스코프의 실행 변수와 함수도 참조한다. 또한 VariableEnviorment와는 다르게 변동된 변수의 값을 변경한다.

thisValue는 컨텍스트 내부의 this가 어디인지를 참조하는 객체이다. 이것은 함수의 실행 페턴에 따라서 변동된다.

## 요약

자바스크립트의 각 실행 환경 단위는 기본적으로 함수이고, 함수마다 컨텍스트를 보유하고 있다. 컨텍스트에는 엔진이 참조할 수 있는 객체 3가지가 존재하는데 이 객체의 이름이 'VariableEnviorment', 'LexicalEnviorment', 'thisValue'이다. 이 3가지 객체가 있어야 자바스크립트 코드가 돌아간다.


---


# 컨텍스트와 콜스택

## 설명

위에서 설명한대로 컨텍스트가 생성되고, 이후 각 컨텍스트를 실행시 자바스크립트에는 콜스택이라는 자료구조가 생긴다.

콜스택이라는 것은 전역과 함수가 실행될 때마다 스택에 컨텍스트가 쌓이는 것을 말한다.

스택의 최상위 컨텍스트는 실행 중인 컨텍스트이며, 이 컨텍스트가 종료되면 콜스택에서 빠지게 된다.

전역 컨텍스트는 최초로 쌓이고, 가장 마지막인 프로그램 종료될 때 사라진다.

콜 스택을 통해서 알 수 있는 점은 최상위에 있는 컨텍스트가 현재 실행 중인 컨텍스트라는 것을 알 수 있다.

## 요약

콜스택은 LIFO 구조를 지닌 자료구조이다. 새로운 컨택스트가 실행될 때마다 최상위로 쌓이고, 실행이 종료되면 최상위 컨텍스트가 없어진다. 콜스택은 현재 실행 중인 컨텍스트를 자료구조로 나타낸 것이다.

---
### 참고자료
- 정재남 개발자님의 코어 자바스크립트 참고
- https://poiemaweb.com/js-execution-context | 실행 컨텍스트와 자바스크립트의 동작 원리
- https://blog.bitsrc.io/understanding-execution-context-and-execution-stack-in-javascript-1c9ea8642dd0 | Understanding Execution Context and Execution Stack in Javascript (Sukhjinder Arora)