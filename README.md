# Общее описание
Скрипт реагирования достает из алерта KUMA нужные поля и отпраляет на локальный порт содержимое сообщения с форматированием (такой формат нужен чтоб форматирование сохранялось). Бот полученое сообщение отправляет в чат с пользователем, также возможна настройка чтобы бот отправлял сообщение в определенный канал (но этот функционал не реализован).

# Шаги для настройки
1. Разместите файлы kuma_telebot.conf, kuma_telebot.py, send_alert_to_bot.sh по пути */opt/kaspersky/kuma/correlator/<ID_CORRELATOR>/scripts/*
2. Заполните файл конфигурации kuma_telebot.conf
3. Создайте правило реагирования которое запускает скрипт send_alert_to_bot.sh со следующим аргументом: *"{{.Timestamp}} | {{.Name}} | {{.DeviceHostName}} | {{.Message}} | {{.Tactic}} | {{.Technique}}"*
4. Создайте службу запуска скрипта для бота сморти содержимое файла bot-kuma.service, его нужно создать по пути */usr/lib/systemd/system/*
5. systemctl enable bot-kuma.service; systemctl start bot-kuma.service

# Скриншоты работы скрипта
![image](https://github.com/borross/kuma_telebot/assets/39199196/ae825c8c-e258-4a5d-aec2-7df42c19d830)

![image](https://github.com/borross/kuma_telebot/assets/39199196/2f577fdf-1b37-4050-9ec6-1d10a032cb00)

![image](https://github.com/borross/kuma_telebot/assets/39199196/f649ed9c-abe1-4c46-a233-48e7bc37f4d9)

![image](https://github.com/borross/kuma_telebot/assets/39199196/5192f128-441a-443d-b7fa-74ae17a1e730)
