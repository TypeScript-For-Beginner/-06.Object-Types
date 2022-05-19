# 06.Object-Types
타입스크립트에서는 인터페이스와 타입 두 가지 방법으로 정의할 수 있는데 이번 파트에서는 타입으로 객체를 정의하는 법에 대해 다룰 것이다. 

# 6-1. 정의

```jsx
let student; // any 타입

let student: object = {};
let arr: object = [];
let func: object = function() {};
let date: object = new Date();
```

객체는 변수 이름 옆에  :(콜론) 오른쪽 {}(중괄호)를 사용하여 작성한다. 타입을 지정하는 위치로 객체 생성이 아닌 타입스크립트의 기능을 활용해 작성한다. 

기본적으로 typeof 연산자가 `object`로 반환하는 모든 타입을 나타낸다. 여러 타입의 상위 타입이기 때문에 그다지 유용하지 않다.

타입을 별도로 정해주지 않으면 any 타입으로 지정되는데 명시적으로 student: any;도 가능하다.

<aside>
💡  JS는 =(등호)를 사용해 객체를 정의한다.

</aside>

# 6-2. 객체 선언

```jsx
let student: {
	name: string;
	grade: number;
};
```

타입을 지정해주면 해당 타입의 객체만 해당 변수에 저장될 수 있다고 알려주는 것이다.

즉 student라는 객체에는 name필드에 문자열만, age 필드에는 숫자만 저장될 수 있다. 

> 정의된 객체에 값 대입
> 

```jsx
student = {
	name: '학생1',
	grade: 3
};
```

 student에 정의한 객체 타입과 동일한 구조를 가졌기에 위와 같은 student 객체를 저장할 수 있다.

> 정의되지 않은 타입
> 

```jsx
student = {
	isClassMonitor: false
};
```

하지만 아래와 같이 정의되지 않은 필드는 잘못된 타입이다. student객체에 정의된 타입과는 맞지 않기 때문에 저장할 수 없다. 

### 6-2-2. 객체 배열

```jsx
let students: {
	name: string;
	age: number;
}[];
```

[ ] 대괄호를 붙이면 객체 배열로 저장된다.

## 6-3. 타입 추론

앞서 객체를 먼저 만들어 필드와 자료형을 지정했다면 표기를 하지 않고도 객체를 만들 수 있다. 

```jsx
let student = {
    name: '김멋사',
    grade: 3
}
```

타입의 표기가 없는 경우 값을 기반으로 타입을 유추해낸다.

studnet객체의 `name`은 `string`, `grade`는 `number`로 추론 된다. 

### 6-3-1. 최적 공통 타입

## 6-4. **선택적 속성**

```jsx
let car: { type: string, mileage?: number } = { // no error
  type: "Toyota"
};
car.mileage = 2000;
```

필드 이름 뒤에 `?`를 붙이면 옵션 속성이 된다. 옵션 속성을 사용하면 사용자가 선택적으로 사용할 수 있게 된다. 객체 생성 시 지정하지 않고 나중에 값을 추가할 수 있다.

## 6-5. 인덱스 시그니처

```tsx
const student: { [index: string]: number } = {};

student.id = 220101;
student.id = "김멋사";
```

객체를 만들 때 필드의 자료형을 지정하지 않은 채 인덱스를 사용하여 만들 수 있다. 

`student`라는 객체에 `id` 필드를 `string`으로 지정하고 해당 값은 `number`로 추가할 수 있다.
