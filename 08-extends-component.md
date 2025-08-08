# Масштабируемые компоненты

При создании компонентов в React следует использовать расширение компонентов для наследования всех свойств HTML‑элементов. Это делает компоненты масштабируемыми и гибкими:

```tsx
import type { ComponentProps, ReactNode } from "react";

interface ButtonProps extends ComponentProps<"button"> {
  children: ReactNode;
  variant?: "primary" | "secondary";
  ...
}

const Button = ({ variant = "primary", children, ...props }: ButtonProps) => (
  <button className={variant} {...props}>
    {children}
  </button>
);

export const App = () => (
  <Button
    variant="secondary"
    onClick={() => console.log("clicked")}
  >
    Закрыть
  </Button>
);
```

Таким образом мы создаем компонент один раз и получаем масштабируемое решение, которое не требует изменений при добавлении новых HTML‑атрибутов. Типы пропсов компонента важно держать как можно ближе к компоненту и делать их простыми и понятными.
