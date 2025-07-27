# Лишняя деструктуризация

При работе с кодом разработчики часто используют деструктуризацию там, где она не нужна. Это приводит к проблемам с переименованием и усложняет код.

```tsx
import { useCounter } from "@siberiacancode/reactuse";

const App = () => {
  const { count, increment, decrement, reset } = useCounter(0);

  ...
};
```

Проблемы такого подхода становятся очевидными при использовании нескольких счетчиков:

```tsx
const App = () => {
  const { count: userCount } = useCounter(0);
  const { count: postCount } = useCounter(0);

  ...
};
```

Лучше оставить объект как есть и обращаться к его свойствам явно:

```tsx
const App = () => {
  const userCounter = useCounter(0);
  const postCounter = useCounter(0);

  ...
};
```

Такой подход делает код более читаемым, избавляет от необходимости придумывать новые имена и четко показывает, к какой сущности относятся методы и значения.
