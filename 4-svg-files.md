# Svg в ассетах и проблемы масштабирования

При работе с SVG в веб-приложениях мы часто сталкиваемся с проблемами масштабирования, когда используем их как обычные изображения. Таким образом мы теряем все масштабируемость и мы не можем использовать css, что приводить к росту количества svg.

```tsx
import iceIcon from "../icons/ice.svg";

<img src={iceIcon} width={24} height={24} />;
```

Один из вариантов решения - это создание react компонента

```tsx
import type { ComponentProps } from "react";

const IceIcon = (props: ComponentProps<"svg">) => (
  <svg
    height="1em"
    width="1em"
    xmlns="http://www.w3.org/2000/svg"
    viewBox="0 0 32 32"
    {...props}
  >
    ...
  </svg>
);

<IceIcon width={24} height={24} fill="currentColor" />;
```

## Автоматизация для импортов

Для автоматического преобразования SVG в React компоненты можно использовать svgr. Данная библиотека имеет **cli** для перевода ваших svg в react комопоненты, но также еще можно подключить к нашим любимым билдерам, чтобы получать компонент сразу при импорте:

```tsx
import IceIcon from "../icons/logo.svg";

<IceIcon width={24} height={24} fill="currentColor" />;
```

Svg можно оптимизировать, удалив лишнии атрибуты и оптимизировав path с помощью онлайн инструментов. Важно задавать вашим icons семантически верные названия и корректный **viewBox**.Правильная работа с SVG в веб-приложениях требует понимания их природы как векторной графики. Используя SVG как компоненты, мы получаем все преимущества векторной графики и возможности для кастомизации.

## Спрайты

Если у вас много SVG иконок на одной странице, использование спрайтов может значительно улучшить производительность. SVG спрайт - это один файл, содержащий все иконки, которые можно переиспользовать.

```svg
<svg xmlns="http://www.w3.org/2000/svg" style="display: none;">
  <symbol id="iceIcon" viewBox="0 0 24 24">
    // ice icon
  </symbol>
</svg>
```

Его можно добавть напрямую в ваш html или же подключить отдельным файлом.

```tsx
import type { ComponentProps } from "react";

const IceIcon = (props: ComponentProps<"svg">) => (
  <svg
    height="1em"
    width="1em"
    xmlns="http://www.w3.org/2000/svg"
    viewBox="0 0 32 32"
    {...props}
  >
    <use href="#iceIcon" />
  </svg>
);
```
