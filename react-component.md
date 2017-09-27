# recat

## 컴포넌트 구조

하양 데이터 플로우

부모 컴포넌트는 데이터를 가져올 권리를 가져야 한다.

App 컴포넌트를 함수형 컴포넌트에서 클래스 기반 컴포넌트로 변환

``` js
const App = () => {
	return (
		<div>
			<SearchBar />
		</div>
	)
}
```

const를 정의하는 것 대신에 class를 정의하고 extends로 컴포넌트로부터 상속을 받는다.

error 메세지가 있을시에는 npm start 부분을 살펴본다.

es6

arrow function

``` js
this.setState({ vidoes });
// this.setState({ vidoes: videos });
```


``` js
class App extends Component {
	constructor(props) {
		super(props);

		this.state = { videos: [] };

		YTSearch({key: API_KEY, term: 'surfboards'}, (vidoes) => {
			this.setState({ vidoes });
		});
	}

	render() {
		return (
			<div>
				<SearchBar />
			</div>
		);
	}
}
```
