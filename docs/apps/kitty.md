---
aggregation:
  sisyphus: kitty
appstream:
  id: kitty.desktop
  name: Kitty
  icon: /kitty/kitty-logo.svg
  summary: Быстрый, многофункциональный, кроссплатформенный терминал с поддержкой графического процессора
  developer:
    name: Kovid Goyal
    nickname: kovidgoyal
    avatar: https://avatars.githubusercontent.com/u/1308621?v=4
  metadata_license:
    name: GNU GPLv3
    link: https://choosealicense.com/licenses/gpl-3.0/
  url:
    homepage: https://sw.kovidgoyal.net/kitty/
    bugtracker: https://github.com/kovidgoyal/kitty/issues
---

# Kitty

Kitty — эмулятор терминала с поддержкой графического ускорения для Linux, macOS и некоторые дистрибутивы BSD. Он ориентирован на производительность и функциональные возможности, написан C и Python.

К его особенностям можно отнести:

- Отображение изображений с установленной программой ImageMagick;
- Интерактивный ввод символов Unicode по имени, коду, которые недавно использовались;
- Поддерживает функции реального цвета и форматирования текста;
- Разбиение на листы нескольких окон и вкладок;
- Один конфигурационный файл;
- Переходы по гиперссылкам;
- Поддержка мыши (например, в Vim);
- Несколько буферов копирования/вставки, как в Vim;
- Рендеринг в OpenGL.

Kitty поддерживает дополнительные программы под названием Kittens («котята») расширяют его функционал. Также он популярен благодаря возможности полной настройки внешнего вида: пользователь может настроить любой элемент терминала, полностью адаптировав его под себя.

<!--@include: @apps/.parts/install/content-repo.md-->

## Основные клавиатурные сокращения

### Перемещение

| Действие                                                                 | Комбинация клавиш                  |
| ------------------------------------------------------------------------ | ---------------------------------- |
| Курсор на строку вверх/вниз                                              | [[Ctrl + Shift + ↑/↓]]             |
| Курсор на экран вверх/вниз                                               | [[Ctrl + Shift + PageUp/PageDown]] |
| К началу/концу терминала                                                 | [[Ctrl + Shift + Home/End]]        |
| К предыдущей/следующей исполненной команде                               | [[Ctrl + Shift + Z/X]]             |
| Использовать `less` для перемещения по экрану / выводу последней команды | [[Ctrl + Shift + H/G]]             |

### Вкладки

| Действие                         | Комбинация клавиш                                                |
| -------------------------------- | ---------------------------------------------------------------- |
| Открыть/Закрыть вкладку          | [[Ctrl + Shift + T/Q]]                                           |
| Следующая/Предыдущая вкладка     | [[Ctrl + Shift + →/←]] или [[Ctrl + Tab]]/[[Ctrl + Shift + Tab]] |
| Передвинуть вкладку вперёд/назад | [[Ctrl + Shift + ./,]]                                           |
| Изменить заголовок вкладки       | [[Ctrl + Shift + Alt + T]]                                       |

### Окна

| Действие                                       | Комбинация клавиш          |
| ---------------------------------------------- | -------------------------- |
| Открыть/Закрыть окно                           | [[Ctrl + Shift + Enter/W]] |
| Новое окно в системе                           | [[Ctrl + Shift + N]]       |
| Следующее расположение разделённых терминалов  | [[Ctrl + Shift + L]]       |
| Изменение размера окна                         | [[Ctrl + Shift + R]]       |
| Следующее/Предыдущее окно                      | [[Ctrl + Shift + ]\\[]]    |
| Передвинуть окно вперёд/назад/наверх           | [[Ctrl + Shift + F/B/\`]]  |
| Перейти на определённое окно                   | [[Ctrl + Shift + 1-9]]     |
| Выбор окна для выделения в визуальном режиме\* | [[Ctrl + Shift + F7]]      |
| Поменять окна местами в визуальном режиме\*    | [[Ctrl + Shift + F8]]      |

![](/kitty/kitty-1.png '*Режим визуального взаимодействия с окнами')

## Настройка

Конфигурационный файл находится по пути `~/.config/kitty/kitty.conf`. Через него можно настроить все аспекты терминала.

Все опции настройки можно найти [в официальной документации](https://sw.kovidgoyal.net/kitty/conf/).

:::details Пример конфигурационного файла

```
font_family      FiraCode Nerd Font
font_size        14

hide_window_decorations yes
enable_audio_bell no

tab_bar_edge            bottom
tab_bar_style           powerline
tab_powerline_style     slanted
tab_title_template      {title}{' :{}:'.format(num_windows) if num_windows > 1 else ''}

active_tab_foreground   #fff
active_tab_background   #222
inactive_tab_foreground #fff
inactive_tab_background #000
tab_bar_background      #000
```

Разбор параметров:

| Опция                                                                      | Описание                                                            |
| -------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `font_family`                                                              | Используемый шрифт                                                  |
| `font_size`                                                                | Размер шрифта по умолчанию                                          |
| `hide_window_decorations` (`yes`/`no`)                                     | Скрыть системные декорации окна (рамка, заголовок окна)             |
| `enable_audio_bell` (`yes`/`no`)                                           | Управление звуковым сигналом при неверном вводе                     |
| `tab_bar_edge` (`top`/`bottom`)                                            | Положение панели вкладок                                            |
| `tab_bar_style` (`fade`/`slant`/`separator`/`powerline`/`custom`/`hidden`) | Стиль панели вкладок                                                |
| `tab_powerline_style` (`angled`/`slanted`/`round`)                         | Дополнительные опции стиля (доступно при `tab_bar_style powerline`) |
| `tab_title_template`                                                       | Шаблон имени вкладки (позволяет использовать условные операторы)    |
| `active_tab_foreground/active_tab_background`                              | Настройка цвета текста и фона активной вкладки соответственно       |
| `inactive_tab_foreground/inactive_tab_background`                          | Настройка цвета текста и фона неактивной вкладки соответственно     |
| `tab_bar_background`                                                       | Настройка фона панели вкладок                                       |

:::