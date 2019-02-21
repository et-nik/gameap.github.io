---
title: Настройка панели
layout: default
lang: ru
category: Общее
order: 35
---

* This will become a table of contents (this text will be scraped).
{:toc}

## Новый выделенный сервер

Для самого начала необходимо добавить выделенный сервер (VDS, контейнер, физический сервер), на котором работает GameAP Daemon.

Установить GameAP Daemon на выделенный сервер можно автоматически, выполнив скрипт, а можно [вручную](/ru/gameap_daemon.html). При установке вручную нужно также сгенерировать сертификаты SSL и подписать их, а также отредактировать файл конфигурации `/etc/gameap-daemon/gameap-daemon.cfg`.

### Автоматическая установка GameAP Daemon на выделенный сервер

Перейдите на страницу "Администрирование" -> "Выделенные серверы", кликните по кнопке "Создать".
На странице создания появится окошко с предложением автоматически установить GameAP Daemon на выделенный сервер. Скопируйте команду для автоматической установке и выполните её на выделенном сервере от пользователя с правами root. Команда выглядит примерно так:
```
curl http://your-panel/gdaemon/setup/zItWHWlI4RKPl9ZsYc3y3Wgd | bash --
```
Данная команда будет доступна для выполнения в течение 5 минут, по истечению времени она работать не будет. Необходимо вновь открыть страницу создания выделенного сервера, где появится новая команда для автоматической установки.