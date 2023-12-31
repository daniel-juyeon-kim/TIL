# let, const <!-- omit in toc -->

let, const는 ES6부터 추가된 변수 선언 키워드입니다.

기존 var 선언문의 문제점을 해결하기 위해 나왔습니다.

## var의 문제점

var 변수 선언의 문제점

- 중복 선언 가능
- 함수 레벨 스코프
- 변수 호이스팅

### 변수 중복 선언 가능

var 변수는 중복 선언이 가능합니다.

의도치 않게 변수의 값이 변하는 부작용이 있습니다.

```js
var page = 1
console.log(page)   // 1

{
    var page = 300  // 변수 중복 선언, 예외가 발생하지 않는다.
    console.log(page)   // 300
}

// var 선언문 + 함수 코드 블록이 아니라서 변수 page에 재할당이 일어난다.
console.log(page)   // 300
```

**초기화문이 있는 변수 선언문**은 자바스크립트 엔진에 의해 **var 키워드가 없는 것처럼 동작**합니다. 초기화문이 없는 변수 선언문은 무시합니다.

```js
var a = 1;      // a = 1
var a = 3;      // 같은 변수 이름으로 선언, 에러는 생기지 않는다.

console.log(a)  // 3

var b = 4;      // b = 4
var b;          // 초기화 문이 없는 변수 선언문은 무시된다.

console.log(b)  // 4
```

### 함수 레벨 스코프

var는 함수 레벨 스코프를 가집니다.

**함수 외부**에서 선언된 var 선언문은 **전역 변수** 또는 **전역 변수 중복 선언** 처리됩니다.

### 변수 호이스팅

[변수 호이스팅](./변수.md#변수-호이스팅)

## let과 const의 특성

- 같은 스코프에 변수 중복 선언 불가능
- 블록 레벨 스코프
- TDZ

### TDZ (일시적 사각지대, Temporal Dead Zone)

TDZ(Temporal Dead Zone)는 스코프의 시작 지점부터 let, const 변수의 초기화 지점까지를 말합니다.

let, const 키워드로 선언한 변수는 호이스팅이 발생하지 않는 것처럼 동작합니다. 이는 변수 선언에서 선언 단계와 초기화 단계가 분리되어 진행되기 때문입니다.
**변수 선언**에서 자바스크립트 엔진에 의해 **선언 단계만 진행**되고 이후 **런타임에서 초기화 단계와 할당 단계가 동시에 실행**됩니다.
그 사이 변수에 접근하면 참조 에러(Reference Error)가 발생합니다.

#### var, let, const의 선언에 대한 차이점 요약 <!-- omit in toc -->

| 흐름\변수 키워드 |                    var                     |                 let, const                 |
| :--------------: | :----------------------------------------: | :----------------------------------------: |
|    변수 선언     | 선언 단계, 초기화 단계 (`undefined`초기화) |                 선언 단계, TDZ 영역                  |
|  변수에 값 할당  |                 할당 단계                  | 초기화 단계 (`undefined`초기화), 할당 단계 |

## 모든 선언문의 호이스팅

모든 선언문은 호이스팅이 발생합니다. 다만 `let`, `cosnt`, `class` 선언문은 호이스팅이 발생하지 하지 않은 것처럼 동작할 뿐입니다.

## let, const의 저장

`let`, `const` 전역변수는 전역 객체에 프로퍼티가 되는 것이 아닌 전역 렉시컬 환경의 `Declare Enviroment Record`에 별도로 관리됩니다.

## const

`const` 선언 키워드는 상수를 의미합니다.

### 상수(재할당 금지, 변경 가능)

상수는 재할당이 금지된 변수를 말합니다.

재할당이 금지된 것일 뿐 변경은 가능합니다. 변경이 가능한 값인 객체는 재할당 없이 직접 변경이 가능합니다. 또한 `const`는 불변을 의미하지 않습니다.
