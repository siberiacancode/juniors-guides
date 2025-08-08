# React строковые пропсы

React‑пропсы очень гибкие и позволяют нам делать разные вычисления. Мы часто работаем со строками в наших приложениях:

```tsx
<Component title={"Title"} />
```

Фигурные скобки `{}` в данном кейсе необязательны.

```tsx
<Component title="Title" />
```

Но мы возвращаемся к `{}` каждый раз, когда хотим использовать JavaScript.

```tsx
const APP_NAME = "siberiacancode";

export const App = () => <Component title={`${APP_NAME} title`} />;
```
