# CSS селекторы для состояний компонентов

Большинство состояний компонентов (disabled, hover, focus, loading) нужно реализовывать через CSS селекторы. Это делает код проще, производительнее и автоматически обеспечивает доступность. Также нет необходимости создавать дополнительные классы или JavaScript обработчики для управления состояниями. CSS селекторы позволяют декларативно описать все возможные состояния компонента и их стили.

```tsx
import type { ComponentProps, ReactNode } from "react";

import styles from "./Button.module.css";

interface ButtonProps extends ComponentProps<"button"> {
  children: ReactNode;
}

const Button = ({ children, ...props }: ButtonProps) => (
  <button className={styles.button} {...props}>
    {children}
  </button>
);
```

```css
/* Button.module.css */
.button {
  padding: 12px 24px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: all 0.2s ease;
}

.button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
  background-color: #ccc;
}

.button:focus-visible {
  outline: 2px solid #007bff;
  outline-offset: 2px;
}
```

CSS селекторы автоматически обрабатывают состояния элементов без дополнительного JavaScript. Это делает код более производительным, доступным и простым в поддержке.
