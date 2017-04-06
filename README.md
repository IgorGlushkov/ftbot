## FTBot - Flickr to telegram bot to post racoons regularly

- Поиск фотографий на Flickr и отправка в Telegram чат/канал
- Хранение списка фотографий в sqlite базе, с разметкой уже отправленных, чтобы исключить повторы

## Принцип работы

Скрипт ведет учет отправленных и новых фотографий в sqlite базе. 
При запуске проверяется, существуют ли в базе не отправленные фотографии. 
Если все отправлено, скрипт пробует запросить на Flickr новые фото, если новых нет, то считаем сколько у нас в базе элементов и повторяем поиск со смещением, до тех пор, пока не будут найдены новые фотографии для отправки

## Установка

1. Склонируйте репозиторий:
```sh
git clone https://github.com/ivbeg/ftbot.git ./ftbot
```

2. Установите зависимости:
```sh
cd ./ftbot
pip3 install -r requirements
```

3. Запустите установочный файл, для создания sqlite базы данных
```sh
python3 ./database.py
```

## Настройка

Настройки хранятся в файле settings.py
Перед первым запуском нужно настроить следующие параметры:

- TELEGRAM_CHAT_ID - ID или имя чата/канала Telegram, в который будут отправлятся фотографии
- TELEGRAM_BOT_TOKEN - Токен телеграм бота, для доступа к API
- FLICKR_API_KEY Ключ - API Flickr 
- FLICKR_API_SECRET - Секретная фраза API Flickr
- FLICKR_SEARCH_LICENSE_ID - ID Лицензии, для фильтрации поиска
- FLICKR_SEARCH_TAGS - Тэги поиска

## Запуск
```sh
python3 bot.py
```
