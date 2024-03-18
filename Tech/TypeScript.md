---
type:
  - Tech
tags:
  - Typescript
  - Frontend
  - Javascript
  - Static
published: true
folder: Tech
---
# What is TypeScript?

**TypeScript** is a open-source programming language developed by Microsoft. It is developed based on JavaScript, with some additional features like static typing.

Some main features:
- Static type
- Module system
- Interfaces and classes.
- Generics
- JavaScript support

Some benefits:
- Early error detection
- Improved maintainability
- Increased productivity
- Integration with JavaScript

# TypeScript basic

## Everyday types and variables

```TypeScript
let a: string = "name";
let b: number = 12;
let c: boolean = true;
let d = 100;
let e;     # e has type any until it is assigned
```

## Function

```TypeScript
function addTwo(num: number): number {
	return num + 2;
}

let addThree = (num: number): number => {
	return num + 3;
}
```

## Type

```TypeScript
type User = {
	readonly _id: string;
	name: string;
	email: string;
	isActive: boolean;
	cred?: string;     // you can construct object without it
}

function createUser(user: User) {}
let user: User = {name: "Nam", 
			email: "nam@gmail", 
			isActive: true,
			_id: "12"
			}

user._id = "100"     // you cannot do this
createUser(user)
```

## Array

```TypeScript
const str_arr: string[] = []
const num_arr: number[] = []
const user_arr: User[] = []

num_arr.push(12);
num_arr.pop();
```

## Union type

```TypeScript
let score: number | string = 33;
let person: User | Admin;
const data: (string | number | boolean)[] = [1, "2", true]

score = 12;
score = "12";
```

## Tuple

```TypeScript
let a: [string, number, boolean];

a = [true, 12, "12"];     // you cannot do this
a = ["12", 12, false]     // do this instead

a[0] = "str";
a[1] = 100;
console.log(a[2]);
```

## Enum

```TypeScript
enum Days {
	MONDAY,
	TUESDAY,
	WEDNESDAY,
	THURSDAY,
	FRIDAY,
	SATURDAY,
	SUNDAY
};

const a = Days.MONDAY
console.log(a)     // 0
const b = Days.SUNDAY
console.log(b)     // 6
```

## Interface

```TypeScript
interface User {
	readonly id: number,
	email: string,
	userId: string,
	startTrail: () => string,
	endTrail(nu: number): string
}

startTrail: () => {
	return "";
}

endTrail: (nu) => {
	return `hello ${nu}`;
}

```

## Class

```TypeScript
class User {
	public email: string
	private name: string
	readonly city: string = "HCM"

	constructor(email: string, name: string) {
		this.email = email;
		this.name = name;
	}

	get email(): string {
		return this.email;
	}

	set name(name: string) {
		this.name = name;
	}
}

const user = new User("nam@outlook", "HCM");
```

You can use class to implement some interfaces

# References

<iframe width="560" height="315" src="https://www.youtube.com/embed/30LWjhZzg50" title="Learn TypeScript – Full Tutorial" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
