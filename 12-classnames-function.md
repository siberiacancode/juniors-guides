# Функция для формирования classnames

При работе с условными CSS классами разработчики часто формируют `className` вручную, что делает код трудночитаемым и подверженным ошибкам.

```tsx
import type { ComponentProps, ReactNode } from "react";

import styles from './Component.module.css'

interface ComponentProps extends ComponentProps<"div"> {
  children: ReactNode;
  selected?: boolean;
  variant?: "primary" | "secondary";
  ...
}

const Component = ({ variant = "primary", selected = false, children, ...props }: ComponentProps) => (
  <div className={`${styles.button} ${styles[variant]} ${selected ? styles.selected : ''}`} {...props}>
    {children}
  </div>
);
```

Такой код сложно читать и легко допустить ошибку с пробелами. Библиотека `clsx` решает эту проблему элегантно. Утилита очень простая, и вы можете легко реализовать ее самостоятельно:

```tsx
import type { ComponentProps, ReactNode } from "react";
import clsx from "clsx";

import styles from './Component.module.css'

interface ComponentProps extends ComponentProps<"div"> {
  children: ReactNode;
  selected?: boolean;
  variant?: "primary" | "secondary";
  ...
}

const Component = ({ variant = "primary", selected = false, children, ...props }: ComponentProps) => (
  <div className={clsx(styles.button, styles[variant], selected && styles.selected)} {...props}>
    {children}
  </div>
);
```

Функция `clsx` автоматически обрабатывает условия, игнорирует `falsy` значения и правильно расставляет пробелы. Код становится декларативным и легко читаемым.
