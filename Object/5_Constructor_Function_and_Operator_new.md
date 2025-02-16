## # 생성자 함수

 유사한 `객체` 여러 개 만들 때 `생성자 함수` 사용하면 편함
 - `생성자 함수` 이름은 대문자로 시작
 - `new` 연산자 붙여서 실행

```js title:"생성자 함수"
function Student(yourName, yourMajor, yourAge) {
	this.name = yourName;
	this.major = yourMajor;
	this.age = yourAge;
}

let fluolanet = new Student("LHS", "scan", "24");

console.log(fluolanet.name);
console.log(fluolanet.major);
console.log(fluolanet.age);
```

 `new Student` 가 실행될 때 일어나는 일
 1) `let this = {};`
 2) `this`에 프로퍼티 하나씩 추가
 3)  `this` 반환

