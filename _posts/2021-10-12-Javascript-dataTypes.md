---
title: "# 03. Data Types 🌈"
permalink: /js1/JavascriptDataTypes
tags:
  - [js1]

navigation: true
toc: true
toc_sticky: true

date: 2021-10-12
last_modified_at: 2021-10-12
---

![]()

# 데이터 타입

## Variable
어플리케이션을 실행하게 되면, 어플리케이션마다 쓸 수 있는 메모리가 할당된다.
이 메모리는 텅텅 빈 박스들인데, 어플리케이션마다 그 박스의 갯수가 제한적으로 할당된다.
let name 이라는 키워드로 변수를 정의하면, 한가지의 박스를 가리킬 수 있는 포인터가 생긴다
name이라는 변수가 가리키고 있는 어딘가에 Jeenie라는 값을 저장할 수 있음
추후에 가리키고 있는 곳에 다른값을 넣어 저장할 수 있음 
## Block scope와 Global scope 

### block scope
{  } 이렇게 블럭 안에서 선언된 변수들.
블럭 안에서 선언된 이 name이라는 변수를 밖에서 접근하게 되면 아무값도 나오지않음
- 블럭 밖에서는 접근할 수 없다! 

### global scope
{ } 블럭을 쓰지 않고 파일 안에 바로 정의해서 쓰는 변수들.
- 블럭 밖에서도 접근 가능하고, 블럭 안에서도 접근 가능하다 

=> global 변수는 어플리케이션 실행된 순간부터 끝까지 항상 메모리에 탑재되어 있기 때문에, 최소한으로 쓸 것.
가능하면 class나 함수, if나 for 루프 등 필요한 부분에서만 정의해서 쓰는 것이 좋다. 

## let
let은 es6에 추가됨. mutable data type
* var는 쓰지 말 것!
쓰면 안되는 이유
1. 대부분 프로그래밍 언어에서는 변수를 선언한 후에 값을 할당함
하지만 JS var에서는 선언도 하기전에 값을 할당할 수 있음(미친행동)
이것을 <b>var hoisting</b> 이라고 함
(hoisting이란? 어디에 선언했느냐에 상관없이 제일 위로 끌어올려주는 것을 말함)
2. var는 block scope을 철저하게 무시한다!
block scope 안에서 var로 선언한 변수인데 밖에서 호출이 가능함.
(아무리 깊은 곳에 선언을 한다고 해도 어디에서나 호출할 수가 있어서, 규모가 큰 프로젝트에서 선언하지도 않은 값들이 할당되어서 오기도 함.) 

=> 이러한 위험성 때문에 var 대신 let을 써야함! 

## constants
es6에서 추가됨. immutable data type
값을 한번 할당하면 절대 바뀌지 않음.
기존의 변수를 이용하면, 메모리 어딘가에 할당된 박스를 가리키고 있어서 포인터를 이용해 값을 계속 바꿔나갈 수 있지만
바로 이 constants는 값을 가리키는 포인터가 잠겨있다. 한번 선언과 동시에 할당한 뒤로는 절대 값을 변경할 수 없음
favor immutable data type always
: 웬만하면 한번 할당한 뒤에는 값이 변경되지 않는 그런 데이터타입에 사용해라
이유?
1. 안전성
2. thread safety
어플리케이션이 실행되면 한가지 프로세스가 할당되고 그 프로세스 안에서는 다양한 thread가 동시에 돌아가면서 좀 더 빠르고 효율적으로 동작할 수 있도록 도와준다. 다양한 thread들이 동시에 변수에 접근을 해서 값을 변경할 수 있는데, 동시에 값을  변경한다는 것은 위험하다.
그래서 가능하면 이렇게 값이 변하지 않는 변수를 사용하는 것이 좋다.(앞으로 변경해야할 좋은 이유가 없다면)
코드변경시나 타인이 코드변경시에도 실수를 방지할 수 있다.

바이러스가 mutation을 통해서 계속 유전자의 서열을 바꿔나가듯이,
데이터의 타입에도 변경가능한 mutable과 변경불가능한 immutable이 있다.

Note !
Immutable data types 변경불가
: primitive types, frozen objects
Mutable data types 변경가능
: all objects by defult are mutable in JS
JS에서 array는 mutable data type이다


## variable types
### primitive type 더이상 작은 단위로 나눠질 수 없는 하나의 아이템
number, boolean, null, undefined, simbol

#### number
c언어와 java는 number에 얼마나 큰 데이터를 저장하는지 선언해야하지만 JS는 그럴필요 없음
JS에서는 integer와 decimal number 상관없이 타입은 number

```js
const infinity = 1 / 0;
// positive한 value의 값을 0으로 나누면 무한대
const negativeinfinity = -1 / 0;
// negative한 value의 값을 0으로 나누면 무한대
const nAn = 'not a number' / 2;
// 숫자가 아닌 string을 숫자로 나누게 되면 nAn
* const bigInt = 1224456745889554785n;
// 숫자 끝에 n을 붙이면 bigInt로 인식(아직 지원안되는 브라우저 있음)
```

#### string
한가지의 글자든 여러개의 글자든 다 string 타입.
다른 string과 붙이는 것도 가능
##### template literals
```js
`hi ${brendan}!`
```
이렇게 붙여서 쓸 수 있음

#### boolean
##### false
0, null, undefined,NaN, ' '
##### true
any other type

#### null
```js
let nothing = 'null';
```
명확하게 empty 값을 지정 = null로 값이 할당됨

#### undefined
```js
let x = 'undefined';
let x; // 위와 동일
```

선언은 되었지만 값이 아무것도 들어가지 않음

#### symbol
```js
const symbol1 = Symbol('id');
const symbol2 = Symbol('id');
```

map이나 다른 자료구조에서 고유한 식별자가 필요하거나, 아니면 동시다발적으로 일어날 수 있는 코드에서 우선순위를 주고싶을 때, 정말 고유한 식별자가 필요할 때 사용
식별자를 string으로 두면 다른 코드에서 동일한 string을 만날때 같은 식별자로 간주함
반면 symbol은 동일한 string을 줘도 완전히 다른 식별자로 간주한다

```js
const gsymbol1 = Symbol.for('id');
const gsymbol2 = Symbol.for('id');
```
만약 동일한 식별자를 주고싶다면 이렇게

```js
console.log(`value: ${symbol1.decription}, type: ${tyopof(symbol2)}`)
```
출력하려면 이렇게 description으로 변환해야함





###(2)object type
real-life object, data structure
싱글 아이템들을 묶어서 한 단위, 한 박스로 관리할 수 있게 해줌
물건과 물체 형태를 대표할 수 있는 박스 형태를 뜻함
```js
const ellie ={ name : 'ellie', age : 20 };
```

객체 ellie는 const로 선언되었기때문에 객체ellie가 가리키고있는 메모리의 포인터는 잠겨있어서 다른 object로 할당이 불가능
하지만 객체 ellie 안에는 name과 age라는 변수가 존재함. 그것들을 가리키고있는 포인터는 잠겨있지 않아서 다른 값으로 변경가능!
```js
ellie.age = 21;
```

##### first-class function

function도 다른 데이터 타입처럼 변수에 할당이 가능
함수의 parameter(인자)로도 전달이 됨
함수에서 return 타입으로도 function을 리턴 가능

## Dynamic typing : dynamically typed language
C나 JAVA는 statically type이라 변수 선언 시에 어떤 타입인지 결정해서 선언했지만
JS는 선언할때 타입을 선언하지않고 런타임 시 할당된 값에 따라 타입이 변경될 수 있다
그래서 프로토타입 시에는 정말 유연하지만 규모있는 프로젝트에서는 좋지않다
```js
let text = 'hello';
console.log(`value:${text}, type: ${typeof  text}`) // value:Hello, type:string

text = 1;
console.log(`value:${text}, type: ${typeof  text}`) // value:1, type:number

text = '7' + 5;
console.log(`value:${text}, type: ${typeof  text}`) // value:75, type:string

text = '8' / '2';
console.log(`value:${text}, type: ${typeof  text}`) // value:4, type:number
```
나누기 연산자가 있어서 string이 아닌 number로 변환되며 연산이 된다

=> 런타임 시 할당된 값에 따라 타입이 변하기때문에, 중간에 변수의 값이 바뀌면 오류가 발생한다 

