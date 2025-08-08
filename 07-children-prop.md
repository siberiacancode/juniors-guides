# Children prop

При создании компонентов в React мы часто сталкиваемся с ситуацией, когда нужно передать содержимое внутрь компонента. Для этого в React существует специальный проп `children`, который позволяет передавать любой контент между открывающим и закрывающим тегами компонента. Это делает компоненты более гибкими и переиспользуемыми.

```tsx
import type { ComponentProps, ReactNode } from "react";

interface ButtonProps extends ComponentProps<"button"> {
  children: ReactNode;
}

const Button = ({ children, ...props }: ButtonProps) => (
  <button {...props}>{children}</button>
);

export const App = () => <Button>Click</Button>;
```

Важно помнить, что `children` — это обычный проп, и мы можем ограничивать его типизацию так же, как и любой другой. Например, если компонент должен принимать только текст, можно указать `children: string`.
