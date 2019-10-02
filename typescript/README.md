# TypeScript MeetUp #3

## 안전성을 지키는 방법 @uhyo

- 거짓말에의한 오염범위를 좁게 한다
  - 변수에 거짓말을 보존하지 않는다.
    - 변수 레벨의 올바름은 인간이 보존
  - 함수의 인터페이스 레벨을 올바르게 보존한다
- 애초부터 거짓말을 피한다
- [TypeScript 3.7](https://qiita.com/uhyo/items/b8d2ea6fbf6214fc4194)

## Product developed effectively?

- 기능
  - Javascript는 아니지만 Javascript이다
  - enum
    - 문자열로서도 사용가능 ( CARD = "CARD")
    - const fn = (card: Card) => { return card }
    - 문자열로 사용하면 없는 항목은 제대로 막힘
  - Null or Undefined
    - stricNull은 null만 체크해줌
    - type Optional<T> = T | undefined | null;
    - 3.7부터 옵셔널 채이닝으로 가능
      - obj?.value || ''
      - obj!.value!
- 변화
  - 인터페이스 타입의 정의를 먼저하자 interface first
- 경계
  - Virtual an Real
    - 유저가 주의할 필요도 있지만 외부에서 들어오는 거짓말이 있음.
      - LocalStorage 따위에서 거짓말이 들어올 가능성이 있음
      - Proto판 따위를 사용하여 거짓을 줄임
      - 프로그램과 외부 세계를 연결하는 Adapter를 확실하게 정의하는게 중요함
- To Typed

## TypeScript제 라이브러리와 개발체험 @Akito0107

- mapped typed
  - for in과 가까운 움직임을 함

```ts
type M<N extends string> = {
  [K in N]: string;
};
```

- 형의 capture

```ts
function capture<N>(a: N): N {
  //
}
```

- 가변장인수
  - 인수가 2개인 경우-
- intersection type?
- method chain like library => yargs (for typescript type)

https://github.com/yargs/yargs

- method chain은 tree shaking이 힘듬.
- method chain은 side effects의 가능성이 있음

- tuple조작 (ts-toolbelt)
- https://github.com/pirix-gh/ts-toolbelt

Ramda (A practical functional library for JavaScript programmers.)
https://github.com/ramda/ramda
