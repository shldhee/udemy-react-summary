# react

## event

전체코드

``` js
class SearchBar extends Component {
	render() {
		return <input onChange = {this.onInputChange} />;
	}

	onInputChange (e) {
		console.log(e.target.value);
	}
}

export default SearchBar;
```

이 부분이 onChange(리액트 정의된 프로퍼티) 이벤트 발생할때마다 onInputChange 함수를 작동시킨다.

``` js
render() {
	return <input onChange = {this.onInputChange} />;
}
```

`event.target`은 이벤트가 발생하는 요소(여기선 input)

``` js
onInputChange (event) {
	console.log(event.target.value);
}
```

target.value 지우고 console창에서 확인
input.value 값이 있다.

``` js
onInputChange (event) {
	console.log(event);
}
```

ES6 arrow function 사용

``` js
render() {
	return <input onChange = { event => console.log(event.target.value)} />;
}
```

리팩토링 코드

``` js
class SearchBar extends Component { // 문법적 설탕
	constructor(props) {
		super(props)

		this.state = {term: ""};
	}

	render() {
		return <input onChange = { event => console.log(event.target.value)} />;
	}
}

export default SearchBar;
```
