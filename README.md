

# Домашнее задание к занятию "12.7 «Репликация и масштабирование. Часть 2»" - Соловьёв Андрей SYS-18

---


## Задание 1.

Опишите основные преимущества использования масштабирования методами:

1. активный master-сервер и пассивный репликационный slave-сервер, master-сервер и несколько slave-серверов:

Мастер используется для записи или изменения информации, слейвы — для копирования информации с мастера и её чтения. Чаще всего используется один мастер и несколько слейвов, так как обычно запросов на чтение больше, чем запросов на изменение. Главное преимущество репликации — большое количество копий данных.

- Репликация мастер-мастер - Преимуществом является гибкость, поскольку каждый участвующий экземпляр базы данных хорошо инкапсулирован, а сценарии гибридной репликации возможны с несколькими наборами мастеров.
В этой схеме, любой из серверов может использоваться как для чтения так и для записи.

- Репликация Master-Slave - 

Преимущества -  резервное копирование,  способ анализа данных без использования Master БД, или как средство для масштабирования:

При такой схеме  копирование всей базы данных практически не влияет на работу Мастера - аналитические приложения могут считывать данные с подчиненных устройств, не влияя на главный.
Подчиненные устройства могут быть переведены в автономный режим и синхронизированы с ведущим устройством без каких-либо простоев. 
В случае аварии на основном сервере, есть возможность быстро переключить нагрузку на резервный.

master-slave-slave-...уменьшает в разы нагрузку и скорость чтения информации пропорционально увеличению колличества slave серверов

2. активный сервер со специальным механизмом репликации — distributed replicated block device (DRBD) -   преимущество  в основном только в увеличении отказоустойчивости.

3. SAN-кластер - быстродействие и масштабируемость, центральное управление и резервирование данных без загрузки локальной сети и серверов.


## Задание 2.


Разработайте план для выполнения горизонтального и вертикального шаринга базы данных. База данных состоит из трёх таблиц:

пользователи,
книги,
магазины (столбцы произвольно).
Опишите принципы построения системы и их разграничение или разбивку между базами данных.


База данных состоит из трех таблиц:

пользователи, книги, магазины.

## Вертикальный шардинг

Каждая таблица находится на отдельном сервере.

![vertical.PNG](https://github.com/Andrewsolo1969/12-7-hw/blob/master/img/vertical.PNG)


## Горизонтальный шардинг

таблица Книги разделена на 2 сервера (server_BD4, server_BD5) по названию книги по алфавиту от A-N и от O-Z

таблица Пользователи разделена  на 2 сервера server_BD1 - аутентификация, server_BD2 данные пользователей

таблица Магазины  перенесена полностью в отдельный сервер без изменений


![Gorizontal.PNG](https://github.com/Andrewsolo1969/12-7-hw/blob/master/img/Gorizontal.PNG)













 
