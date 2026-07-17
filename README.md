# Zapret-Universal-Preset

Готовые пресеты для [Zapret 2](https://github.com/youtubediscord/zapret) (GUI) — обход DPI-блокировок на Windows 11. Десинк применяется **только** к явно заблокированным доменам/спискам, обычный трафик (Steam, Riot, российские сайты) не трогается.

---

## 🇷🇺 Русский

### Что внутри

| Файл | Описание |
|---|---|
| `Universal_V2_1.txt` | Основной пресет. Стабильный десинк для YouTube, Discord (текст+звонки), соцсетей, AI-сервисов, торрент-трекеров. |
| `Universal_V2_1_voice_ALT.txt` | Альтернатива для тех, у кого **текст в Discord работает, а голос — нет**. Меняет стратегию для голосовых пакетов (STUN/UDP): `udplen` + `quic2` вместо `quic_google`. |

Оба пресета покрывают:
- YouTube / googlevideo (TCP + QUIC)
- Discord (текст, обновления, медиа, голос/STUN)
- Facebook, Instagram, Twitter/X, LinkedIn
- ChatGPT, Gemini, Notion, Claude, DeepSeek
- RuTracker, rutor и другие торрент-ресурсы
- Riot / Valorant / LoL
- Список Russia blacklist

RU-сайты и адреса из `ipset-exclude.txt` десинку не подвергаются (`pass`).

### ⚠️ WhatsApp, RuTracker, LinkedIn — под полной блокировкой

Эти сервисы блокируются не тем способом, который лечит десинк, поэтому даже с пресетом они могут не открыться:

- **RuTracker** — блокировка на уровне **DNS** (провайдер отдаёт заглушку `81.200.2.238` вместо реального Cloudflare-адреса `104.21.32.39`). Десинк тут бессилен — нужно включить **DNS-over-HTTPS** в GUI Zapret (раздел "Настройка DNS"). После этого сработает тот же multidisorder, что пробивает LinkedIn.
- **LinkedIn** — блокировка полная (IP+DNS+DPI), доступность нестабильна даже с десинком и DoH.
- **WhatsApp** — под полной блокировкой на уровне провайдера, десинк не помогает.

### Установка Zapret 2 с нуля

1. Скачайте GUI-сборку с [github.com/youtubediscord/zapret](https://github.com/youtubediscord/zapret) — раздел релизов, либо `ZapretSetup.exe` по ссылке из шапки репозитория.
2. Запустите установщик — WinDivert ставится вместе с программой.
3. После установки Zapret появится в меню "Пуск".
4. Запускайте GUI **от имени администратора** (обязательно — WinDivert работает на уровне драйвера).

### Как поставить пресет

1. Скачайте нужный `.txt`-файл из этого репозитория.
2. Положите его в папку `presets` внутри директории установки Zapret 2.
3. В GUI откройте список пресетов и выберите `Universal V2.1` (или `V2.1 voice ALT`).
4. Нажмите "Запустить" / "Start".
5. Проверьте работу через встроенный BlockCheck или вручную (открыть YouTube, Discord и т.д.).

### Какой пресет выбрать

- **По умолчанию:** `Universal_V2_1.txt`.
- **Если в Discord пишет, но не звонит (нет звука/картинки в войсе):** переключитесь на `Universal_V2_1_voice_ALT.txt`.

### Zapret2 + Happ VPN

Использую связку Zapret 2 и Happ VPN — VPN включён только для выбранных приложений, а не глобально, поэтому Zapret продолжает обрабатывать остальной трафик напрямую.

### Структура правил (кратко)

Каждый блок `--new` — отдельное правило для конкретного домена/списка/протокола. Основные стратегии:
- `multidisorder` — для TCP/TLS ClientHello (YouTube, соцсети, AI-сервисы, торренты)
- `send + syndata` — для Discord (текст/медиа)
- `fake` (blob quic/stun) — для UDP/QUIC/голоса

### Дисклеймер

Пресеты предоставляются "как есть", для образовательных целей и в рамках использования интернета в личных целях. Автор не несёт ответственности за использование, противоречащее законодательству вашей страны.

---

## 🇬🇧 English

### Contents

| File | Description |
|---|---|
| `Universal_V2_1.txt` | Main preset. Stable desync rules for YouTube, Discord (text + voice), social media, AI services, torrent trackers. |
| `Universal_V2_1_voice_ALT.txt` | Alternative for users whose **Discord text works but voice doesn't**. Changes the strategy for voice packets (STUN/UDP): `udplen` + `quic2` instead of `quic_google`. |

Both presets cover:
- YouTube / googlevideo (TCP + QUIC)
- Discord (text, updates, media, voice/STUN)
- Facebook, Instagram, Twitter/X, LinkedIn
- ChatGPT, Gemini, Notion, Claude, DeepSeek
- RuTracker, rutor and other torrent sites
- Riot / Valorant / LoL
- Russia blacklist domains

RU sites and addresses from `ipset-exclude.txt` are left untouched (`pass`) — no unnecessary desync on domestic traffic.

### ⚠️ WhatsApp, RuTracker, LinkedIn — fully blocked

These services are blocked in a way desync alone doesn't fix, so they may still fail even with the preset running:

- **RuTracker** — blocked at the **DNS level** (your ISP's resolver returns a dead IP `81.200.2.238` instead of the real Cloudflare address `104.21.32.39`). No desync fixes a bad DNS answer — enable **DNS-over-HTTPS** in the Zapret GUI (DNS settings section). Once enabled, the same multidisorder strategy that unblocks LinkedIn will work here too.
- **LinkedIn** — fully blocked (IP+DNS+DPI); availability stays inconsistent even with desync and DoH.
- **WhatsApp** — fully blocked at the ISP level; desync doesn't help.

### Installing Zapret 2 from scratch

1. Download the GUI build from [github.com/youtubediscord/zapret](https://github.com/youtubediscord/zapret) — releases section, or `ZapretSetup.exe` linked from the repo's README.
2. Run the installer — WinDivert is bundled and installed automatically.
3. After install, Zapret appears in the Start menu.
4. Run the GUI **as Administrator** (required — WinDivert operates at the driver level).

### Installing a preset

1. Download the desired `.txt` file from this repo.
2. Place it in the `presets` folder inside your Zapret 2 installation directory.
3. Open the preset list in the GUI and select `Universal V2.1` (or `V2.1 voice ALT`).
4. Click Start.
5. Test using the built-in BlockCheck or manually (open YouTube, Discord, etc.).

### Which preset to use

- **Default:** `Universal_V2_1.txt`.
- **If Discord text works but voice calls don't (no audio/video in voice channels):** switch to `Universal_V2_1_voice_ALT.txt`.

### Zapret2 + Happ VPN

I run Zapret 2 alongside Happ VPN — the VPN is enabled only for selected apps, not globally, so Zapret keeps handling the rest of the traffic directly.

### Rule structure (brief)

Each `--new` block is a separate rule for a specific domain/list/protocol. Main strategies used:
- `multidisorder` — for TCP/TLS ClientHello (YouTube, social media, AI services, torrents)
- `send + syndata` — for Discord (text/media)
- `fake` (quic/stun blobs) — for UDP/QUIC/voice

### Disclaimer

These presets are provided "as is" for educational purposes and personal internet use. The author is not responsible for any use that violates the laws of your jurisdiction.
