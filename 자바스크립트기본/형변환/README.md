### 형 변환
함수 연산자에 전달되는 값은 대부분 자료형으로 자동 변환됩니다.
이런 과정을 형 변환이라고 합니다.
`alert`가 전달받은 값의 자료형과 관계없이 이를 문자열로 자동 변환하여 보여주는 것이나,
수학 관련 연산자가 전달받은 값은 숫자로 변환하는 경우가 형 변환의 대표적인 예시입니다.
이 외에, 전달받은 값을 의도를 갖고 원하는 타입으로 변환해 주는 경우도 형 변환이라고 할 수 있습니다.

### 문자형으로 변환
문자형으로의 형 변환은 문자형의 값이 필요할 때 일어납니다.
`alert`메서드는 매개변수로 문자형을 받기 때문에,
`alert(value)`에서 value는 문자형이어야 합니다.
만약, 다른 형의 값을 전달받으면 이 값은 문자형으로 자동 변환됩니다.
`String(value)` 함수를 호출해 전달받은 값을 문자열로 변환할 수 있습니다.
```js
let value = true;
alert(typeof value); // boolean

value = String(value); // 변수 value 엔 문자열 "true"가 저장됨
alert(typeof value); // string
```
### 숫자형으로 변환
숫자형으로의 변환은 수학과 관련된 함수와 표현식에서 자동으로 일어납니다.

```js
alert('6'/'2'); // 3, 문자열이 숫자형으로 자동변환된 후 연산이 수행됩니다.
```
`Number(value)` 함수를 사용하면 주어진 값(`value`)을 숫하졍으로 명시해서 변환할 수 있습니다.
```js
let str = '123';
alert(typeof str); // string

let num = Number(str); // 문자열 '123'이 숫자 123으로 변환됩니다.

alert(typeof num); // number
```

숫자형 값을 사용해 무언가를 하려할 때, 그 값을 문자 기본 폼을 통해 입력받는 경우엔,
명시적 형 변환이 필수입니다.
```js
alert(Number('     123     ')); // 123
alert(Number('123z')); // NaN
alert(Number(true)); //1
alert(Number(false)); // 0
```
### 불린형으로 변환
```js
alert(Boolean(1)); // 숫자 1(true)  
alert(Boolean(0)); // 숫자 1(false)

alert(Boolean('1')); // 문자열(true)
alert(Boolean('')); // 빈 문자열(false)
```

