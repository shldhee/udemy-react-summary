## 액션과 액션 생성자

#### 액션과 리덕스 라이프사이클

1. 리덕스 어플리케이션 이벤트(책 선택 클릭) 발생(액션생성자-Action Creator 호출)
1. 액션생성자는 오브젝트 반환
1. 오브젝트는 타입을 가지는데 이게 액션 타입니다.
1. 오브젝트는 실제 액션이다. 그 자체로 액션을 호출한다.
1. 액션은 자동으로 어플리케이션 안에 모든 리듀서에게 전달이 된다.
1. `switch` 액션 타입 분기 지금 예제의 경우에는 액션 타입이 `BOOK_SELETED` 선택되면 `action.book` 반환 (클릭 된 책)
1. 현재 state 를 반환하고 특정한 리듀서를 위한 상태 변화가 없다.
1. 리듀서가 새 스테이트를 만들고 새 스테이트는 모든 컨테이너로 흘러간다.

_Action Creator_

```js
function (return {
  type: BOOK_SELETED // BOOK_SELETED 액션
  book: { title: 'Book 2'}
})
```

_ActionBook Reducer_

```js
switch (action.type) {
  case BOOK_SELETED:
    return action.book;
  default:
    return currentState;
}
```

_state_

```js
{
  activeBook: {title:'Javascript'},
  books: [{title:'Dark Tower'},{title: 'Javascript'}]
}
```
