# 객체

객체형은 원시형과 달리 다양한 데이터를 담을 수 있습니다.
키로 구분된 데이터 집합이나 복잡한 객체를 저장할 수 있습니다.
객체는 자바스크립트 거의 모든 면에 녹아있는 개념입니다.
객체는 중괄호를 이용해 만들 수 있고 중괄호 안에는
키 : 값 쌍으로 구성된 프로퍼티를 여러 개 넣을 수 있는데
키엔 문자형, 값엔 모든 자료형이 허용됩니다.
프로퍼티 키는 '프로퍼티 이름'이라고도 불립니다.

```js
let user = new Object(); // 객체 생성자 문법
let user = {}; // 객체 리터럴 문법
```

### 리터럴과 프로퍼티
중괄호 안에는 '키:값' 쌍으로 구성된 프로퍼티가 들어갑니다.
```js
let user = {
  name: 'John',
  age: 30,
}

// 프로퍼티 값 얻기
alert(user.name); // John
alert(user.age); // 30
```
`delete` 연산자를 사용하면 프로퍼티를 삭제할 수 있습니다.
```js
delete user.age;
```
여러 단어를 조합해 프로퍼티 이름을 만든 경우엔 프로퍼티 이름을 따옴표로 묶어줘야 합니다.
```js
let user = {
  name : 'John',
  age: 30,
  "like birds": true // 복수의 단어는 따옴표로 묶어야 합니다.
}
```
상수 객체는 수정될 수 있습니다.
`const`로 선언된 객체는 수정될 수 있습니다.
```js
const user = {
  name : 'John'
};

user.name = 'Pete'; // (*)

alert(user.name); // Pete
```
### 대괄호 표기법
여러 단어를 조합해 프로퍼티 키를 만든 경우엔, 점 표기법을 사용해 프로퍼티 값을 읽을 수 없습니다.

'점'은 키가 '유효한 변수 식별자'인 경우에만 사용할 수 있습니다.
유효한 변수 식별자엔 공백이 없어야 합니다.
또한 숫자로 시작하지 않아야 하며 `$`와`_`를 제외한 특수 문자가 없어야 합니다.

키가 유효한 변수 식별자가 아닌 경우엔 점 표기법 대신에 대괄호 표기법이라 불리는
방법을 사용할 수 있습니다.
대괄호 표기법은 키에 어떤 문자열이 있던지 상관없이 동작합니다.
```js
let user = {};

// set
user['like birds'] = true;

// get
alert(user['likes birds']); // true

// delete
delete user['likes birds'];
```
대괄호 표기법 안에서 문자열을 사용할 땐 문자열을 따옴표로 묶어줘야 한다는 점에
주의해야합니다. 따옴표의 종류는 상관없습니다.
```js
let key = 'likes birds';

// user["likes bird"] = true 와 같습니다.
user[key] = true;
```

### 계산된 프로퍼티
객체를 만들 때 객체 리터럴 안의 프로퍼티 키가 대괄호로 둘러싸여 있는 경우,
이를 계산된 프로퍼티라고 부릅니다.
```js
let fruit = prompt('어떤 과일을 구매하시겠습니까?', 'apple');

let bag = {
  [fruit]: 5, // 변수 fruit에서 프로퍼티 이름을 동적으로 받아 옵니다.
}

alert(bag.apple); // fruit에 'apple'이 할당되었다면, 5가 출력됩니다.
```

### 단축 프로퍼티
```js
function makeUser(name, age) {
  return {
    name, // name : name 과 같음
    age: 30,
  }
}
```
### 프로퍼티 이름의 제약사항

변수 이름(키)엔 `for`, `let` , `return` 같은 예약어를 사용하면 안되지만
객체 프로퍼티엔 이런 제약이 없습니다.
하지만, 역사적인 이유 때문에 특별 대우를 받는 이름이 하나 있습니다.
바로, `__proto__` 입니다.
```js
let obj = {};
obj.__proto__ = 5; // 숫자를 할당합니다.
alert(obj.__proto__); // [object Object] - 숫자를 할당했지만 값은 객체가 되었습니다.
```

### 'in' 연산자로 프로퍼티 존재 여부 확인하기
자바스크립트 객체의 중요한 특징 중 하나는 다른 언어와는 달리,
존재하지 않는 프로퍼티에 접근하려 해도 에러가 발생하지 않고
`undefined`를 반환한다는 것입니다.
이런 특징을 응용하면 프로퍼티 존재 여부를 쉽게 확인할 수 있습니다.
```js
let user = {};

alert(user.noSuchProperty === undefined ); // true는 '프로퍼티가 존재하지 않음'을 의미
```

이렇게 `undefined`와 비교하는 것 이외에도 연산자 `in`을 사용하면
프로퍼티 존재 여부를 확인할 수 있습니다.
```js
'key' in object
```

```js
let user = {name: 'John', age: 30};

alert('age' in user); // user.age가 존재하므로 true가 출력됩니다.
alert('blabla' in user); // user.blabla는 존재하지 않기 때문에 false가 출력됩니다.
```

### for in 반복문
`for..in` 반복문을 사용하면 객체의 모든 키를 순회할 수 있습니다.
```js
const user = {
  name : 'John',
  age: 30,
  isAdmin: true
}

for(let key in user) {
  alert(key); // name, age, isAdmin

  alert(user[key]); // John, 30 , true
}
```

