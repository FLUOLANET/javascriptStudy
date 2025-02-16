 `객체 프로퍼티`에 할당된 `함수`를 `매서드`라고 함
## #1 매서드 생성

```js 
let studentOne = {
	name: "fluolanet",
	age: 24,
	major: "scan",
}

studentOne.helloAndGoodbye = function() {
	alert("Hello");
	alert("GoodBye");
};

studentOne.helloAndGoodbye();
```

 여기서 `helloAndGoodbye`는 `studentOne`이라는 객체에 할당된 매서드.

 단축해서 쓰려면 이렇게도 가능.
 
 ```js title:"매서드 만들기 단축된 버전"
 // version 1
 studentOne = {
	 hihi: function() {
		 alert("hihi");
	}
 };
 
// version 2
studentOne = {
	byebye() {
		alert("byebye");
	}
};
// 둘 다 가능
```

## #2 매서드와 this

어떤 `객체`의`매서드`가 그 `객체`의 `프로퍼티`를 이용하는 경우 `this`사용하면 됨.

```js title:this
studentOne = {
	mayNameIs() {
		alert("this.name");
	}
};
// this == studentOne
```



