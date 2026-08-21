# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

---

## Проект

Личный лендинг Алины Шведовой — сертифицированного терапевта метода «Вселенская терапия». Одностраничный сайт для привлечения клиентов и онлайн-записи на сессии.

**Живой сайт:** https://alinavselenka.vercel.app

---

## Архитектура

Весь сайт — один файл `index.html`: CSS, HTML и JavaScript находятся внутри него, никаких фреймворков и сборщиков нет.

**Структура `index.html`:**
1. `<head>` — шрифты Google Fonts (Raleway, Montserrat, Josefin Sans), весь CSS в `<style>`
2. `<body>` — секции лендинга в порядке: nav → hero → trust-strip → about → method → audience → booking (Cal.com) → reviews → footer
3. В конце `<body>` — скрипт Cal.com и inline JS (burger-меню, scroll-reveal)

---

## Деплой

```bash
vercel --prod
```

Деплой напрямую через Vercel CLI из корня репозитория. GitHub-пуш тоже триггерит авто-деплой (репо подключено к Vercel).

---

## Дизайн-система

**CSS-переменные** (объявлены в `:root`):
| Переменная | HEX | Применение |
|---|---|---|
| `--terra` | `#C4714A` | Акценты, eyebrow, CTA |
| `--olive` | `#3D4A36` | Nav, footer, тёмные секции |
| `--sandy` | `#C8BBA8` | Вторичный текст, разделители |
| `--ofwhite` | `#F2F0EB` | Фон светлых секций |
| `--dark` | `#2C2825` | Основной тёмный цвет |
| `--ink-soft` | `#78756F` | Вторичный текст |

**Шрифты:**
- Заголовки: `Raleway` (font-weight 300/400, italic для акцентов)
- Основной текст: `Montserrat` (font-weight 300/400/500)
- Логотип/футер: `Josefin Sans`

**Логотип** — SVG-спираль Фибоначчи, генерируется инлайн в коде, используется в nav и footer.

**Чередование фонов секций:**
```
nav/footer  → --olive  (#3D4A36)
hero        → --dark   (#2C2825)
about       → --ofwhite
method      → --olive
audience    → --sandy
booking     → --ofwhite
reviews     → --dark
```

---

## Брендовый язык

**Использовать:** первопричина, подсознательные паттерны, ограничивающие убеждения, трансформация, глубинные программы.

**Избегать:** энергетические блоки, вибрации, вселенная, исцеление, квантовая физика как обоснование.

Тон: глубокий, философский, язык результата — без эзотерики.

---

## Интеграции

- **Cal.com** — встроен в секцию `.booking` через `#cal-inline`. Скрипт подключается внизу `<body>`.
- **Google Calendar** — интеграция через Cal.com (показывает занятость без деталей клиентов).
- **Telegram** — ссылка в footer и CTA-кнопках.

---

## Мобильная адаптация

Основные брейкпоинты:
- `820px` — hero меняет раскладку (фото сверху, текст снизу), уменьшаются отступы секций
- `860px` — about, audience, reviews переходят в одну колонку
- `780px` — nav скрывает ссылки, показывает burger-меню

---

## Контент-файлы

- `PROJECT.md` — полное PRD, статус всех модулей, журнал решений
- `alina_shvedova_brand.md` — бренд-досье: ЦА, позиционирование, тон голоса, логотип
- `feedback/reviews_published.md` — реальные отзывы клиентов, размещённые на лендинге
- `feedback/reviews_raw.md` — исходники отзывов до редактуры

---

## Статус MVP (лендинг)

Лендинг полностью готов. Все секции заполнены реальным контентом, Cal.com подключён.

Следующий этап — бэк-офис (M3–M8 из `specs/PROJECT.md`): CRM и кабинет клиента в Notion, автоматизация и напоминания через Make.com, уведомления и сбор фидбэка через Telegram Bot. План выполнения: `docs/superpowers/plans/2026-06-24-backoffice-setup.md`, дизайн: `docs/superpowers/specs/2026-06-24-backoffice-design.md`, структура баз: `specs/NOTION_STRUCTURE.md`.
