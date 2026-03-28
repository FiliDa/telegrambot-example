# 🤖 TelegramBotMessanger (.NET 8)

[![.NET](https://img.shields.io/badge/.NET-8.0-512BD4?style=flat&logo=dotnet&logoColor=white)](https://dotnet.microsoft.com/)
[![Telegram Bot API](https://img.shields.io/badge/Telegram%20Bot%20API-2CA5E0?style=flat&logo=telegram&logoColor=white)](https://core.telegram.org/bots/api)
[![Newtonsoft.Json](https://img.shields.io/badge/Newtonsoft.Json-13.0.3-gray)](https://www.newtonsoft.com/json)

Консольный пример Telegram‑бота на C#/.NET 8. Показывает отправку сообщений и фотографий через HTTP (без сторонних SDK) и прием апдейтов методом long‑polling.

## Возможности

- Отправка сообщений с MarkdownV2 форматированием
- Отправка фотографий с подписью
- Прием апдейтов через `getUpdates` в цикле
- Чистая разделенная логика: HTTP‑обертка в сервисе, точка входа — отдельно

## Стек

- .NET 8 (Console App)
- Newtonsoft.Json для сериализации
- Telegram Bot API (HTTP)

## Структура проекта

```
telegrambot-example/
└── TelegramBotMessanger/
    ├── BotService.cs        # Логика отправки сообщений/фото и получения апдейтов
    ├── Program.cs           # Точка входа, чтение токена/чата из окружения
    ├── cat.jpg              # Тестовое изображение
    └── TelegramBotMessanger.csproj
```

Ключевые файлы:

- [BotService.cs](file:///e:/GITR — копия/telegrambot-example/TelegramBotMessanger/BotService.cs) — методы `SendMessageAsync`, `SendPhotoAsync`, `StartReceivingMessagesAsync`
- [Program.cs](file:///e:/GITR — копия/telegrambot-example/TelegramBotMessanger/Program.cs) — настройка и запуск

## Быстрый старт

1) Установите .NET 8 SDK
2) Задайте переменные окружения с токеном и целевым чатом

Windows PowerShell:

```powershell
$env:TELEGRAM_BOT_TOKEN="ваш_бот_токен"
$env:TELEGRAM_CHAT_ID="ваш_chat_id_или_channel_id"
```

Linux/macOS (bash/zsh):

```bash
export TELEGRAM_BOT_TOKEN="ваш_бот_токен"
export TELEGRAM_CHAT_ID="ваш_chat_id_или_channel_id"
```

3) Запуск:

```bash
dotnet run --project TelegramBotMessanger
```

## Отправка сообщения/фото

В файле [Program.cs](file:///e:/GITR — копия/telegrambot-example/TelegramBotMessanger/Program.cs) раскомментируйте нужные строки:

```csharp
//await botService.SendMessageAsync(chatId, message);
//await botService.SendPhotoAsync(chatId, photoPath, caption);
```

`photoPath` по умолчанию указывает на `cat.jpg`, который копируется в выходную директорию.

## Переменные окружения

- `TELEGRAM_BOT_TOKEN` — токен вашего бота
- `TELEGRAM_CHAT_ID` — ID чата/канала для отправки сообщений

Данные не хранятся в коде — только в окружении.

## Безопасность

- Никогда не коммитьте токен в репозиторий
- Используйте секреты в CI/CD и переменные окружения локально

## Полезно знать

- Форматирование текста — режим MarkdownV2 (экранируйте спецсимволы)
- Для продакшена используйте вебхуки или промежуточный планировщик

## Автор

Filippov D.A. — Backend Engineer
Email: phoenixmediacall@gmail.com
GitHub: https://github.com/FiliDa

---

Если проект полезен — поставьте ⭐ и предлагайте улучшения через Issues.
