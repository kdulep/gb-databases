# О лекторе - Ильнар Шафигуллин

* СУБД это система управления базами данных
* CУБД – ИНСТРУМЕНТ

# История
1. Картотека
1. Библиотека
1. Перепись
1. Книга учета

# Для чего?
>Базы данных нужны для хранения,обработки и быстрого извлечения необходимой информации

# Задача
* Необходимо составить базу данных для картинной галереи.

# Иерархическая модель хранения данных
* Есть ограничения
* При создании иерархической базы данных мы уже изначально фиксируем сценарий использования этой базы

# Решение – предметный указатель

# Задача 
* Необходимо создать свой собственный телефонный справочник.

# Проблема
* Больше 2-х номеров
* Пустые ячейки
* Разное количество номеров

# Проблема
* Дубли
* Объём данных

# Проблема
* Несколько одинаковых ФИО

# Решение
* Добавляем уникальные идентификаторы
* Связываем таблицы между собой именно по этому идентификатору
* Таблицы связаны между собой по столбцу id
* Можем разбивать данные на разные таблицы без потери данных

# Relation – связь

>Реляционные базы данных – это базы данных, в которых данные распределены по отдельным, связанным между собой,таблицам.

# Телефонный справочники информация, которую нам хорошо бы хранить:
* ФИО
* Дата рождения
* Статус (семейное положение)
* Телефоны этого человека
* Комментарий к каждому номеру телефона
* Адреса этого человека
* Комментарии к каждому адресу


# Базы данных нужны для хранения, обработки и быстрого извлечения необходимой информации.

# Извлечение информации

1. Вывести все данные из таблицы Общий список.

1. Вывести столбцы ФИО, Тел, Комментарий из таблицы Общий список

1. Вывести столбцы ФИО, Тел, Комментарий из таблицы Общий список.где статус = холост.

# SQL – это особый язык программирования, который позволяет формулировать то, что нужно сделать с данными в таблицах

>SELECT * FROM Общий список

>SELECT – «выбери»; * – после SELECT указывается набор столбцов, * означает что мы хотим видеть все столбцы;
FROM – «из» указываем, откуда необходимо выбрать информацию.
Общий список – название таблицы из нашего примера.

* Вторая задача в этой структуре выглядела бы как: 

>SELECT ФИО, Тел, Комментарий FROM Общий список

* Третья задача может быть записана как:
>SELECT ФИО, Тел, Комментарий FROM общий список WHERE статус = "холост"

# Разобьем нашу базу данных на несколько связанных таблиц

* Есть несколько способов, как можно
соединить таблицы, вы с ними уже
знакомы из теории множеств.

* INNER JOIN
* LEFT JOIN
* RIGHT JOIN
* FULL JOIN

# Рассмотрим, что будет результатом
>INNER JOIN Люди, Телефоны ON id = Чей телефон

# Задача 
* Что будет результатом для команды: 
>INNER JOIN Люди, Адреса ON id = Чей адрес


# Решение

* Что будет результатом для команды: 
>LEFT JOIN Люди, Адреса_2 ON id = Чей адрес

# Что будет результатомдля команды:
>RIGHT JOIN Люди, Адреса_2 ON id = Чей адрес


# Структуры баз данных

# Задача
* Cформировать структуру базы данных для бизнеса в сфере аренды автомобилей.

# Типы связей

# Цель лекции
* Разобрать, как создавать структуру базы данных до наполнения её данными.

# Описание структуры данных
* В каждую таблицу добавлен уникальный идентификатор

# Структура наших таблиц
* Структура таблицы «Люди»
* Структура таблицы «Телефоны»
* Структура таблицы «Адреса»

# Длина: под каждое значение резервируем одинаковое количество символов
>Не надо делать большой запас и перерасходовать память.

>Лучше сразу рассчитать максимальное необходимое количество памяти для каждого типа данных и закладывать достаточное количество памяти.

>Лучше выносить города в отдельную таблицу (справочник).

# Общие рекомендации по подготовке структуры хранения данных

* Добавлять уникальные идентификаторы в каждую таблицу
* Указывать тип данных
* Использовать особый тип данных для даты или времени
* Заранее рассчитывать длину полей.
* Использовать справочники для повторяющихся данных: семейное положение, город и других
* Дробить информацию на несколько полей, если это соответствует вероятным будущим задачам работы с БД. Например, можно разнести значения из «ФИО», номера телефонов и т.д.


# Типы связей между таблицами

* Один к одному
>Одно свидетельство о рождении соответствует одному человеку
* Один ко многим
>Один мужчина был женат на нескольких женщинах

>У одной женщины несколько детей.

* Многое ко многому
>По одному адресу зарегистрированы несколько людей, и у каждого человека, в свою очередь, может быть несколько адресов: фактический и адрес регистрации, например.

# Разбор базы данных «Аренда автомобилей»

# Как сделать оптимальную базу данных

>Изначально в таблице не было поля «Регистрационный номер», и сейчас имеющейся информации недостаточно,чтобы установить, кто из клиентов превысил скорость и кто должен платить штраф

>Понять, какие бывают ситуации и кейсы.

>Понять, какая информация может понадобится в разных кейсах.

>Понять, какой путь проходит клиент от момента начала коммуникации с сервисом до завершения, какая информация сопровождает этот путь.

>На этапе создания базы данных придумывать кейсы, в которых ваша база данных может «сломаться».

# Структура базы данных библиотеки

Какая структура данных нужна в библиотеке?
* Перечень книг.
* Жанры книг.
* Перечень читателей.
* Данные о том, кто какие книги читал.

# Связь по author_id

# Книги с несколькими авторами

# Недостающая таблица

>для полей Start_date и End_date мы сделали тип данных TimeStamp. Почему?
: иногда в библиотеках берут книги не на несколько дней, а на несколько часов для работы в читальном зале. Нужно учитывать выдачу книг в рамках одного дня. Если есть задача фиксировать событие в рамках дня, надо добавлять поле с типом данных TimeStamp, чтобы понимать, в какой день и в какое время произошло событие.



