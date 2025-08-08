# Типизация пропсов

Простой и читаемый способ типизировать пропсы в React — создать рядом тип `Props` и использовать его в сигнатуре компонента: `props: Props`.

```tsx
...

type ButtonVariant = "primary" | "secondary";
interface ButtonProps extends ComponentProps<"button"> {
  children: ReactNode;
  variant?: ButtonVariant;
  ...
}

const Button = ({ variant = "primary", children, ...props }: ButtonProps) => (
    ...
```
