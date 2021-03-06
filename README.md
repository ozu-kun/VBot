VBot
======

**ВНИМАНИЕ**
Я забросил этот проект, но, возможно другой человек продолжит разрабатывать этого бота. В любом случае я буду принимать пулл реквесты!

Асинхронный чат-бот для ВКонтакте.
Идеально подходит как помощник в конференциях.

Для работы бота необходим Python 3.6+ или PyPy3.5, с версиями ниже бот **не работает** и поддержка старых версий не планируется.
Работоспособность проверена **исключительно на ОС семейства Linux** (однако пользователи сообщали о работоспособности под Windows).

## Начальная настройка
1. Перейдите в папку с ботом
2. Выполните команду `pip3 install -r requirements.txt`. Это автоматически установит все нужные модули.
3. Запустите бота, чтобы он создал файл `settings.py` - `python3 vbot.py`.
4. **В `settings.py` замените `TOKEN` на access_token группы или `LOGIN` и `PASSWORD` на логин и пароль аккаунта ВК соответственно.**
5. Запустите `python3 lolbot.py` (если вам нужно запустить бота в фоне, используйте `screen` под Linux).

## Смена префиксов
По умолчанию бот отзывается на три префикса: `лолбот`, `лб`, `!`. 
Сменить их можно в `settings.py` на 17 строке.

## Плагины
* Приветствие (Плагин приветствия)
* Список плагинов (Список загруженных плагинов)
* Музыка (Список музыки из ваших рекомендаций в ВК)
* Случайное число (Случайное число в разных диапазонах)
* Случайные мемы (Берутся из паблика, указанного в плагине memes.py)
* Случайные мемы с 2ch (Берутся из паблика, указанного в плагине 2ch.py)
* Ближайшие дни рождения в группе (Берутся из паблика, указанного в плагине hday.py)
* Курс валют (Отображение основных курсов валют)
* Список команд (Список всех команд бота с описанием, как их использовать)
* Шар восьмерка (Решает за вас)
* Время (Показывает текущую дату и время)
* Статистика бота (Показывает данные о счетчиках аккаунта)
* Послать сообщение (Посылает сообщение другому пользователю)
* Блокнот (Может запоминать и вспоминать строки)
* Рассказать шутку (рассказывает случайный анекдот)
* Выключение (Выключает бота, если команду послал администратор)
* Поиск видео (Ищет видео в ВК по запросу пользователя)

## Примечание
Для того, чтобы узнать ID пользователя или группы, используйте https://vk.com/linkapp

## Создание плагинов
В папке plugins есть пример плагина в файле example.py, отвечающий на команду `!тест`
Там есть и другие плагины, код которых можно просмотреть для понимания того, что можно сделать с помощью бота.

Каждый плагин должен иметь экземпляр класса Plugin (из plugin_system) под именем(обязательно) plugin, вот пример простого плагина:
```python
# Импортируем класс Plugin
from plugin_system import Plugin
# Создаём объект класса, через него мы будем "подписываться" на команды
plugin = Plugin('Плагин для еды')

# Использование async и await обязательно, т.к. бот использует asyncio
@plugin.on_command('еда')
async def test(msg, args):
    await msg.answer('Где еда?!')
```

Плагины размещаются в папке `plugins`. Если два плагина имеют одинаковые команды - они обрабатываются в обоих плагинах.
Плагины могут работать со всеми методами API ВКонтакте.

#### Связь со мной
Меня можно найти в ВК - https://vk.com/tiberium_1111
