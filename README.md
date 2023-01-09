# Скрипт для работы с Evernote

## Подготовка
1. Зарегистрируйтесь на [Evernote](https://www.evernote.com/Registration.action).
2. Зарегистрируйте [приложение](https://dev.evernote.com/key.php) с правами "Full Access".
3. Получите [токен](https://dev.evernote.com/get-token/) используя данные из предыдущего шага.
4. Создайте `.env` файл следующего вида:
```
EVERNOTE_CONSUMER_KEY=ключ вашего приложения
EVERNOTE_CONSUMER_SECRET=секретная строка вашего приложения
EVERNOTE_PERSONAL_TOKEN=ваш персональный токен, полученный на шаге №3
EVERNOTE_SANDBOX=значение True или False
JOURNAL_TEMPLATE_NOTE_GUID=guid аблона для заметок
JOURNAL_NOTEBOOK_GUID=guid для блокнота
INBOX_NOTEBOOK_GUID=guid почтового блокнота
```
5. Убедитесь, что на вашем компьютере установлен python2, а не python3, так как это может привести к невозможности установки библиотек из-за того, что [Evernote SDK](https://pypi.org/project/evernote/) было предназначено для версий *Python 2.X*.
6. Установите зависимости с помощью `pip`:
```
pip install -r requirements.txt
```

## Использование

### add_note2journal.py
Используется для создания заметок по шаблону из `JOURNAL_TEMPLATE_NOTE_GUID`. В названии заметки шаблона могут быть использованы ключи для подстановки дня недели и даты: `{dow}` и `{date}`.
В качестве аргумента для вызова может быть передана произвольная дата в формате `YYYY-MM-DD`.
Пример запуска скрипта:
```
python add_not2journal.py 2022-01-18
```
Создаст заметку с переданной датой: `2022-01-18`.

### list_notebooks.py
Выводит список всех блокнотов пользователя и их `GUID`.
Пример запуска скрипта:
```
python list_notebooks.py
```

### dump_inbox.py
Выводит список заметок из почтового блокнота, указанного в `INBOX_NOTEBOOK_GUID`.
В качестве аргумента вызова может быть использовано число для ограничеия кол-ва вывода.
Пример вызова:
```
python dump_inbox.py 10
```
Выведет последние 10 заметок. 

### config.py
Содержит в себе настройки переменных окружения.

### Цель проекта
Код написан в образовательных целях на онлайн-курсе для веб-разработчиков [dvmn.org](https://dvmn.org/).