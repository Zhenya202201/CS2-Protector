# CS2-Protector AntiCheat для Кс2

🔹 Пошаговая инструкция для пользователя

1️⃣ Скачивание и распаковка

1. Скачай архив CS2-AntiCheat.zip.


2. Распакуй его в удобную папку на компьютере или сервере.
Структура папки после распаковки:



CS2-AntiCheat/
 ├── scripting/
 │    ├── anticheat.sp           # исходник плагина
 │    └── compile.exe            # SourceMod компилятор
 ├── modules/
 │    ├── process_checker.cpp
 │    └── dll_checker.cpp
 ├── configs/
 │    └── anticheat.cfg
 ├── scripts/
 │    └── auto_update_and_build.bat
 ├── CHANGELOG.txt
 ├── logs/
 ├── demofiles/
 └── README.md


---

2️⃣ Проверка SourceMod

В папке scripting/ уже есть compile.exe — это компилятор SourceMod для Windows.

Он нужен, чтобы собрать anticheat.sp в .smx.

Если вдруг его нет — скачай SourceMod с официального сайта и положи compile.exe в папку scripting/.



---

3️⃣ Первый запуск скрипта

1. Открой папку scripts/.


2. Дважды кликни auto_update_and_build.bat.



Что делает скрипт автоматически:

Проверяет GitHub на новые коммиты.

Если есть обновления, компилирует:

anticheat.sp → anticheat.smx

process_checker.cpp → process_checker.dll

dll_checker.cpp → dll_checker.dll


Создаёт папки logs/ и demofiles/, если их нет.

Выводит новые пункты из CHANGELOG.txt.

Сохраняет текущую версию в last_update_version.txt, чтобы при следующем запуске показывать только новые улучшения.



---

4️⃣ Копирование плагина на сервер

1. После компиляции скопируй .smx из scripting/compiled/ в папку сервера:



cs2/addons/sourcemod/plugins/

2. Перезапусти сервер или загрузи плагин командой в консоли:



sm plugins load anticheat


---

5️⃣ Настройка античита

Открой файл configs/anticheat.cfg и при необходимости поменяй параметры под свой сервер:


anticheat_aim_threshold "60.0"
anticheat_max_warnings "3"
anticheat_autoban "1"
anticheat_trigger_delay "0.08"
anticheat_max_hs_percent "90"
anticheat_max_kd "4.0"


---

6️⃣ Логи и демо

logs/anticheat.log — текстовые логи подозрительных действий.

logs/anticheat.json — JSON-логи для анализа.

logs/reports.log — репорты игроков через /report nickname.

demofiles/ — демо подозрительных игр.


Все папки создаются автоматически при первом запуске .bat.


---

7️⃣ Обновления

Каждый раз, когда ты добавляешь новую версию в GitHub и обновляешь CHANGELOG.txt, пользователь просто запускает .bat.

Скрипт:

Скачивает новые файлы, компилирует их.

Выводит только новые изменения или улучшения, которых пользователь ещё не видел.
