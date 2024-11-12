# DPI Penguin [YouTube + Discord]

<img src="https://github.com/zhivem/DPI-Penguin/blob/main/resources/icon/newicon.ico" width=10% height=10%>

[![en](https://img.shields.io/badge/lang-en-red.svg)](./README.EN.md)
[![ru](https://img.shields.io/badge/lang-ru-green.svg)](./README.md)

**DPI Penguin** — это графическое приложение на Python, разработанное для обхода сетевых ограничений, таких как глубокий анализ пакетов (DPI). Приложение предоставляет интуитивно понятный интерфейс для управления скриптами, позволяющими получать доступ к платформам таким как YouTube и Discord. Работа приложения основана на интеграции с [Zapret](https://github.com/bol-van/zapret). Загрузить `exe` можно c [Releases](https://github.com/zhivem/DPI-Penguin/releases)

![image](https://github.com/user-attachments/assets/e3bc3377-8444-4277-a879-0cf3c8c0c55d)
![image](https://github.com/user-attachments/assets/b002dcd0-fdee-4164-bd5f-d474e4675761)

## Особенности

- **Удобный интерфейс:** Создан с использованием PyQt6 для отзывчивого и интуитивно понятного взаимодействия.
- **Управление процессами:** Легко запускать, останавливать и управлять скриптами для обхода сетевых ограничений.
- **Интеграция с системным треем:** Свертывайте приложение в системный трей для бесперебойной фоновой работы.
- **Настройка автозапуска:** Опция автоматического запуска приложения при старте системы.
- **Управление конфигурацией:** Обновляйте и перезагружайте файлы конфигурации непосредственно из интерфейса.
- **Поддержка тем:** Переключение между светлой и тёмной темами в соответствии с вашими предпочтениями.
- **Автоматические обновления:** Проверка и применение обновлений для обеспечения наличия последних функций.
- **Логирование:** Полное логирование для помощи в устранении неполадок и мониторинге поведения приложения.

## Конфигурация настройки

Приложение использует файл `default.ini`, расположенный в папке `config`. Этот файл содержит настройки для различных скриптов и параметров работы приложения. Вы можете редактировать этот файл вручную и добавлять свои конфигурации. Пример на основе `DiscordFix`:

### Путь к исполняемым файлам должны оставаться как есть 

```py
{ZAPRET_FOLDER}\winws.exe
{ZAPRET_FOLDER}\quic_initial_www_google_com.bin 
{ZAPRET_FOLDER}\tls_clienthello_www_google_com.bin
{ZAPRET_FOLDER}\tls_clienthello_iana_org.bin
```

### Путь к черным спискам должны оставаться как есть 

```py
 "russia-blacklist.txt" - {BLACKLIST_FILES_0}
 "russia-youtube.txt" - {BLACKLIST_FILES_1}
 "discord-blacklist.txt" - {BLACKLIST_FILES_2}
 "disk-youtube.txt" - {BLACKLIST_FILES_3}
 "ipset-discord.txt" - {BLACKLIST_FOLDER}\ipset-discord.txt
 "netrogat.txt" - {BLACKLIST_FOLDER}\netrogat.txt
 "autohostlist.txt" - {BLACKLIST_FOLDER}\autohostlist.txt 
```
### Пример конфига DiscordFix

```py
[DiscordFix]  | Название секции, называйте как хотите
executable = {ZAPRET_FOLDER}\winws.exe | Путь к исполняемому файлу для обхода блокировок
args = 
    --wf-tcp=443;  // Открыть порт TCP 443 (HTTPS)
    --wf-udp=443,50000-65535;  // Открыть порты UDP 443 и диапазон 50000-65535 для использования
    --filter-udp=443; // Фильтрация по UDP-порту 443
    --hostlist={BLACKLIST_FILES_1};  // Список заблокированных доменов {BLACKLIST_FILES_1}
    --dpi-desync=fake;  // Использование метода подделки для обхода DPI
    --dpi-desync-udplen-increment=10;  // Увеличение длины UDP-пакетов на 10 байт
    --dpi-desync-repeats=6;  // Повторить процесс десинхронизации 6 раз
    --dpi-desync-udplen-pattern=0xDEADBEEF;  // Шаблон для изменения длины UDP-пакетов
    --dpi-desync-fake-quic={ZAPRET_FOLDER}\quic_initial_www_google_com.bin;  // Использование поддельного трафика QUIC
    --filter-udp=50000-65535;  // Фильтрация по UDP-портам в диапазоне 50000-65535
    --dpi-desync=fake;  // Повторное использование метода подделки для обхода DPI
    --dpi-desync-any-protocol; // Применение метода десинхронизации ко всем протоколам
    --dpi-desync-cutoff=d3;  // Обрезка данных для дополнительного обхода DPI
    --dpi-desync-repeats=6;  // Повторить десинхронизацию 6 раз
    --dpi-desync-fake-quic={ZAPRET_FOLDER}\quic_initial_www_google_com.bin;  // Повторное использование поддельного QUIC трафика
    --new;  // Начать новый сеанс
    --filter-tcp=443;  // Фильтрация по TCP-порту 443
    --hostlist={BLACKLIST_FILES_1};  // Список заблокированных доменов {BLACKLIST_FILES_1}
    --dpi-desync=fake,split; // Метод подделки и разбиения пакетов для обхода DPI
    --dpi-desync-autottl=2;  // Автоматическое управление TTL (Time to Live)
    --dpi-desync-repeats=6;  // Повторить процесс десинхронизации 6 раз
    --dpi-desync-fooling=badseq; // Обман DPI с помощью неправильной последовательности пакетов
    --dpi-desync-fake-tls={ZAPRET_FOLDER}\tls_clienthello_www_google_com.bin;  // Использование поддельного TLS трафика
```
### Дополнительные файлы конфигурации

В архиве с программой лежат конфигурации которые вы можете использовать вместо обычного `default.ini`. `DiscordFix (для МГТС).ini`, `YoutubeFix (для МГТС).ini`, `FixYouTube+Discord (для Билайн, Ростелеком, Инфолинк).ini` и т.д. Чтобы открыть папку с конфигурациями нажмите кнопку `Открыть configs`.

### Возможные ошибки

- Если не нажимается кнопка запустить, значит ошибка в конфигурации, в текстовом поле должна отобразиться ошибка.
- Одинаковые названия для конфигураций не доспустимы, иначе программа выдаст ошибку.

## Использование тем

Можете редактировать в папке `.._internal\resources\styles` файлы с расширением `.qss` под свои нужды, если кому не нравится стандартный интерфейс программы.
```py
dark_theme.qss - темный интерфейс
light_theme.qss - светлый интерфейс
```

## Установка

Для тех кто не хочет собирать свой проект и вносить в него изменения можете загрузить архив с вкладки [Releases](https://github.com/zhivem/DPI-Penguin/releases), а кто хочет собрать свой:

1. Клонируйте репозиторий:

    ```bash
    git clone https://github.com/zhivem/DPI-Penguin.git 
    ```

2. Установите зависимости:

    ```bash
    pip install -r requirements.txt
    ```

3. Запустите программу:

    ```bash
    python main.py
    ```

## Благодарности

- **GoodbyeDPI:** Основа для работы YouTube. Разработчик: ValdikSS. [Репозиторий](https://github.com/ValdikSS/GoodbyeDPI)
- **Zapret:** Основа для работы Discord и YouTube. Разработчик: bol-van. [Репозиторий](https://github.com/bol-van/zapret)

## Лицензия 

Этот проект лицензирован под [Apache License, Version 2.0.](https://raw.githubusercontent.com/zhivem/DPI-Penguin/refs/heads/main/LICENSE)
