# React

## 제어필드

인풋의 값이 스테이트에 의해 세팅되는 폼 요소를 말합니다.

인풋 = 직원
스테이트 = 사장님

직원인 저는 안변해요 사장님이 변해야 직원이 변합니다.

스테이트는 인풋에게 현재값이 무엇이어야 하는지 알려줘야만 합니다.

``` js
render() {
	return (
		<div>
			<input onChange = { event => this.setState({ term : event.target.value })} />
		</div>
	)
}
```

``` js
render() {
	return (
		<div>
			<input
				// 1. 잘됨
				value={this.state.term}
				onChange = { event => this.setState({ term : event.target.value })} />

				// 2. 타이핑이 안쳐짐
				value={this.state.term}
		</div>
	)
}
```

위에꺼 설명

`this.state.term`에 의해 값을 제공받을 인풋을 제어 컴포넌트

인풋이기때문에 업데이트가 필요(제어 요소이기에 업데이트가 필요한게 아니다.)

`onChange`가 스테이트에게 여기 새로운 변화된 값이 있다고 알려준다.

인풋은 스스로 아는것이 아니라 반대다.

this.setStatesms 컴포넌트를 리렌더링하고
인풋값을 리렌더링할때 this.state의 term에 새로운 값을 세팅

요약

앱이 실행하면 index.js에서

searchBar 인스턴스 렌더링(search_bar.js)
인스턴스 생성 -> constructor -> this.state의 term이 빈문자열 초기화 -> 컴포넌트는 `this.state`의  `term`값을 가져와서 인풋값을 렌더링 -> 초기값은 빈 문자열

컴포넌트가 렌더링 되던 유저가 문자를 입력할때까지 기다리다가, 값이 입력되면 스테이트가 업데이트됩니다.

this.state의 term이 변화된 텍스트와 같아진다.

이것이 유용한 예

인풋 안에 기본값을 정하길 원할때(플레이스홀더말고)

``` js
constructor(props) {
	super(props)
	this.state = {term: "기본값"};
}
```
