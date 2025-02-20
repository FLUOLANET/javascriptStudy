## #1 모듈?

미리 만들어놓은 함수 세트 파일.
- 다른 js 파일에서 함수 불러와서 쓸 수 있게 해줌
- 그냥  어떤 js 파일에서 `exports` 만 해주면 `모듈`로 사용가능!

## #2 모듈 실습

```js title:"js파일 모듈로 만들기"
// A.js
function helloAndBye(name) {
	console.log('Hello');
	console.log(`My name is ${name}.`);
	console.log('Bye');
}

const someValue = 100;

// module.exports.다른데서쓸이름.이파일에서의이름
module.exports.helloAndBye = helloAndBye;
module.exports.someValue = someValue; // 변수도 가능
```

```js
// B.js
// 모듈 불러오기(두 파일 같은 dir에 있다고 가정)
const funcSet = require('./A.js');

funcSet.helloAndBye('HS'); // 함수
console.log(funcSet.someValue); // 변수
```
