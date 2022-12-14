# 자료형
자바스크립트에서 값은 항상 문자열이거나 숫자형 같은 특정한 자료형에 속합니다.

자바스크립트에는 여덟가지 기본 자료형이 있습니다.
자바스크립트의 변수는 자료형에 관계없이 모든 데이터일 수 있습니다.
따라서 변수는 어떤 순간에 문자열일 수 있고 다른 순간엔 숫자가 될 수도 있습니다.
```js
// no error
let message = 'hello';
message = 123456;
```
이처럼 자료의 타입은 있지만 변수에 저장되는 값의 타입은 언제든지 바꿀 수 있는
언어를 동적 타입 언어라고 부릅니다.
### 숫자형
```js
let n = 123;
n = 12.345
```
숫자형은 정수 및 부동소수점 숫자를 나타냅니다.
숫자형과 관련된 연산은 다양한데, 곱셈, 나눗셈, 덧셈, 뺄셈 등이 대표적입니다.
숫자형엔 일반적인 숫자 외에 `Infinity`, `-Infinity`, `NaN` 같은 특수 숫자값이 포함됩니다.
```js
alert(1 / 0); // 무한대

alert('숫자 아님' / 2); // NaN, 문자열을 숫자로 나누면 오류가 발생합니다.
```
### BigInt
암호 관련 작업같이 아주 큰 숫자가 필요한 상황이거나
아주 높은 정밀도로 작업을 해야할 때는 큰 숫자가 필요합니다.
`BigInt`형 값은 정수 리터럴 끝에 `n`을 붙이면 만들 수 있습니다.
```js
const bigInt = 1234567890123456789012345678901234567890n;
```
### 문자형
자바스크립트에선 문자열을 따옴표로 묶습니다.
```js
const str = 'Hello';
const str2 = '문자열';
const phrase = `can embed anoter ${str}`;
```
따옴표는 크게 세 종류가 있습니다.
1. 큰따옴표: `"Hello"`
2. 작은따옴표: `'Hello'`
3. 역 따옴표(백틱) : `Hello`

큰따옴표와 작은따옴표는 기본적인 따옴표로, 자바스크립트에서는 이 둘에 차이를 두지 않습니다.

백틱으로 변수나 표현식을 감싼후 `${...}`안에 넣어주면, 아래와 같이 원하는 변수나 표현식을
문자열 중간에 손쉽게 넣을 수 있습니다.
```js
const name = "John";

// 변수를 문자열 중간에 삽입
alert(`Hello, ${name}!`); // Hello, John!

// 표현식을 문자열 중간에 삽입
alert(`the result is ${1 + 2}`); // the result is 3
```

### 불린형
불린형은 `true` 와 `false` 두 가지 값밖에 없는 자료형입니다.

### null 값
`null` 값은 지금까지 소개한 자료형 중 어느 자료형에도 속하지 않는 값입니다.
`null` 값은 오로지 `null` 값만 포함하는 별도의 자료형을 만듭니다.
```js
let age = null;
```
자바스크립트에서 `null` 은 존재하지 않는 값, 비어있는 값, 알 수 없는 값을 나타내는데 사용합니다.

### undefined 값
`undefined` 값도 `null`값처럼 자신만의 자료형을 형성합니다.
`undefined`는 값이 할당되지 않은 상태를 나타낼 때 사용합니다.
변수는 선언했지만, 값을 할당하지 않았다면 해당 변수에 `undefined`가 자동으로 할당됩니다.
```js
let age;

alert(age); // undefined가 출력됩니다.
``` 
### 객체와 심볼
`object`는 특수한 자료형입니다.
객체형을 제외한 다른 자료형은 문자열이든 숫자든 한 가지만 표현할 수 있기 때문에
원시 자료형이라 부르지만 객체는 데이터 컬렉션이나 복잡한 개체를 표현할 수 있습니다.
심볼은 객체의 고유한 식별자를 만들 때 사용됩니다.

### typeof 연산자
`typeof` 연산자는 인수의 자료형을 반환합니다.
자료형에 따라 처리 방식을 다르게 하고 싶거나 변수의 자료형을 빠르게 알아내고자 할 때 유용합니다.
`typeof`연산자는 두 가지 형태의 문법을 지원합니다.
1. 연산자 : `typeof x`
2. 함수 : `typeof(x)`
괄호가 있든 없든 결과가 동일합니다.
