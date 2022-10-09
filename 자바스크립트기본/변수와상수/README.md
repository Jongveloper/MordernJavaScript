# 변수와 상수

대다수의 자바스크립트 애플리케이션은 사용자나 서버로부터 입력받은 정보를 처리하는 방식으로 동작합니다.
변수는 이러한 정보를 저장하는 용도로 사용됩니다.

### 변수
[변수](#변수computer-science)는 데이터를 저장할 때 쓰이는 '이름이 붙은 저장소'입니다.
자바스크립트에선 `let`키워드를 사용해 변수를 생성합니다.
아래 문(statement)은 'message'라는 이름을 가진 변수를 생성(선언)합니다.
```js
let message;
```

이제 할당 연산자 `=`를 사용해 변수 안에 데이터를 저장해봅시다.

```js
let message;

message = 'Hello'; // 문자열을 저장합니다.
```
문자열이 변수와 연결된 메모리 영역에 저장되었기 때문에, 변수명을 이용해 문자열에 접근할 수 있게 되었습니다.
```js
let message;
message = 'Hello';

alert(message); // 변수에 저장된 값을 보여줍니다.
```
아래와 같이 변수 선언과 값 할당을 한 줄에 작성할 수도 있습니다.
```js
let message = 'Hello'; // 변수를 정의하고 값을 할당합니다.

alert(message);
```
한 줄에 여러 변수를 선언하는 것도 가능합니다.
```js
let user = 'John', age=25, message='Hello';
```
이렇게 작성하면 코드가 좀 더 짧아보이긴 하지만 권장하는 방법은 아닙니다.
한 줄에 한 개의 변수를 작성하면 코드가 길어보이지만 읽기엔 편합니다.
```js
let user = 'jong';
let age = 29;
let message = 'Hello';
```
### 현실 속의 비유
'상자'안에 데이터를 저장하는데, 이 상자에 특별한 이름표가 붙어있다고 상상해보면
변수를 좀 더 쉽게 이해할 수 있습니다.
예를 들어, 변수 `message`는 `message`라는 이름표가 붙어있는 상자에
`Hello!`라는 값을 저장한 것이라고 생각할 수 있습니다.
상자 속엔 어떤 값이든 넣을 수 있고 원하는 만큼 값을 변경할 수 있습니다.
```js
let message;

message = 'Hello';
message = 'World'; // 값이 변경되었습니다.

alert(message);
```
값이 변경되면, 이전 데이터는 변수에서 제거됩니다.

변수 두 개를 선언하고, 한 변수의 데이터를 다른 변수에 복사할 수도 있습니다.
```js
let Hello = 'Hello world!';

let message;

message = Hello;

alert(Hello); // Hello world!
alert(message); // Hello world!
```

변수를 두 번 선언하면 에러가 발생합니다.
```js
let message = 'This';
// 'let'을 반복하면 에러가 발생합니다.
let message = 'That';
```
따라서 변수는 딱 한 번만 선언하고, 선언한 변수를 참조할 때는 `let`없이 변수명만 사용해 참조해야 합니다.
잘못된 변수 예시를 아래를 통해 살펴봅시다.

잘못된 변수 예시
```js
let 1a; // 변수명은 숫자로 시작해선 안됩니다.

let my-name; // 하이픈 '-'은 변수명에 올 수 없습니다.

let let = 5; // 예약어는 변수로 사용할 수 없습니다.
```

### 상수
변화하지 않는 변수를 선언할 땐, `let`대신 `const`를 사용합니다.
```js
const myBirthday = '30.08.1994';
```
이렇게 `const`로 선언한 변수를 상수(constant)라고 부릅니다.
상수는 재할당할 수 없으므로 상수를 변경하려고 하면 에러가 발생합니다.
```js
const myBirthday = '30.08.1994';

myBirthday = '01.01.2022'; // error, can't reassign the constant!
```
### 대문자 상수
기억하기 힘든 값을 변수에 할당해 별칭으로 사용하는 것은 널리 사용되는 관습입니다.
이런 상수는 대문자와 밑줄로 구성된 이름으로 명명합니다.
대문자 상수는 **하드 코딩한** 값의 별칭을 만들 때 사용하면 됩니다.
```js
const COLOR_RED = '#F00';
const COLOR_GREEN = '#0F0';

let color = COLOR_RED;
alert(color); // #F00
```

#### 변수(computer science)
컴퓨터 프로그래밍에서 변수는 관련 기호 이름과 쌍을 이루는 추상적인 저장위치이며,
여기에는 값이라고 하는 알려진 정보 또는 알려지지 않은 양의 정보가 포함됩니다.
간단히 말해서 변수는 특정 비트 세트 또는 데이터 유형에 대한 명명된 컨테이너입니다.
변수는 결국 메모리 주소와 연관되거나 식별될 수 있습니다.
변수의 저장 위치는 여러 다른 식별자에 의해 참조될 수 있습니다.
이러한 상황을 [앨리어싱](#앨리어싱)이라고 합니다.
식별자 중 하나를 사용하여 변수에 값을 할당하면 다른 식별자를 통해 액세스할 수 있는 값이 변경됩니다.


#### 앨리어싱
컴퓨팅에서 엘리어싱은 프로그램의 다른 기호 이름을 통해 메모리의 데이터 위치에 액세스할 수 있는 상황을
설명합니다.

### 참고
변수와 상수 : [모던 자바스크립트 튜토리얼](https://ko.javascript.info/variables)
변수 : [변수 위키피디아](https://en.wikipedia.org/wiki/Variable_(computer_science))
앨리어싱 : [앨리어싱 위키피디아](https://en.wikipedia.org/wiki/Aliasing_(computing))