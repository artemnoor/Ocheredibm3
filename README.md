# Ocheredibm3 Queue Bot

Telegram-бот очередей на **aiogram 3 + FastAPI webhook**, готовый для деплоя на **Vercel** и работы с **Supabase**.

## Что уже настроено

Supabase-проект уже подготовлен. Используется проект:

```text
https://rmxmrxqcayfkyhromvvl.supabase.co
```

В базе созданы таблицы:

- `queue_bot_users`
- `queue_bot_user_states`
- `queue_bot_events`
- `queue_bot_entries`

И RPC-функции:

- `register_user`
- `get_user_by_telegram_id`
- `set_user_state`
- `get_user_state`
- `clear_user_state`
- `create_event`
- `close_event`
- `list_active_events`
- `join_queue`
- `leave_queue`
- `my_queue`
- `event_queue`
- `call_next`

## Как работает бот

- `/start` — регистрация пользователя.
- При первом запуске бот просит ФИО.
- Для каждого мероприятия создаётся отдельная очередь.
- Пользователь может встать в очередь, выйти из очереди и посмотреть своё место.
- Админ может создать мероприятие и вызвать следующего участника.

## Переменные окружения для Vercel

В Vercel нужно добавить:

```env
BOT_TOKEN=your-telegram-token
WEBHOOK_SECRET=your-random-secret
PUBLIC_BASE_URL=https://your-vercel-domain.vercel.app
SUPABASE_URL=https://rmxmrxqcayfkyhromvvl.supabase.co
SUPABASE_SERVICE_ROLE_KEY=your-supabase-service-role-key
ADMIN_IDS=your_telegram_numeric_id
APP_NAME=Ocheredibm3 Queue Bot
```

Важно: реальные токены и service role key нельзя коммитить в GitHub.

## Деплой на Vercel с телефона

1. Открой Vercel.
2. `Add New` → `Project`.
3. Импортируй этот GitHub-репозиторий.
4. Добавь переменные окружения.
5. Нажми `Deploy`.
6. После деплоя скопируй домен Vercel.
7. Открой URL установки webhook:

```text
https://<your-domain>.vercel.app/api/set-webhook?secret=<WEBHOOK_SECRET>
```

Если всё хорошо, Telegram webhook будет установлен.

## Команды

### Пользователь

```text
/start
/events
/my_queue
```

### Админ

```text
/new_event Название мероприятия | Описание
/event_ids
```

Описание можно не указывать:

```text
/new_event Защита проектов
```
