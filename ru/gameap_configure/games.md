---
title: Игры
layout: default
lang: ru
category: Настройка панели
order: 30
---

* This will become a table of contents (this text will be scraped).
{:toc}

## Добавление новых игр

Панель управления поддерживает запуск и базовое управление любыми игровыми серверами и приложениями. Если
в панели нет нужной вам игры, то вы можете её добавить.

Для добавления новой игры необходимо перейти на страницу **"Администрирование"** -> **"Игры"**, затем выбрать 
**"Добавить игру"**.

После добавление игры добавьте первую модификацию этой игры и укажите параметры запуска игрового сервера.

### Описание полей 

#### Код

Код игры — это уникальное значение. Обычно это представляет собой сокращение от названия игры, например для игры 
"7 Day To Die" это `7d2d`. Код должен быть уникальным. Его можно придумать самому, главное, чтобы он был уникальным.

#### Старт код

Старт код обычно указывается в параметрах запуска. Это значение может быть любым, но чаще всего оно совпадает с кодом 
игры. Может совпадать с другими играми.

#### Имя игры

В имени игры нет ничего особенного — это полное название игры.

#### Движок игры

Движок игры — это система, на котором написана игра. Игры Half-Life, Counter-Strike написаны на движке GoldSource.

Half-Life 2, Counter-Strike Source написаны на Source. Иногда бывает, что неизвестно на каком движке написана игра,
в этом случае можно указать код игры или какое-либо сокращение от игры.

Для игр, написанных на GoldSource и Source следует указывать точно название движка. Для игр на Unity лучше указывать
какое-либо сокращение от игры, например Rust написана на Unity, но название движка указано как `rust`.
Игра Minecraft не написана с использованием какого-либо движка, поэтому название движка также указано как "Minecraft".

#### Версия движка

Числовая или строковое значение версии движка. Можно указать какое-либо смысловое значение, например "legacy", "beta"
и т.п.

#### Steam App ID

ID сервера игры в Steam. Используется для установки сервера через SteamCMD.
SteamID можно узнать на [официальной вики Steam](https://developer.valvesoftware.com/wiki/Dedicated_Servers_List), либо
в базе данных [SteamDB](https://steamdb.info/)

#### Steam App Set Config

Дополнительные параметры для установки сервера через SteamCMD. Некоторые значения можно узнать на можно узнать на 
[официальной вики Steam](https://developer.valvesoftware.com/wiki/Dedicated_Servers_List)

#### Локальный репозиторий

Путь на выделенном сервере к архиву либо к каталогу со сборкой игры, используемой как шаблон.
Этот путь должен обязательно присутствовать на выделенном сервере на который происходит установка нового игрового 
сервера. При создании нового игрового сервера архив будет распакован в рабочий каталог игрового сервера.

Поддерживаются следующие архивы: Zip, 7z, Tar, XZ, Bzip, GZip. 

RAR архивы не поддерживаются.

##### Примеры

В качестве примера рабочий каталог игрового сервера `/srv/gameap/servers/example-server`

| Значение поля "Локальный репозиторий" | Корректность значения | Результат при установке
| ------ | ------- | ------ |
| `/srv/gameap/repo/cs16_gungame.zip` | Корректно, при наличии архива на выделенном сервере | Содержимое архива `cs16_gungame.zip` будет распаковано в каталог `/srv/gameap/servers/example-server`
| `/srv/gameap/repo/cs16_public` | Корректно, при наличии каталога на выделенном сервере | Содержимое каталога будет скопировано в `/srv/gameap/servers/example-server`
| `/srv/gameap/repo/cs16_gungame.rar` | Некорректно. Архивы RAR не поддерживаются | Способ установки из локального репозитория будет пропущен либо сервер не будет установлен
| `http://files.gameap.ru/cstrike-1.6/rehlds-amxx-reunion.tar.xz` | Некорректно. Указано значение для удалённого репозитория | Способ установки из локального репозитория будет пропущен либо сервер не будет установлен


#### Удалённый репозиторий

Ссылка на удалённый источник. Это должен быть URL на HTTP или FTP ресурс. Архив должен быть доступен по прямой ссылке
без всяких промежуточных страниц, требующих ожидания или дополнительных действий. Ссылки к Yandex Disk, Google Drive и 
т.п. не поддерживаются.

Некоторые сборки вы можете найти на [официальном хранилище GameAP](http://files.gameap.ru/).

##### Примеры

В качестве примера рабочий каталог игрового сервера `/srv/gameap/servers/example-server`

| Значение поля "Локальный репозиторий" | Корректность значения | Результат при установке
| `http://files.gameap.ru/cstrike-1.6/rehlds-amxx-reunion.tar.xz` | Корректно | Будет загружен архив `rehlds-amxx-reunion.tar.xz` и распакован в каталог `/srv/gameap/servers/example-server`
| `/srv/gameap/repo/cs16_gungame.zip` | Некорректно | Способ установки будет пропущен либо игровой сервер не будет установлен.

## Добавление новых модификаций

У каждой игры может быть множество модификаций, каждая из которых обладает своими особенностями — настройками, 
параметрами запуска, конфигурационными файлами и т.п.

Для добавления новой игры необходимо перейти на страницу **"Администрирование"** -> **"Игры"**, затем выбрать 
**"Добавить модификацию"**

### Описание полей

#### Игра

Игра к которой принадлежит модификация.

#### Имя

Имя модификации. Это может быть название аддона, сборки, ядра, какой-либо особенности и т.п. Укажите имя полностью на
своё усмотрение.

#### Репозитории

У модификации можеть быть свой собственный набор файлов и настроек, которые записываются поверх файлов основной сборки.
В архив с файлами вы можете включить какие-либо дополнительные плагины, дополнительные контент, звуки, музыку и т.д.
Поля локальный репозиторий не являются обязательными.

Поддерживаются следующие архивы: Zip, 7z, Tar, XZ, Bzip, GZip. 

RAR архивы не поддерживаются.

##### Локальный репозиторий

Путь на выделенном сервере к архиву либо к каталогу с файлами модификации игры, используемой как шаблон.
Этот путь должен обязательно присутствовать на выделенном сервере на который происходит установка нового игрового 
сервера. При установке игрового сервера архив будет распакован поверх основной сборки в рабочий каталог игрового 
сервера.

Поддерживаются следующие архивы: Zip, 7z, Tar, XZ, Bzip, GZip. 

RAR архивы не поддерживаются

###### Примеры

В качестве примера рабочий каталог игрового сервера `/srv/gameap/servers/example-server`

| Значение поля "Локальный репозиторий" | Корректность значения | Результат при установке
| ------ | ------- | ------ |
| `/srv/gameap/repo/cs16_gungame.zip` | Корректно, при наличии архива на выделенном сервере | Содержимое архива `cs16_gungame.zip` будет распаковано в каталог `/srv/gameap/servers/example-server`
| `/srv/gameap/repo/cs16_gungame` | Корректно, при наличии каталога на выделенном сервере | Содержимое каталога будет скопировано в `/srv/gameap/servers/example-server`
| `/srv/gameap/repo/cs16_gungame.rar` | Некорректно. Архивы RAR не поддерживаются | Распаковка архива будет пропущена
| `http://files.gameap.ru/cstrike-1.6/rehlds-amxx-reunion.tar.xz` | Некорректно. Указано значение для удалённого репозитория | Установка модификации будет пропущена


##### Удалённый репозиторий

Ссылка на удалённый источник. Это должен быть URL на HTTP или FTP ресурс. Архив должен быть доступен по прямой ссылке
без всяких промежуточных страниц, требующих ожидания или дополнительных действий. Ссылки к Yandex Disk, Google Drive и 
т.п. не поддерживаются.

Некоторые сборки вы можете найти на [официальном хранилище GameAP](http://files.gameap.ru/).

###### Примеры

В качестве примера рабочий каталог игрового сервера `/srv/gameap/servers/example-server`

| Значение поля "Локальный репозиторий" | Корректность значения | Результат при установке
| `http://files.gameap.ru/cstrike-1.6/rehlds-amxx-reunion.tar.xz` | Корректно | Будет загружен архив `rehlds-amxx-reunion.tar.xz` и распакован в каталог `/srv/gameap/servers/example-server`
| `/srv/gameap/repo/cs16_gungame.zip` | Некорректно | Установка модификации будет пропущена

## Редактирование модификаций

После создания модификации её можно дополнительно настроить, указав дополнительные параметры, такие как 
"Команды запуска по умолчанию", переменные запуска, различные RCON команды.

### Основные настройки

В основные настройки входят такие параметры, как имя модификации, репозитории и команды запуска по умолчанию. Особое
внимание следует уделить командам запуска.

#### Имя модификации

#### Репозитории

Подробнее читайте в разделе [Добавление новых модификаций, репозитории](#репозитории)

#### Команды запуска по умолчанию

При создании нового игрового сервера для выбранного мода, ему по автоматически будет присвоена эта команда. Если
команда пуста, то ничего присвоено не будет и для каждого игрового сервера нужно указывать команду запуска вручную.
Без команды запуска игровой сервер запустить невозможно.

В командах запуска можно использовать шорткоды, они затем будут заменены на значения переменных сервера. Шорткоды
представляют из себя слова без пробелов в фигурных скобках `{`, `}`, например `{ip}`, `{port}`, `{maxplayers}` и др.

##### Базовые шорткоды

Эти шорткоды всегда доступны, для них не требуется добавлять дополнительные переменные в настройках модификации.

| Шорткод | Описание
| ------ | -------
| {ip} | IP игрового сервера
| {port} | Основной порт игрового сервера. Иногда называется connect-портом
| {query_port} | Порт для запросов (Query порт)
| {rcon_port} | Порт для коммуникации с сервером (RCON порт)
| {rcon_password} | RCON пароль
| {uuid} | UUID сервера
| {uuid_short} | Короткий UUID сервера

##### Определяемые пользователем шорткоды

Эти шорткоды вы можете определить для каждой определённой модификации игры самостоятельно. В зависимости от 
индивидуальных настроек сервера, эти шорткоды будут заменены на значения параметров игрового сервера. Более подробно 
читайте раздел [Переменные](#переменные).

### Переменные

Позволяют добавить индивидуальные настройки для каждого игрового сервера. Эти настройки затем могут быть отредактированы
администратором либо обычным пользователем на странице настроек (**"Список серверов"** -> **"Управление"** -> 
**"Настройки"**).

| Поле | Описание
| ------ | -------
| Переменная | Имя переменной. Указывается без фигурных скобок.
| По умолчанию | Значение переменной по умолчанию. Если для игрового сервера не будет задано индивидуальное значение, то будет использоваться это значение.
| Описание | Используется для описания на странице настройки игрового сервера (**"Список серверов"** -> **"Управление"** -> **"Настройки"**)
| Переменная администратора | Если поставлена галочка, то только администратор сможет редактировать значение этой настройки для игровых серверов.

#### Примеры

| Значения | Описание
| ------ | -------
| **Переменная:** default_map <br><br>**По умолчанию:** de_dust <br><br>**Описание:** Карта при запуске| Для каждого игрового сервера этой модификации появится шорткод `{default_map}` и новый параметр в настройках под названием "Карта по умолчанию" со значением по умолчанию "de_dust". <br><br>Индивидуально для каждого сервера этот параметр можно отредактировать перейдя на страницу **"Список серверов"** -> **"Управление"** -> **"Настройки"**


### Команды RCON

Эти команды позволяют более расширенно управлять игровым сервером. Если игра поддерживает работу с RCON, либо 
поддерживается консоль, то можно делать следующее: кикать игроков с сервера, банить игроков, менять карту на сервере,
отправлять текстовые в общий чат, устанавливать пароль.

Некоторый функционал может быть ограничен самой игрой или модификацией. Например, не все игровые серверы поддерживают
вход на сервер по паролю.

#### Команда кика

Позволяет установить команду RCON, которая будет использоваться для выкидывания игрока с сервера.

Для команды можно задать шорткоды, которые будут заменены на данные определённого игрока

| Шорткод | Описание
| ------ | -------
| {id} | ID игрока на сервере
| {name} | Имя игрока на сервере

Для многих игр на GoldSource/Source это команда: 
```
kick #{id}
```

#### Команда бана

Позволяет установить команду, которая будет использоваться для временного или перманентного бана игрока на сервере.

Для команды можно задать шорткоды, которые будут заменены на данные определённого игрока

| Шорткод | Описание
| ------ | -------
| {id} | ID игрока на сервере
| {name} | Имя игрока на сервере
| {time} | Время бана
| {reason} | Причина бана

Для многих игр на GoldSource (Half-Life, Counter-Strike 1.6 и др.) под управлением AMX Mod X это команда: 
```
amx_ban "{name}" {time} "{reason}"
```

#### Команда смены имени (ника)

Команда, которой будет меняться ник выбранного игрока.

Для команды можно задать шорткоды, которые будут заменены на данные определённого игрока

| Шорткод | Описание
| ------ | -------
| {id} | ID игрока на сервере
| {name} | Текущее имя игрока на сервере
| {new_name} | Новое имя игрока на сервере
| {reason} | Причина смены

Для многих игр на GoldSource (Half-Life, Counter-Strike 1.6 и др.) под управлением AMX Mod X это команда: 
```
amx_nick #{id} {new_name}
```

#### Команда перезапуска

Позволяет установить команду мягкой перезагрузки сервера, без перезагрузки самого процесса игрового сервера. Обычно
этой командой перезапускается карта или раунд для какой-нибудь игры. Не поддерживается многими играми.

Для многих игр на GoldSource/Source это команда: 
```
restart
```

#### Команда смены карты

Этой командой можно сменить карту на игровом сервере.

| Шорткод | Описание
| ------ | -------
| {map} | Имя карты

Для многих игр на GoldSource/Source это команда: 
```
changelevel {map}
```

#### Команда отправки сообщения

Позволяет отправить сообщение в текстовый чат для всех игроков на сервере.

| Шорткод | Описание
| ------ | -------
| {msg} | Сообщение, которое будет отправлено на сервер

Для многих игр на GoldSource (Half-Life, Counter-Strike 1.6 и др.) под управлением AMX Mod X это команда: 
```
amx_say "{msg}"
```

#### Команда установки/смены пароля

Позволяет установить пароль для игрового сервера, благодаря чему на сервер смогут зайти только игроки, которые знают
этот пароль.

| Шорткод | Описание
| ------ | -------
| {password} | Пароль, который будет установлен на сервере

Для многих игр на GoldSource/Source это команда: 
```
password {password}
```

### Команды FastRCON

Вы можете определить свои дополнительные команды RCON. Например команда статуса сервера, получение статистики, получения
списка недавно отключившихся игроков и др.