# TypeScript

## Decorator

class 코드의 중복을 제거하는 패턴

```ts
function makeGender(target: typeof Person) {
  return class extends target {
    gender = "male";
    sayGender() {
      return this.gender;
    }
  };
}

function readonly(target: any, key: any, descriptor: PropertyDescriptor) {
  descriptor.writable = false;
}

@makeGender
class Person {
  constructor() {
    this.title = name;
  }
  setTitle(title) {
    this.title = title;
  }
  @readonly sayTitle() {
    return this.title;
  }
}
```

## Union

여러 개의 interface나 type 중 하나만 만족시켜도 됨

| 이 Union

```ts
interface A {
  hello: true;
}

interface B {
  bye: true;
}

const c: A | B = {
  hello: false,
  bye: true
};
```

## Intersection

여러 개의 interface나 type을 동시에 만족 시켜야 됨

& 이 intersection

```ts
interface A {
  hello: true;
}

interface B {
  bye: true;
}

type C = {
  hi: false;
};

const d: A & B & C = {
  hello: true,
  bye: true,
  hi: false
};
```

## Utilities

https://www.typescriptlang.org/docs/handbook/utility-types.html

### Partial

interface의 일부분만 사용할 때

```ts
interface A {
  a: "a";
  b: true;
  c: 123;
}

const a: A = {
  a: "a",
  b: true,
  c: 123
};

const b: Partial<A> = {
  b: true,
  c: 123
};
```

## Call

Generic을 쓰는 법

```ts

const result = Array.prototype.map.call([1,2,3], (item) => {
  return item.toFixed(1);
})


const result = Array.prototype.map.call<number[], [(item: number) => string], string[]>([1,2,3], (item) => {
  return item.toFixed(1);
}

```

## Base Type

### Boolean

true / false 값을 가짐

```ts
let isDone: boolean = false;
```

### Number

부동 소숫점 값이고 number 타입을 가짐

16진수, 10진수, 8진수, 바이너리를 지원함

```ts
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
```

### String

문자열 데이터에 사용

"" 또는 ''를 사용함

```ts
let color: string = "blue";
color = "red";
```

template string도 사용 가능

``(백틱)으로 사용가능함

```ts
let fullName: string = "Some one";
let age: number = 37;
let sentence: string = `Hello, my name is ${fullName}`;
```

### Array

배열은 두 가지 방법으로 나타낼 수 있음

각 타입에 []를 붙여 해당 타입 나타내기

```ts
let list: number[] = [1, 2, 3];
```

일반적인 배열 타입 Array를 사용

```ts
let list: Array<number> = [1, 2, 3];
```

### Tuple

고정된 수의 요소 타입을 알고 있지만, 값의 종류가 다른 배열을 표현할 수 있음

예를 들어 문자열과 숫자의 쌍을 아래와 같이 표현 가능

```ts
let x: [string, number];

x = ["Hello", 10]; // OK
x = [10, "Hello"]; // Error
```

액세스한 데이터의 처리가 달라질 수 있음

```ts
console.log(x[0].substr(1)); // OK
console.log(x[1].substr(1)); // Error, 'number' does not have 'substr'
```

변수 선언에 포함되지 않은 요소에 대한 액세스는 Tuple 선언에 사용된 타입의 Union 타입으로 사용

```ts
x[3] = "world"; // OK, 'string' can be assigned to 'string | number'
console.log(x[5].toString()); // OK, 'string' and 'number' both have 'toString'
x[6] = true; // Error, 'boolean' isn't 'string | number'
```

### Enum

```ts
enum Color {
  Red,
  Green,
  Blue
}
let color: Color = Color.Green;
```

enum은 0부터 시작해서 멤버의 번호를 매김

멤버 중 하나의 값을 수동으로 설정하여 변경 가능

```ts
enum Color {
  Red = 1,
  Green,
  Blue
}
let color: Color = Color.Green;
```

enum의 모든 값을 수동으로 설정 가능

```ts
enum Color {
  Red = 1,
  Green = 2,
  Blue = 4
}
let color: Color = Color.Green;
```

숫자 값에서 enum의 값 이름으로 이동할 수 있음

```ts
enum Color {
  Red = 1,
  Green,
  Blue
}
let colorName: string = Color[2];

alert(colorName);
```

### Any

```ts
let notSure: any = 4;
notSure = "maybe a string instead";
notSure = false; // okay, definitely a boolean
```

### Void

값을 반환하지 않는 함수의 반환 유형으로 사용

```ts
function warnUser(): void {
  alert("This is warning message");
}
```

void 타입의 변수 선언은 undefined 또는 null 만 가능

```ts
let unusable: void = undefined;
```

### Null 과 Undefined

null 과 undefined는 다른 모든 유형의 하위 유형이라 number와 같은 다른 유형에 할당할 수 있음

```ts
let u: undefined = undefined;
let n: null = null;
```

--strictNullChecks 사용이 권장됨

### Never

```ts
// Function returning never must have unreachable end point
function error(message: string): never {
  throw new Error(message);
}
// Inferred return type is never
function fail() {
  return error("Something failed");
}
// Function returning never must have unreachable end point
function infiniteLoop(): never {
  while (true) {}
}
```

### Object

object는 non-primitive 타입 number, string, boolean, symbol, null, undefined가 아닌 타입을 나타내는 타입

object타입을 사용하면 Object.create와 같은 API를 보다 잘 표현할 수 있음

```ts
declare function create(o: object | null): void;

create({ prop: 0 }); // OK
create(null); // OK
create(42); // Error
create("string"); // Error
create(false); // Error
create(undefined); // Error
```

### Type assertions

1. angle-bracket(<>)

```ts
let someValue: any = "this is a string";
let strLength: number = (<string>someValue).length;
```

2. as

```ts
let someValue: any = "this is a string";
let strLength: number = (someValue as string).length;
```

두 가지 방법의 결과는 동일

TypeScript를 JSX와 함께 사용할 경우 as만 허용됨

# TypeScript MeetUp #3

## 安全性の極北から見る TypeScript @uhyo

https://speakerdeck.com/uhyo/an-quan-xing-falseji-bei-karajian-rutypescript

- 거짓말에의한 오염범위를 좁게 한다
  - 변수에 거짓말을 보존하지 않는다.
    - 변수 레벨의 올바름은 인간이 보존
  - 함수의 인터페이스 레벨을 올바르게 보존한다
- 애초부터 거짓말을 피한다
- [TypeScript 3.7](https://qiita.com/uhyo/items/b8d2ea6fbf6214fc4194)

## Product development with TypeScript

https://speakerdeck.com/brn/purodakutokai-fa-totypescript-657a1b05-0a19-4032-aa40-5656f1d01b63

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
