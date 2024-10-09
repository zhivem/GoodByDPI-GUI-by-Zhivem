# GoodByeDPI GUI by Zhivem [YouTube + Discord ( + Голосовой чат )]

## О проекте

Этот проект представляет собой графический интерфейс для утилиты [GoodByeDPI](https://github.com/ValdikSS/GoodbyeDPI/releases), которая помогает обходить блокировки и фильтрацию интернет-ресурсов. Программа предоставляет удобный способ запуска и управления процессом GoodByeDPI через графический интерфейс, а также поддерживает функции обновления чёрных списков и управления службами.

Доступна также **версия программы в формате `.exe`** для пользователей, которые не хотят вручную устанавливать зависимости или запускать исходный код. Готовую сборку можно скачать на странице [релизов проекта](https://github.com/zhivem/GoodByDPI-GUI-by-zhivem/releases).

![image](https://github.com/user-attachments/assets/6d08d6ed-73ac-45e9-bf1d-addbf5325c37)
![image](https://github.com/user-attachments/assets/fc2a294c-c9af-4f76-ae1b-73b31b92a475)


## Основные файлы

- **`main.py`** — основной файл для запуска графического интерфейса.
- **`gui.py`** — файл, содержащий классы для построения GUI с использованием PyQt5.
- **`process_worker.py`** — отвечает за выполнение фоновых процессов для управления GoodByeDPI.
- **`updater.py`** — обновлённый модуль для проверки доступных версий программы и работы с обновлениями.
- **`utils.py`** — содержит полезные функции и константы, которые используются в других модулях.
- **`site_checker.py`** — отвечает за проверку доступности списка веб-сайтов в фоновом потоке с использованием библиотеки PyQt5.

## Новые возможности

1. **Создание и удаление службы**:
   - Пользователь теперь может создавать системную службу для автоматического запуска **GoodByeDPI** при загрузке системы.
   - Есть возможность удалить службу через графический интерфейс.

2. **Автоматическое обновление и поддержка чёрных списков**:
   - Реализована возможность обновления списков заблокированных ресурсов по сети.

3. **Проверка обновлений программы**:
   - Программа автоматически проверяет наличие новых версий и уведомляет пользователя о необходимости обновления.

4. **Обход блокировки Discord**:
   - Добавлен пресет и списки для Discord. (❗️Работает с голосовым чатом)

5. **Проверка доступности к YouTube**:
   - Добавлена проверка доступности к сайтам.

## Основной функционал GUI

- **Выбор сценария обхода блокировок**: Предлагается несколько вариантов скриптов для обхода блокировок (например, для YouTube, Discord и общего обхода для всех сайтов).
- **Запуск и остановка процесса**: В интерфейсе доступна кнопка для запуска и остановки процесса GoodByeDPI.
- **Управление системными службами**: Позволяет создать службу для автозапуска GoodByeDPI, а также удалить её при необходимости.
- **Обновление черных списков**: Кнопка для автоматического обновления чёрных списков.
- **Проверка обновлений**: Встроенная функция для проверки новых версий программы с уведомлениями.

### Черные списки:

- **`russia-blacklist.txt`** — содержит список заблокированных сайтов.
- **`russia-youtube.txt`** — содержит список заблокированных YouTube-каналов.
- **`discord-blacklist.txt`** — содержит список заблокированных Discord-каналов.

## Установка

1. Клонируйте репозиторий:

    ```bash
    git clone https://github.com/zhivem/GoodByDPI-GUI-by-zhivem.git
    ```

2. Установите зависимости:

    ```bash
    pip install -r requirements.txt
    ```

3. Запустите программу:

    ```bash
    python main.py
    ```

## Использование

Программа предлагает удобный графический интерфейс для запуска, управления и обновления утилиты GoodByeDPI. Просто выберите нужный сценарий, нажмите "Запустить", и программа выполнит необходимые действия.

# Похожие проекты

- **[GoodbyeDPI UI](https://github.com/Storik4pro/goodbyeDPI-UI)** by @Storik4pro
- **[Launcher for GoodbyeDPI](https://topersoft.com/programs/launchergdpi)** by @TOPERSOFT
- **[Zapret](https://github.com/bol-van/zapret)** by bol-van

## Вклад в проект

Если вы хотите внести свой вклад в проект, пожалуйста, создайте pull request. Любая помощь и улучшения приветствуются!

## Благодарности

Особая благодарность ValdikSS за создание проекта GoodbyeDPI.
