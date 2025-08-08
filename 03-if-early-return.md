# Ранний выход из функции

Мы часто сталкиваемся с ситуациями, когда нужно проверить несколько условий перед выполнением основной логики функции. Многие встречали код с множеством вложенных условий:

```typescript
const init = () => {
  const rawAuthToken = localStorage.getItem("rawAuthToken");

  if (rawAuthToken) {
    const token = JSON.parse(rawAuthToken);

    if (token.user && token.user.id) {
      console.log(`✅ success #${token.user.id}`);
    }
  }
};
```

Такой код сложно читать из-за большой вложенности. Ранний выход делает код более предсказуемым и легким для понимания. Каждая проверка становится явной, и мы точно знаем, почему функция может прекратить выполнение на определенном этапе.

```typescript
const init = () => {
  const rawAuthToken = localStorage.getItem("rawAuthToken");

  if (!rawAuthToken) return;

  const token = JSON.parse(rawAuthToken);

  if (!token.user || !token.user.id) return;

  console.log(`✅ success #${token.user.id}`);
};
```
