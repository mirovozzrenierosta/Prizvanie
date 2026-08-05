# Архив сессии — Мировоззрение Роста

**Дата:** 2026-08-05
**Сессия:** bdf40010-0afd-5d24-80ae-19371bc09cba

---

## Что было сделано

### 1. platform_landing2.html — редизайн лендинга по принципам Репьева

Создан `/home/user/Prizvanie/platform_landing2.html` — копия `platform_landing.html`, переработанная по 7 маркетинговым принципам Репьева:
- Светлый фон (cream/white) вместо тёмного, ТЫ-маркетинг, структура от боли
- Секции: NAV → HERO → PROOF BAR → PAIN (4 карточки) → BENEFITS (5 «вы будете знать») → HOW (3 шага) → ABOUT (фото + факты) → SYSTEM (5 матриц + 7 модулей) → CASES (3) → TIMELINE → B2B → CTA → FOOTER
- Встроенное фото Александра (base64, JPEG 275KB)
- Все CTA ведут на `https://mrost-platform-production.up.railway.app/join.html` с параметрами `?src=landing2`, `?src=landing2-b2b`, `?src=landing2-cta`

### 2. Удалено поле телефона из формы регистрации

**`/workspace/mrost-platform/public/join.html`** — убран блок `<div class="fld">` с полем телефона и строка `phone: ...` из JS fetch.

**`/workspace/mrost-platform/src/app/api/join/route.ts`** — убраны: деструктуризация `phone`, переменная `phoneNorm`, валидация телефона, вызов `updateContact`, импорт `updateContact`.

### 3. Лендинг для репозитория Александр

Создан `/workspace/aleksandr/index.html` — премиальная страница личного бренда:
- Все данные встроены (CSS + JS + base64 фото ×2)
- Секции: NAV, HERO с фото и бейджем, PROOF BAR, PAIN (4), BENEFITS (5), ABOUT, MATRICES (5 матриц + 7 модулей), CASES (3), HOW (3 шага), B2B (4 карточки), CTA, FOOTER
- Кнопки: `?src=aleksandr`, `?src=aleksandr-hero` и т.д.
- SEO meta + OG теги
- Сохранён как `index2.html` отдельно

### 4. Все лендинги проекта

| Файл | URL | Описание |
|------|-----|----------|
| `platform_landing.html` | github.io/Prizvanie/platform_landing.html | Оригинал (тёмный фон) |
| `platform_landing2.html` | github.io/Prizvanie/platform_landing2.html | Редизайн по Репьеву (светлый) |
| `index.html` (Aleksandr repo) | github.io/Aleksandr/ | Премиальный личный бренд |
| `index2.html` (Aleksandr repo) | github.io/Aleksandr/index2.html | Копия premium лендинга |

### 5. Структура A/B теста для Яндекс Директ

Два URL → две группы объявлений → одна цель конверсии в Метрике.
- Группа A → `platform_landing.html` (тёмный), `?src=landing-a`
- Группа B → `platform_landing2.html` (светлый), `?src=landing-b`
- Метрика: цель на `join.html`, разбивка по параметру `src`
- Обе страницы ведут на `mrost-platform-production.up.railway.app/join.html`

### 6. Content-завод: HR-пак (24 единицы контента)

**Тема:** Подбор сотрудников по психологическому портрету, анализ рабочих коллективов.

**Источники:**
- «База знаний: Ценность психологических портретов» (9 разделов)
- Реальный кейс «Мария Богачева / Сергей, IT-сфера» — 5-матричный разбор пары

**Ключевые данные кейса:**
- Сергей: Параноидный 83%, Жёлтый 88%, Дигитал 67%, Властник 83%, Директор/Советник 83%/83%
- Мария: Гипертимный 100%, Жёлтый 75%, Кинестетика 67%, Причастник 67%, Директор/Бизнесмен 67%
- Точки опоры: оба Жёлтый, оба слабый Аудиал (33%), оба лидерского архетипа
- Точки трения: энергетический разрыв 67 пунктов, Властник vs Причастник, логика vs практика, Эпилептоид 67% vs 33%

**Файлы (скачаны, в репо не хранятся):**

| Файл | Содержание |
|------|-----------|
| `Статья_HR-портрет.md` | SEO-статья ~2000 слов: 5 матриц + кейс + управленческие выводы |
| `Тредсы_HR-портрет.md` | 10 тредсов (все углы: инсайт, цифра, ошибка, лайфхак, кейс, до→после, ценность, миф, чек-лист, провокация) |
| `Рилсы_HR-портрет.md` | 5 сценариев Reels с режиссёрскими пометками, хронометражом, хэштегами |
| `Посты_HR-портрет.md` | 5 постов: анонс, инсайт, кейс, ценностная мысль, вовлечение |
| `Карусели_HR-портрет.md` | 3 карусели: гайд «5 матриц», «было→стало», «7 признаков выгорания» |
| `Контент-план_HR-портрет.md` | Очередь публикаций на 14+ дней, таблица по платформам, 28 хуков |

---

## Технические детали

**Репозитории:**
- `mirovozzrenierosta/Prizvanie` → GitHub Pages: `mirovozzrenierosta.github.io/Prizvanie/`
- `mirovozzrenierosta/Aleksandr` → GitHub Pages: `mirovozzrenierosta.github.io/Aleksandr/`
- `mrost-platform` → Railway: `mrost-platform-production.up.railway.app`

**Платформа mrost:**
- Next.js + TypeScript
- Supabase (users, contacts, consents)
- `/api/join` — публичная регистрация по реф-ссылке
- `/api/cabinet` — личный кабинет по токену

**Бренд-система:**
- `--navy:#1C2B5E`, `--gold:#C9A227`, `--gold-bg:#FDF8EC`, `--cream:#FDFCF9`
- Georgia serif заголовки, PT Sans body

**Tracking параметры:**
- `?src=landing` / `?src=landing2` / `?src=aleksandr` / `?src=landing2-b2b` и т.д.
- Передаются в `users.source` в БД через `/api/join`

---

## Важное замечание по безопасности

PAT токен `github_pat_11CFYNSTY0c...` был случайно засвечен в предыдущей сессии. Необходимо отозвать на `https://github.com/settings/tokens`.
