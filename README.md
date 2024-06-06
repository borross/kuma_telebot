# Общее описание
Скрипт реагирования достает из алерта KUMA нужные поля и отправляет на локальный порт содержимое сообщения с форматированием (передача данных нужна для сохранения форматирования). Бот полученое сообщение отправляет в чат с пользователем, также возможна настройка, чтобы бот отправлял сообщение в определенный канал (но этот функционал не реализован). Бот позволяет закрывать алерты по кнопке, создавать резервную копию и выполнять команды ssh на KUMA.

# Шаги для настройки
1. Разместите файлы kuma_telebot.conf, kuma_telebot.py, send_alert_to_bot.sh по пути */opt/kaspersky/kuma/correlator/<ID_CORRELATOR>/scripts/*
2. Заполните файл конфигурации kuma_telebot.conf
3. Создайте правило реагирования которое запускает скрипт send_alert_to_bot.sh со следующим аргументом: *"{{.Timestamp}} | {{.Name}} | {{.DeviceHostName}} | {{.Message}} | {{.Tactic}} | {{.Technique}}"*
4. Создайте службу запуска скрипта для бота сморти содержимое файла bot-kuma.service, его нужно создать по пути */usr/lib/systemd/system/*
5. systemctl enable bot-kuma.service; systemctl start bot-kuma.service

# Скриншоты работы скрипта
![image](https://github.com/borross/kuma_telebot/assets/39199196/379a4b1d-44b5-443a-9117-f82d81a8b174)

![image](https://github.com/borross/kuma_telebot/assets/39199196/c1fbdc5c-2828-45cf-ac90-5fa5be1a99d0)

![image](https://github.com/borross/kuma_telebot/assets/39199196/c6d23989-c6d6-4e54-b98b-6107fd713c38)

![image](https://github.com/borross/kuma_telebot/assets/39199196/2ae40c6d-6278-4ada-8600-afe5433baa08)

# Версия 2
Добавлен фунционал выгрузки отчетов из KUMA с помощью бота, добавлена новая кнопка по нажатию которой выгружается список сгенерированных отчетов, по нажатию в боте на строку с командой */report_<цифра>* загружается конкретный отчет.

Скриншот с нововведениями:

![image](https://github.com/borross/kuma_telebot/assets/39199196/b7fcb51e-e029-4b8d-a00b-00004c650a38)
