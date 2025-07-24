# React строковые пропсы

React пропсы очень гибкие и позволяют нам делать разные вычисления. Мы очень часто работаем со строками в наших приложениях:

```tsx
<Component title={"Title"} />
```

Фигурные скобки `{}` в данном кейсе необязатльены.

```tsx
<Component title="Title" />
```

Но мы возращаемся к `{}` каждый раз, когда хотим использовать javascript.

```tsx
const APP_NAME = "siberiacancode";

export const App = () => <Component title={`${APP_NAME} title`} />;
```
