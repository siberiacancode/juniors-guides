# Оператор ?? против ||

При работе со значениями по умолчанию мы часто используем оператор `||` (логическое ИЛИ), но иногда он может привести к неожиданному поведению. В JavaScript есть более точный оператор `??` (nullish coalescing), который работает только с `null` и `undefined`:

```typescript
const config = {
  port: 0,
  debug: false,
  cache: null,
};

const portNullish = config.port ?? 3000; // 0
const portOr = config.port || 3000; // 3000

const debugNullish = config.debug ?? true; // false
const debugOr = config.debug || true; // true

const cacheNullish = config.cache ?? "memory"; // "memory"
const cacheOr = config.cache || "memory"; // "memory"
```

Оператор `||` считает «ложными» следующие значения: false, 0, "", null, undefined, NaN. Оператор `??` работает только с null и undefined. Явное применение `??` там, где важно различать «нет значения» и «значение 0/false/пустая строка», повышает читаемость и предсказуемость кода.
