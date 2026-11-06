# tmux config

Конфигурация tmux без префикса: все бинды висят на Alt/Meta, плюс TUI-справочник клавиш по F12.

## Состав

| Файл | Назначение |
|------|------------|
| `tmux.conf` | основная конфигурация |
| `tmux copy.conf` | альтернативный/резервный вариант конфига |
| `keys.conf` | список биндов для справочника: `КЛАВИША\|Описание\|команда tmux` |
| `keys-tui` | TUI-справочник на whiptail (используется по F12 из popup) |
| `keys-tui-fzf` | тот же справочник на fzf, для прямого запуска в терминале |
| `Сравнение_tmux_конфигов.md` | заметки-сравнение вариантов конфига |

## Что настроено

- Нумерация окон и панелей с 1, вим-навигация `M-h/j/k/l`, мышь включена.
- Сплиты `M-v` (вертикально) / `M-s` (горизонтально) в текущей директории, зум `M-f`.
- Ресайз панелей `M-S-стрелки` и `M-C-h/j/k/l`.
- Сессии: `M-w` дерево, `M-n` новая именованная, `M-d` detach, `M-Q` убить.
- Copy-mode в стиле vi: `M-y` вход, `v` выделение, `y` копировать, `q` выход.
- `escape-time 0`, `set-clipboard on`, `allow-passthrough on` — для vim/neovim и OSC 52.
- `M-r` перезагрузка конфига, `F12` справочник клавиш в popup.
- Плагины через TPM: resurrect, continuum (автосохранение каждые 15 мин), themepack.

## Установка

```sh
git clone <this-repo> ~/.config/tmux
ln -sf ~/.config/tmux/tmux.conf ~/.tmux.conf   # или tmux -f ~/.config/tmux/tmux.conf
chmod +x ~/.config/tmux/keys-tui ~/.config/tmux/keys-tui-fzf
git clone https://github.com/tmux-plugins/tpm ~/.config/tmux/plugins/tpm
~/.config/tmux/plugins/tpm/bin/install_plugins
```

Каталог `plugins/` в репозиторий не входит — TPM ставит плагины сам.

## Требования

tmux 3.2+ (`display-popup`, `allow-passthrough`), `whiptail` или `fzf` для справочника.
