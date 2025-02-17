
`이벤트`가 발생할 때 특정한 `함수`를 할당해 실행해 줄 수 있는데, 이걸 `Event Handler` 라고 함.

```html title:"Event Handler 할당 방법 1"
<!--방법1-->
<button onclick="alert('clicked!!')">
버튼1
</button>
```

```html title:"Event Handler 할당 방법 2"
<!--방법2-->
<button onclick="hello()">
버튼2
</button>

<script>
const hello = () => {alert("Hello!!")};
</script>
```

```html title:"Event Handler 할당 방법 3"
<!--방법3-->
<button id="third">
버튼3
<button>

<script>
const hello = () => {alert("Hello!!")};
const thirdBtn = document.getElementById('third');
thirdBtn.onclick = hello;
</script>
```

```html title:"Event Handler 할당 방법 4"
<!--방법4-->
<button id="fourth">
버튼4
<button>

<script>
const hello = () => {alert("Hello!!")};
const fourthBtn = document.getElementById('fourth');
fourthBtn.addEventListener('click', hello)
</script>
```

### addEventListener에 대해 알게된점

- `addEventListner` 는 두 개의 인자를 받음
	1) 첫 번째는 event 객체 : 어떤 이벤트인지 
	2) 두 번째는 콜백함수
		- 그런데 이 콜백함수의 인자로는 또 event 객체가 전달됨.
			-> 어떤 이벤트가 감지되면 어떤 함수를 실행하고싶은데 그 함수에 또 어떤 인자를 받고싶으면 아래와 같이 하면 됨.

```js
something.addEventListener('click', (event) => {
	someFunction(someArgument);
});
```
