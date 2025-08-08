# Функция для формирования classnames

При работе с условными CSS классами разработчики часто формируют `className` вручную, что делает код трудночитаемым и подверженным ошибкам.

```tsx
import type { ComponentProps, ReactNode } from "react";

import styles from './Button.module.css'

interface ButtonProps extends ComponentProps<"button"> {
  children: ReactNode;
  selected?: boolean;
  variant?: "primary" | "secondary";
  ...
}

const Button = ({ variant = "primary", selected = false, children, ...props }: ButtonProps) => (
  <button className={`${styles.button} ${styles[variant]} ${selected ? styles.selected : ''}`} {...props}>
    {children}
  </button>
);
```

Такой код сложно читать и легко допустить ошибку с пробелами. Библиотека `clsx` решает эту проблему элегантно. Утилита очень простая, и вы можете легко реализовать ее самостоятельно:

```tsx
import type { ComponentProps, ReactNode } from "react";
import clsx from "clsx";

import styles from './Button.module.css'

interface ButtonProps extends ComponentProps<"button"> {
  children: ReactNode;
  selected?: boolean;
  variant?: "primary" | "secondary";
  ...
}

const Button = ({ variant = "primary", selected = false, children, ...props }: ButtonProps) => (
  <button className={clsx(styles.button, styles[variant], selected && styles.selected)} {...props}>
    {children}
  </button>
);
```

Функция `clsx` автоматически обрабатывает условия, игнорирует `falsy` значения и правильно расставляет пробелы. Код становится декларативным и легко читаемым.
