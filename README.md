# VKinder

![9WrCCXEvxyg](https://user-images.githubusercontent.com/100129717/179293274-18206c68-693f-4c6c-8e25-6106a970e9b0.jpg)


## Техническое описание проекта

Проект содержит программу-бота для взаимодействия с базами данных социальной сети. Бот предлагает различные варианты людей для знакомств
в социальной сети Вконтакте в виде диалога с пользователем.

Программа-бот выполняет следующие действия:

1. Существует два сценария поиска человека:
    * Используя информацию (возраст, пол, город) о пользователе, который общается с ботом в ВК, производится поиск других людей (других пользователей ВК) для знакомств.
    * В режиме диалога Бот запрашивает возраст для поиска человека.
2. Собеседник бота получает три самые популярные фотографии профилей, которые подошли под критерии поиска. Популярность определяется по количеству лайков.
3. В чат с ботом выводится информация о пользователе в формате: имя, фамилия, ссылка на профиль, три популрных фотографии.
4. С помощью кнопок реализована возможность лайкнуть или дизлайкнуть пользователя.
5. Информация о лайкнутых и дизлайкнутых пользователях сохраняется в соответствующие таблицы в базу данных.
6. С помощью кнопки "Показать избранные" есть возможность увидеть список понравившихся пользователей.
7. При взаимных лайках (match) пользователи получают информацию о лайкнувшем его человеке в сообщении.


## Структура каталога проекта

- sql_database.py
- search_people.py
- server.py
- main.py
- settings.ini
- test_unittest.py
- requirements.txt
- README.md

### Модуль sql_database.py
>В модуле определяется класс Postgresql реализующий логику взаимодействия с базой данных.
#### Диаграмма
![4](https://user-images.githubusercontent.com/100129717/179345921-3e2023a1-478c-4d7a-b63a-56f953169d3e.png)

Для создания таблиц следует вызвать метод "create_tables" в классе Postgresql.

### Модуль search_people.py
>Модуль служит для поиска профилей по определенным параметрам. 
>В ВК максимальное количество результатов при поиске - 1000 человек. Обойти это ограничение можно с помощью цикла и добавления
>дополнительного параметра при поиске (в данном случае итерировались по месяцам). Такой способ помог увеличить кол-во
>результатов примерно в 8 раз.

### Модуль server.py
>Основной модуль, содержащий класс Server. Данный класс реализует логику взаимодействия с API ВКонтакте, 
>содержит различные методы и главный цикл обработки событий.

### Модуль main.py
>Данный модуль запускает чат-бота.

### Файл settings.ini
>Файл конфигурации "settings.ini" содержит данные для подключения к базе данных и для инициализации запуска чат-бота.

### Модуль test_unittest.py
>В файле реализовано тестирование отдельных методов и функций.

### Файл requirements.txt
>В файле содержится список внешних зависимостей.


## Установка
Перед запуском программы нужно создать базу данных в Postgresql, ввести данные в файл "settings.ini": имя базы, пользователь и пароль.
В социальной сети "ВКонтакте" создать сообщество и занести в файл "settings.ini" токен, id-группы и access code.

## Пример общения с чат-ботом
![1](https://user-images.githubusercontent.com/100129717/179293347-7123046b-e7e7-406d-a8ff-a148b55e455c.png)

![2](https://user-images.githubusercontent.com/100129717/179293358-771ed772-3209-46d2-9ce8-c2a1ec4bdadc.png)

![3](https://user-images.githubusercontent.com/100129717/179293361-b74ff9d7-d4cf-43de-9bf0-4f1a3b1bcf6d.png)