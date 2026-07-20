# Minecraft Fix

Модификация для [Zapret Hub](https://github.com/bol-van/zapret), позволяющая обходить блокировки сервисов и игровых серверов, связанных с Minecraft.

## Что исправляет

- Доступ к серверам Minecraft Java Edition (порт 25565)
- Работа Discord (голосовые каналы, медиа, STUN)
- Обход блокировок YouTube и Google (включая QUIC)
- Доступ к платформам Modrinth, CurseForge, Forge, NeoForged, PrismLauncher и другим Minecraft-связанным ресурсам
- Поддержка Game Filter для дополнительных игровых портов

## Варианты запуска

| Файл | Описание |
|------|----------|
| `Servers.bat` | Основной скрипт. Использует стратегию `multisplit` для Minecraft и Discord, `fake` для QUIC и голосовых. Поддерживает пользовательские списки. |
| `Servers (ALT).bat` | Альтернатива с комбинированной стратегией `fake+multisplit` и поддержкой пользовательских списков. |
| `Servers (ALT 2).bat` | Стратегия `hostfakesplit` для основных протоколов. Поддерживает пользовательские списки. |
| `Servers (ALT 3).bat` | Гибридная стратегия `fake+multisplit` для TCP и `fake` для UDP. Поддерживает пользовательские списки. |
| `Servers (ALT 4).bat` | Упрощённая стратегия `fake` для всех протоколов с минимальным количеством повторов. Поддерживает пользовательские списки. |
| `Servers (ALT 5).bat` | Стратегия `fake+multidisorder` с автоматической модификацией TLS. Поддерживает пользовательские списки. |
| `Servers (ALT 6).bat` | Комбинированная стратегия `fake+multisplit` с автоопределением TTL. Без пользовательских списков. |
| `Servers (ALT 7).bat` | Минимальный скрипт — обрабатывает только Minecraft (TCP/UDP 25565). |

## Структура файлов

```
Minecraft-Fix/
├── lists/
│   ├── ipset-all.txt           — IP-адреса заблокированных ресурсов
│   ├── list-general.txt        — Домены Modrinth, CurseForge, Forge и др.
│   ├── list-general-user.txt   — Пользовательский список доменов
│   └── list-exclude-user.txt   — Исключения (Microsoft, Xbox, minecraft.net)
├── utils/
│   └── game_filter.enabled     — Конфигурация игрового фильтра
├── Servers.bat                 — Основной скрипт
├── Servers (ALT).bat           — Альтернатива 1
├── Servers (ALT 2).bat         — Альтернатива 2
├── Servers (ALT 3).bat         — Альтернатива 3
├── Servers (ALT 4).bat         — Альтернатива 4
├── Servers (ALT 5).bat         — Альтернатива 5
├── Servers (ALT 6).bat         — Альтернатива 6
└── Servers (ALT 7).bat         — Альтернатива 7
```

## Используемые DPI-стратегии

- **multisplit** — разбиение пакетов с наложением последовательности
- **fake** — отправка поддельных пакетов для обхода DPI
- **hostfakesplit** — подмена имени хоста при разбиении
- **fake+multisplit** — комбинированная стратегия
- **fake+multidisorder** — комбинированная стратегия с перемешиванием сегментов

## Пользовательские списки

Для добавления своих доменов отредактируйте файлы:
- `list-general-user.txt` — домены, к которым нужно обеспечить доступ
- `list-exclude-user.txt` — домены, которые нужно исключить из обработки

## Требования

- [Zapret Hub](https://github.com/bol-van/zapret) от goshkow под [Windows](https://github.com/goshkow/Zapret-Hub), [Linux](https://github.com/peachoff/Zapret-Hub-Linux), [MacOs](https://github.com/goshkow/Zapret-Hub-Mac/).