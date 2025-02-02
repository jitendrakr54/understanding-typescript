# Next-generation JavaScript & TypeScript

---

<p style="text-align: center; font-size: 20px; font-weight: bold"> "let" and "const" </p>

`let` is "blocked scoped" `{}`!

```ts
const aName = 'Max'; // it is a const – immutable
console.log(name);
aName = 'Antoine'; // KO, we can't update the value

let age = 30; // we can modify the value
age = 29;

// BUT let is block scoped compared to var

if (age > 20) {
  var isOldWithVar = true;
}

console.log(isOldWithVar); // it works, because var is global in this file

if (age > 20) {
  let isOldWithLet = true;
}

console.log(isOldWithLet); // it won't work
```

---

<p style="text-align: center; font-size: 20px; font-weight: bold"> Arrow Functions </p>

```ts
const add = (a: number, b: number) => {
  return a + b;
};

// When you have only 1 expression, you can remove the curly brace and the return statement

const addShort = (a: number, b: number) => a + b;

// When you have only 1 parameter, you can

const printOutput = (output: number | string) => console.log(output);

printOutput(add(5, 2));

// By defining type of printOutput

const printOutput: (a: number | string) => void = (output) =>
  console.log(output);

printOutput(add(5, 2));
```

---

<p style="text-align: center; font-size: 20px; font-weight: bold"> Default Functions Parameters </p>

The default arguments should be the last ones.

```ts
// default value added
const add = (a: number, b: number = 1) => a + b;

const printOutput: (a: number | string) => void = (output) =>
  console.log(output);

printOutput(add(5));
```

---

<p style="text-align: center; font-size: 20px; font-weight: bold"> The Spread Operator (...) </p>

```ts
const hobbies = ['Sports', 'Cooking'];
const activeHobbies = ['Hiking'];
activeHobbies.push(...hobbies);
// const activeHobbies = ['Hiking', ...hobbies];

const person = {
  name: 'Max',
  age: 30,
};

// We're copying the pointer/reference of the person object in memory to this copiedPerson constant
const copiedPersonShallow = person;

// To create a real copy
const copiedPersonDeep = { ...person };
```

---

<p style="text-align: center; font-size: 20px; font-weight: bold"> Rest Parameters </p>

```js
const add = (...numbers: number[]) => {
  return numbers.reduce((acc, num) => acc + num, 0);
};

const addedNumbers = add(1, 3, 10, 5.5, 3.7);
console.log(addedNumbers);
```

With below code, you always have to pass an array

```js
const add = (numbers: number[]) => {
  return numbers.reduce((acc, num) => acc + num, 0);
};

const addedNumbers = add([1, 3, 10, 5.5, 3.7]);
console.log(addedNumbers);
```

Note: `push` is working in the same way with the rest parameter.

```ts
// you could also use for tuple
const add = (...numbers: [number, number, number]) => {
  return numbers.reduce((acc, num) => acc + num, 0);
};
```

---

<p style="text-align: center; font-size: 20px; font-weight: bold"> Array & Object Destructuring </p>

The important thing here is for array destructuring, elements are pulled out in order because an array is an ordered
list. In objects, the order is not always guaranteed, and therefore, we don't pull elements out by position, but by key
name.

```ts
const hobbies = ['Sport', 'Cooking'];

// const hobby1 = hobbies[0];
// const hobby2 = hobbies[1];

const [hobby1, hobby2, ...remainingHobbies] = hobbies; // doesn't mutate your original array

const person = {
  firstName: 'Max',
  age: 30,
};

const { firstName: userName, age } = person;

console.log(userName, age);
```
