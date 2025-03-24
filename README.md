
# 📌 Objects in JavaScript  



## 1. Объекты в JavaScript  

Объект в JavaScript — это структура данных, состоящая из пар "ключ-значение".  

### 🔹 Создание объекта  

```javascript
const user = {
  name: "Alice",
  age: 25,
  isAdmin: false
};
console.log(user); 
// { name: "Alice", age: 25, isAdmin: false }
```

### 🔹 Доступ к свойствам  

```javascript
console.log(user.name); // Alice
console.log(user["age"]); // 25
```

### 🔹 Добавление и удаление свойств  

```javascript
user.email = "alice@example.com"; // Добавляем свойство
delete user.age; // Удаляем свойство
console.log(user);
```

### 🔹 Перебор свойств  

```javascript
for (let key in user) {
  console.log(`${key}: ${user[key]}`);
}
```

---

## 2. Деструктуризация и spread-оператор  

### 🔹 Деструктуризация объекта  

Позволяет извлекать свойства объекта в переменные.  

```javascript
const person = { name: "Bob", age: 30 };
const { name, age } = person;
console.log(name, age); // Bob 30
```

### 🔹 Деструктуризация массива  

```javascript
const numbers = [1, 2, 3];
const [first, second] = numbers;
console.log(first, second); // 1 2
```

### 🔹 Spread-оператор  

Оператор `...` позволяет развернуть объект или массив.  

```javascript
const user1 = { name: "Alice", age: 25 };
const user2 = { ...user1, isAdmin: true };
console.log(user2);
// { name: 'Alice', age: 25, isAdmin: true }
```

---

## 3. `this` в JavaScript  

Ключевое слово `this` указывает на объект, к которому привязана функция.  

### 🔹 `this` в методах объекта  

```javascript
const obj = {
  name: "John",
  greet() {
    console.log(`Hello, ${this.name}!`);
  }
};
obj.greet(); // Hello, John!
```

### 🔹 `this` в обычных функциях  

В строгом режиме `this` равно `undefined`, а в нестрогом указывает на `window`.  

```javascript
function showThis() {
  "use strict";
  console.log(this);
}
showThis(); // undefined
```

### 🔹 `this` в стрелочных функциях  

Стрелочные функции не имеют своего `this`, а используют `this` из внешней функции.  

```javascript
const arrowFunc = () => console.log(this);
arrowFunc(); // Наследует `this` из внешнего контекста
```

---

## 4. Методы `call`, `apply`, `bind`  

Методы `call`, `apply` и `bind` позволяют явно задавать `this` для функции.  

### 🔹 `call`  

Метод `call` вызывает функцию с указанным `this` и аргументами.  

```javascript
function greet() {
  console.log(`Hello, ${this.name}`);
}
const user = { name: "Alice" };
greet.call(user); // Hello, Alice
```

### 🔹 `apply`  

Работает как `call`, но принимает аргументы в виде массива.  

```javascript
function introduce(age, city) {
  console.log(`${this.name} is ${age} years old and lives in ${city}.`);
}
introduce.apply(user, [25, "New York"]);
```

### 🔹 `bind`  

Создаёт новую функцию с привязанным `this`.  

```javascript
const boundGreet = greet.bind(user);
boundGreet(); // Hello, Alice
```

---

