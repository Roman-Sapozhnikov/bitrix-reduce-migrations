Модуль миграций 2.0
===============

Модуль миграций для CMS "1С-Битрикс" – быстрые и стабильные обновления баз данных проекта.

Известно, что с развитием проекта изменению подлежат не только исходный код и алгоритмы бизнес логики, но так же добавляются или удаляются новые сущности или их поля. Для упрощения изменений и последующих обновлений данных и предназначен данный модуль.

## Возможности

* Составление сценариев миграций с помощью специальных ```билдеров```, специально предназначенных для этих нужд. Таким образом создание новых сущностей данных будет происходить не труднее чем через административный интерфейс;
* Актуализация данных. Бавают случаи когда данные нужно "подправить" не меняя структуры - миграции подходят для этого как нельзя кстати. Сценарий будет запущен один раз и для всех площадок;
* Работа через командную строку. Обновление можно выполнять как вмести с обновлением исходного кода, так и использовать специальные инструменты систем версионирования - запуска скриптов после обновления.

## Преимущества

* Стабильность. Сценарии миграций данных составляются и отлаживаются командой.
* Удобство. Модуль обладает широким спектром функционала для манипулирования миграциями.
* Информативность. Удобный вывод списков миграций при работе через консоль.
* Предсказуемость. Можно указывать примерное время выполнения миграций – это будет спобоствовать правильному принятию решения при обновлении.

## Как это работает?

Простейшая схема работы команды над проектом выглядит следующим образом:

![Схема работы над проектом](project_state.png)

Есть локальные площадки програмистов и есть сервера которые доступны "извне" через Интернет. Каждая площадка имеет отдельную базу данных. Базы данных площадок отличаются только наполнением, но схемы (таблицы, поля, инфоблоки и т.д.) данных одинаковы.

Процесс изменения схемы данных (либо манипуляции над данными) которые нужны для каждой площадки следующий:

1. Необходимо сделать изменения в схеме данных на проекте. К примеру добавить поле в одну из сущностей, которое будет использоваться новой функцией.
2. Разработчик создает миграцию добавления нового поля. Миграцией будет являться файл (класс php), определенного формата, в котором необходимо написать сценарии обновления (добавления поля) и отката (удаления поля) на случай неудачного применения обновления или отката версии проекта на предидущую.
3. Запускает миграцию на локальной копии проекта, отлаживает применение и откат миграции.
4. Регистрирует миграцию в системе версионарования. Так исходный код для запуска миграции распрастраниться по всем платформам.
5. Каждая площадка получившая исменения исходного кода запускает обновления миграций.

Таким образом новое поле в базу данных добавляется для всех площадок получивших изменения одинаковым образом.

## Что дальше?

* [Устанавливаем модуль](docs/setup.md)
* [Создаем сценарии миграций](docs/scripts.md)
* [Работаем с готовыми сценариями миграций через конмандную строку](docs/update.md)
* [Интерфейс командной строки ???](docs/cli.md)
* [Миграции в административном интерфейсе]()
