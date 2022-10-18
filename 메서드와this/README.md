# 메서드와 this

### 메서드 만들기
객체 `user` 에게 인사할 수 있는 능력을 부여해 줍시다.
```js
let user = {
  name : 'John',
  age: 30
};

user.sayHi = function() {
  alert('안녕하세요');
}

user.sayHi(); // 안녕하세요
```
함수 표현식으로 함수를 만들고, 객체 프로퍼티 `user.sayHi`에 함수를 할당해 주었습니다.
이제 객체에 할당된 함수를 호출하면 user가 인사를 해줍니다.
이렇게 객체 프로퍼티에 할당된 함수를 **메서드**라고 부릅니다.
메서드는 이미 정의된 함수를 이용해서 만들 수도 있습니다.
```js
let user = {
  ...
};

function sayHi() {
  alert('안녕하세요');
};

// 선언된 함수를 메서드로 등록
user.sayHi = sayHi;

user.sayHi(); // 안녕하세요
```

### 메서드 단축 구문
객체 리터럴 안에 메서드를 선언할 때 사용할 수 있는 단축 문법은 아래와 같습니다.
```js
// 아래 두 객체는 동일하게 동작합니다.

user =  {
  sayHi: function() {
    alert('Hello');
  }
};

user = {
  sayHi() {
    alert('Hello');
  }
};
```
위처럼 `function`을 생략해도 메서드를 정의할 수 있습니다.

### 메서드와 this
메서드는 객체에 저장된 정보에 접근할 수 있어야 제 역할을 할 수 있습니다.
모든 메서드가 그런 건 아니지만, 대부분의 메서드가 객체 프로퍼티의 값을 활용합니다.

`user.sayHi()`의 내부 코드에서 객체 `user`에 저장된 이름을 이용해 인사말을 만드는 경우가
이런 경우에 속합니다.
**메서드 내부에서 `this` 키워드를 사용하면 객체에 접근할 수 있습니다.**
이때 '점 앞'의 `this`는 객체를 나타냅니다. 정확히는 메서드를 호출할 때 사용된 객체를 나타냅니다.
```js
let user = {
  name : 'John',
  age : 30,

  sayHi() {
    // this 는 현재 객체를 나타냅니다.
    alert(this.name);
  }
};

user.sayHi(); // John
```
`user.sayHi()`가 실행되는 동안 `this`는 `user`를 나타냅니다.
`this`를 사용하지 않고 외부 변수를 참조해 객체에 접근하는 것도 가능합니다.
```js
let user = {
  name: 'John',
  age: 30,

  sayHi() {
    alert(user.name); // this 대신 user를 이용함
  }
};
```

하지만 이렇게 외부 변수를 사용해 객체를 참조하면 예상치 못한 에러가 발생할 수 있습니다.
```js
let user = {
  name : 'John',
  age: 30,

  sayHi() {
    alert(user.name); // Error : Cannot read property 'name' of null
  }
}

let admin = user;
user = null; // user를 null로 덮어씁니다.

admin.sayHi(); // sayHi()가 엉뚱한 객체를 참고하면서 에러가 발생합니다.
```
`alert`함수가 `user.name` 대신 `this.name`을 인수로 받았다면 에러가 발생하지 않았을 겁니다.

### 자유로운 this
자바스크립트의 `this`는 다른 프로그래밍 언어의 `this`와 동작 방식이 다릅니다.
자바스크립트에선 모든 함수에 `this`를 사용할 수 있습니다.
아래와 같이 코드를 작성해도 문법 에러가 발생하지 않습니다.
```js
function sayHi() {
  alert(this.name);
}
```
`this` 값은 런타임에 결정됩니다. 컨텍스트에 따라 달라지죠.
동일한 함수라도 다른 객체에서 호출했다면 `this`가 참조하는 값이 달라집니다.
```js
let user = {name : 'John'};
let admin = {name : 'Admin'};

function sayHi() {
  alert(this.name);
}

// 별개의 객체에서 동일한 함수를 사용함
user.f = sayHi;
admin.f = sayHi;

// this는 점 앞의 객체를 참조하기 때문에 this값이 달라짐
user.f(); // John (this == user);
admin.f(); // Admin (this == admin);

admin['f'](); // Admin (점과 대괄호는 동일하게 동작함)
```

`use strict` 모드에서 객체 없이 호출을 한다면 `this`엔 `undefined`가 할당됩니다.
따라서, `this.name`에 접근하려고하면 에러가 발생합니다.
하지만 엄격 모드가 안리 때는 `this`가 전역 객체를 참조합니다.

### this가 없는 화살표 함수
화살표 함수는 일반 함수와는 달리 고유한 `this`를 가지지 않습니다.
화살표 함수에서 `this`를 참조하면, 화살표 함수가 아닌 평범한 외부 함수에서 `this`값을 가져옵니다.
```js
let user = {
  firstName : '보라',
  sayHi() {
    let arrow = () => alert(this.firstName);
    arrow();
  }
}

user.sayHi(); // 보라
```
화살표 함수에는 `this`가 없기 때문에 선언될 시점에서의 상위 스코프가 `this`로 바인딩됩니다.