# Лишний return в стрелочных функциях

В JavaScript мы часто используем стрелочные функции, и иногда добавляем лишние конструкции, которые можно упростить. Стрелочная функция с одним выражением не требует фигурных скобок и `return`:

```javascript
const multiply = (a, b) => {
  return a * b;
};

const multiply = (a, b) => a * b;
```

При работе с асинхронными функциями мы часто добавляем лишний `await` при возврате значения:

```javascript
const getUser = async (id) => {
  const response = await fetch(`/api/user/${id}`);
  return response;
};

const getUser = (id) => fetch(`/api/user/${id}`);
```
