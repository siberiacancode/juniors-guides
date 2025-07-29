# Оператор nullish или or

При работе со значениями по умолчанию мы часто используем оператор `||` (логическое ИЛИ), но иногда он может привести к неожиданному поведению. В JavaScript есть более точный оператор `??` (nullish coalescing), который работает только с `null` и `undefined`:

```typescript
const config = {
  port: 0,
  debug: false,
  cache: null,
};

const port = config.port ?? 3000; // 0
const port = config.port || 3000; // 3000

const debug = config.debug ?? true; // false
const debug = config.debug || true; // true

const cache = config.cache ?? "memory"; // "memory"
const cache = config.cache || "memory"; // "memory"
```

Оператор `||` считает "ложными" следующие значения: **false**, **0**, **""**, **null**, **undefined**, **NaN**.
Оператор `??` работает только с **null** и **undefined**. Явное применение `??` со значениями, которые могут быть только в позициях "существует" или "не существует", повышает читаемость и понятность вашего кода.
