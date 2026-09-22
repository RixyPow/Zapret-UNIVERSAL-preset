# Zapret Universal Presets

Готовые универсальные пресеты для **NetZapret** — Windows GUI для работы с Zapret 2.

Репозиторий содержит `.txt`-пресеты, которые можно импортировать и использовать в NetZapret для настройки обхода DPI-блокировок.

> **NetZapret** использует движок и формат пресетов **Zapret 2**, поэтому пресеты из этого репозитория предназначены прежде всего для работы с NetZapret и совместимыми сборками Zapret 2.

---

## 🇷🇺 Русский

### Что здесь находится

Здесь публикуются готовые пресеты для NetZapret.

Основной пресет — **Universal V9**. Он предназначен для универсального использования и содержит правила для различных сервисов и протоколов.

### Пресеты

| Файл                           | Описание                                                                                                            |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------- |
| `Universal_V9.txt`             | Основной универсальный пресет для NetZapret.                                                                        |
| `Universal_V2_1.txt`           | Предыдущая версия универсального пресета.                                                                           |
| `Universal_V2_1_voice_ALT.txt` | Альтернативная версия V2.1 для случаев, когда Discord работает в текстовом режиме, но возникают проблемы с голосом. |

### Что покрывают универсальные пресеты

В зависимости от версии пресета правила рассчитаны на:

* YouTube / googlevideo
* Discord — текст, медиа и голосовой трафик
* Facebook / Instagram / Twitter(X) / LinkedIn
* ChatGPT / Gemini / Notion / Claude / DeepSeek
* RuTracker / rutor и другие торрент-ресурсы
* Riot / Valorant / League of Legends
* различные домены из Russia blacklist
* TCP, TLS, QUIC, UDP и другие необходимые протоколы

Российские сайты и адреса из исключений не должны обрабатываться десинком без необходимости.

---

## NetZapret

Для использования пресетов рекомендуется **NetZapret**:

[RixyPow/netzapret](https://github.com/RixyPow/netzapret?utm_source=chatgpt.com)

NetZapret предоставляет графический интерфейс для настройки и запуска Zapret 2, поэтому отдельная ручная настройка команд и параметров не требуется.

### Как установить пресет

1. Установите NetZapret.
2. Скачайте нужный `.txt`-пресет из этого репозитория.
3. Импортируйте пресет через NetZapret.
4. Выберите его в списке пресетов.
5. Запустите NetZapret.
6. Проверьте работу нужных сервисов.

Для начала рекомендуется использовать **Universal V9**.

---

## Zapret 2

Пресеты основаны на формате и возможностях **Zapret 2**.

Если вы используете оригинальный Zapret 2 или другую GUI-сборку, совместимость конкретного пресета зависит от используемых в нём параметров и правил.

Оригинальный проект:

[Zapret 2](https://github.com/youtubediscord/zapret?utm_source=chatgpt.com)

---

## ⚠️ Если какой-то сервис всё равно не работает

Работа пресета зависит от конкретного провайдера, типа блокировки и текущей конфигурации сети.

Десинк не решает все виды блокировок. Например, проблемы на уровне DNS или IP могут потребовать дополнительных настроек.

Если после запуска пресета сервис не работает:

1. Проверьте DNS.
2. Запустите диагностику/BlockCheck.
3. Попробуйте другой пресет.
4. Проверьте, воспроизводится ли проблема без VPN или другого сетевого ПО.
5. Убедитесь, что используется актуальная версия NetZapret и пресета.

---

## Структура правил

Пресеты состоят из отдельных блоков правил `--new`, каждый из которых предназначен для определённых доменов, списков или протоколов.

В зависимости от пресета могут использоваться стратегии:

* `multidisorder` — обработка TCP/TLS-трафика;
* `send` / `syndata` — отдельные сценарии для TCP-трафика;
* `fake` — работа с QUIC/UDP и другими протоколами;
* дополнительные правила для Discord, YouTube и других сервисов.

Конкретный набор правил может меняться между версиями пресета.

---

## Версии

### Universal V9

Текущая основная версия универсального пресета.

### Universal V8

Лучшая версия по совместимости.

Рекомендуется начинать именно с неё.

### Universal V2.1

Предыдущая версия, оставленная для совместимости и сравнения.

### Universal V2.1 Voice ALT

Альтернативный вариант V2.1 с изменённой обработкой голосового трафика Discord.

---

## Дисклеймер

Пресеты предоставляются **«как есть»** и предназначены для личного и образовательного использования.

Результат работы зависит от провайдера, сети, используемой версии NetZapret/Zapret 2 и текущих методов блокировки.

Пользователь самостоятельно отвечает за соблюдение законодательства своей юрисдикции.

---

## 🇬🇧 English

### About

Ready-to-use universal presets for **NetZapret**, a Windows GUI for working with Zapret 2.

This repository contains `.txt` presets designed primarily for use with NetZapret and compatible Zapret 2 builds.

### Presets

| File                           | Description                                                                              |
| ------------------------------ | ---------------------------------------------------------------------------------------- |
| `Universal_V9.txt`             | Current main universal preset for NetZapret.                                             |
| `Universal_V2_1.txt`           | Previous version of the universal preset.                                                |
| `Universal_V2_1_voice_ALT.txt` | Alternative V2.1 preset for cases where Discord text works but voice traffic has issues. |

### NetZapret

Recommended GUI for using these presets:

[RixyPow/netzapret](https://github.com/RixyPow/netzapret?utm_source=chatgpt.com)

Download the preset, import it into NetZapret, select it, and start the service.

### Zapret 2

The presets use the format and capabilities of **Zapret 2**.

Original project:

[Zapret 2](https://github.com/youtubediscord/zapret?utm_source=chatgpt.com)

### Troubleshooting

If a service does not work with a preset:

1. Check your DNS configuration.
2. Run BlockCheck/diagnostics.
3. Try another preset.
4. Check whether VPN or other network software affects the connection.
5. Make sure NetZapret and the preset are up to date.

### Disclaimer

Presets are provided **“as is”** for personal and educational use.

Results may vary depending on the ISP, network configuration, NetZapret/Zapret 2 version, and current blocking methods.

Users are responsible for complying with the laws applicable in their jurisdiction.
