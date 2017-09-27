# React

## state

클래스 기반 컴포넌트는 그 자체의 state 객체를 가집니다.
컴포넌트 스테이트가 바뀔때마다 컴포넌트는 즉시 리렌더링하고
자식 요소들에게도 렌더링하도록 한다.

* 만약 검색바가 어떤 스테이트가 있고, 이것이 변화하면 render() 함수 실행 안에 다른 컴포넌트가 있으면 그것도 리렌더링 된다.

``` js
class SearchBar extends Component { // 문법적 설탕
	render() {
		return <input onChange = { event => console.log(event.target.value)} />;
	}
}
```

state 사용하기전에는 state 객체 초기화

``` js
class SearchBar extends Component {
	// 초기화
	constructor(props) {
		super(props);

		this.state = { term: " " };
	}
	//

	render() {
		return <input onChange = { event => console.log(event.target.value)} />;
	}
}
```

클래스 기반 컴포넌트만 state를 가지고 함수 기반 컴포넌트는 state를 가지지 않는다.

`constructor`함수는 첫번째로 실행되고 클래스가 생성될 때마다 자동적으로 실행된다.

항상 실행 된다. 새 인스턴스가 생성될 떄마다 불려진다.(index.js 에서 <SearchBar /> 부분)

`super` class 상속 Component 클래스를 상속받고 이 부모 클래스 메소드를 호출할 수 있다.


유저가 검색창에 입력할때마다 state 변경 된다.

``` js
constructor(props) {
	super(props);

	this.state = { term: " " };
}
```

---

스테이트를 사용하여 인풋값을 계속 기록하는 부분

이 부분 console.log 대신 state 업데이트

``` js
render() {
	return <input onChange = { event => console.log(event.target.value)} />;
}
```

`constructor` 함수 안에서만 this.state 사용
다른 컴포넌트에서는 this.setState 사용
this.state.term = event.target.value; 는 절대 안된다!!!

``` js
render() {
	return <input onChange = { event => this.setState({ term : event.target.value })} />;
}
```

인풋 컴포넌트 추가
타이핑한 텍스트는 화면에 보여진다.

``` js
render() {
	return (
		<div>
			<input onChange = { event => this.setState({ term : event.target.value })} />
			Value of the input: { this.state.term }
		</div>
	)
}
```

* 인풋 요소를 업데이트하거 값을 변화시킬떄마다,
* onChange에 정의된 함수 실행
* 스테이트 세팅
* this.state.term은 인풋의 값
* state 변경될때마다 컴포넌트 리렌더링
* 렌더링 메소드의 모든 업데이트 된 정보를 DOM에 푸쉬
