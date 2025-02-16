## # Literals and Properies

 빈 객체 만드는 법에는 'object constructor ' 문법과 'object literal' 문법이 있음
 
```js title:"How to make an empty object"
// Object constructor
let myObject = new Object(); 

// Object Literal
let yourObject = {};
```

 중괄호{} 안에 properties 가 key: value 방식으로 들어감 (key = name = identifier)

```js
let yourObject = {
	name: "fluolanet",
	age: 24,
	major: "scan", 
}
// 마지막 줄 콤마 넣는걸 trailing 또는 hanging comma라고 함 -> 추가나 옮기기 등 용이
```

 3개의 properties가 있고, 첫 번째 property의 key는 name, value는 "fluolanet"

 CRUD 가능

```js title:CRUD
yourObject.shoeSize = 270; // create
alert(yourObject.name); // read
yourObject.age = 20; // update
delete yourObject.major; //delete
```

 key에 띄어쓰기 있으면 정의할 때 큰따옴표, CRUD 할 때 대괄호 사용
 
```js
let newObj = {
	"my future income": "999999999$"
}

console.log(newObj["my future income"]);
```
