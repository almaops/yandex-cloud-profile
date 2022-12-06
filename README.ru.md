# `ycp`: Простая утилита для перемещения между профилями Yandex Cloud

![Написано на Bash](https://img.shields.io/badge/written%20in-bash-ff69b4.svg)

Этот репозиторий предоставляет утилиту `ycp`. [Установить &rarr;](#установка)

## Что такое `ycp`?

**ycp** -- это утилита для болнн быстрого перемещения между профилями **yc**.<br/>

### Примеры

```sh
# switch to another profile
% ycp almaops-terraform-prod
Profile 'almaops-terraform-prod' activated

# switch back to previous profile
% ycp -
Profile 'almaops-terraform-dev' activated

# get current yandex cloud profile
% ycp -c
almaops-terraform-dev
```

Если у вас установлен [`fzf`](https://github.com/junegunn/fzf), вы можете выбирать 
профиль **интерактивно**, а также выполнять быстрый поиск по всего по нескольким символам.
Чтобы узнать больше, прочитайте про [интерактивный режим &rarr;](#интерактивный-режим)

-----

## Установка

Стабильные версии `ycp` -- это небольшие bash-скрипты, которые вы можете найти в этом
репозитории.

**Варианты установки:**

- [ручная (macOS & Linux)](#ручная-установка-macos-и-linux)

### Ручная установка (MacOS и Linux)

Поскольку `ycp` написан на Bash, вы сможете установить его в любом POSIX окружении,
в котором есть Bash.

- Скачайте скрипт `ycp`.
- Одно из двух:
  - сохраните его куда-либо в свой `PATH`,
  - либо сохраните его в директорю, и затем создайте симлинк на `ycp` откуда-либо
    из вашего `PATH`, например из `/usr/local/bin`
- Сделайте `ycp` исполняемым (`chmod +x ...`)

Пример шагов для установки:

``` bash
sudo git clone https://github.com/almaops/ycp /opt/ycp
sudo ln -s /opt/ycp/ycp /usr/local/bin/ycp
```

-----

### Интерактивный режим

Если вы хотите, чтобы команда `ycp` предоставляла вам интерактивный режим с быстрым поиском,
вам просто нужно [установить `fzf`](https://github.com/junegunn/fzf) в свой `$PATH`.

Если у вас уже установлен `fzf`, но вы не хотите использовать это опцию, выставите переменную
окружения `YCP_IGNORE_FZF=1`.

Если вы хотите оставить интерактивный режим `fzf`, но вам нужно поведение утилиты по-умолчанию,
вы можете добиться этого просто перенаправив её вывод в другую команду (напр. `ycp | cat `).

-----

### Настройка цветов

Если вам захочется поменять цвета, обозначающие активный профиль,
установите переменные `YCP_CURRENT_FGCOLOR` и
`YCP_CURRENT_BGCOLOR` (справку по кодам цветов можно найти
[тут](https://linux.101hacks.com/ps1-examples/prompt-color-using-tput/)):

```sh
export YCP_CURRENT_FGCOLOR=$(tput setaf 6) # blue text
export YCP_CURRENT_BGCOLOR=$(tput setab 7) # white background
```

Цветной вывод можно отключить, выставив переменную окружения [`NO_COLOR`](https://no-color.org/).