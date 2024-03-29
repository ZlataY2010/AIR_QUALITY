## [[База]]
В сутки человек вдыхает 14кг воздуха, помимо пыли человек вдыхает **летучие органические соединения** (VOC), которые включают в себя **углеводороды, альдегиды, спирты, кетоны, терпеноиды** и т.д. За год человек может вдохнуть 6,5 граммов **кетонов**.
###### [[Компоненты монитора]]
1. Пластиковый корпус
2. LED экраны
3. Печатная плата с компонентами
4. Провода питания
5. Сенсоры температуры и качества воздуха
6. Магниты двух видов
7. Упаковка
8. Салфетки для монтажа
9. Блоки питания
10. Защитное стекло
11. Плёнка на стекло
12. Набор винтов
###### [[Инструменты]]
1. Паяльная станция
2. Паяльная паста
3.  Флюс
4. Смывка для печатных плат
5. Лампа с увеличительным стеклом
6. Сетевой фильтр
7.  Набор отвёрток
8. Пинцет
9. Штангенциркуль
10. Скотч 3м
11. Стриппер для кабеля
12. Гибкие кронштейны для пайки
13. Струбцины
14. Пластиковые лотки


## [[Связь]]
• Самая подходящая связь для сенсоров это - **[[LPWAN]]**  
 • Рабочая сеть с покрытием - **NB-Fi** 
 связь реализуется через чип **WA1470** (можно взять готовый модуль)
## [[Сенсоры]]
Производитель рекомендует брать **SGP40** 
Для расчета VOC требуется сообщить сенсору SGP40 влажность и температуру, для этого надо установить **BME280**. Сенсор также умеет регистрировать атмосферное давление.
## [[Микроконтроллер]]
Автор предлагает от **STMicroelectronics STM32L412KB**. Автор утверждает, что он имеет малое энергопотребление и содержит много памяти.
## [[Питание]]
Для автономности нужно установить **Li-ion** аккумулятор ёмкость 180 мАч. Зарядка осуществляется через разъем **Micro-USB.** Для питания всей схемы используется линейный стабилизатор напряжения.
## [[Схема, печатная плата, антенна]]
- [Схема](https://habrastorage.org/r/w1560/getpro/habr/upload_files/f0d/2a6/cfa/f0d2a6cfa7f6c7bc1f1eeafaee491879.jpg) 

- [Печатная плата](https://habrastorage.org/r/w1560/getpro/habr/upload_files/916/9c6/1c8/9169c61c845a0fa67a64572e2788b7ce.png)

- [Модель расчёта антенны](https://habrastorage.org/r/w1560/getpro/habr/upload_files/b03/d7f/9a2/b03d7f9a2a6100f74747606bc33bae5d.jpg)

- [Коэффициент отражения волны](https://habrastorage.org/r/w1560/getpro/habr/upload_files/8a4/ddb/132/8a4ddb132c74210f0e42370b877a0efc.jpg)

- [Коэффициент стоячей волны](https://habrastorage.org/r/w1560/getpro/habr/upload_files/0ba/1eb/d28/0ba1ebd2885462dd1adac35244275bf1.jpg)

- [Диаграмма направленности](https://habrastorage.org/r/w1560/getpro/habr/upload_files/b92/7cc/d4d/b927ccd4d1ecd5db4365569248c176a8.jpg)
## [[Софт]]
Данные отправляются каждый **час** с процентным расходом передаваемых показателей каждые **2,5 минуты**. 
 
Автор пишет что: самым большим вопросом было общение с **WA1470**. Документации немного, есть только библиотека, в которую можно интегрироваться. Сам чип общается по **SPI** и имеет еще две ножки: одна — это выход для подачи прерываний, а вторая — это вход для включения или выключения всей микросхемы. Есть возможность взять просто модуль и общаться АТ-командами
## [[Потребление энергии]]
Измерение с периодом в **30** секунд потребляет **15,6 мкА**. Вместе с передачей раз в час **405** мкА. На аккумуляторе датчик проработает **18** дней. Если вставить батарейку размера АА, то получается уже **260** дней автономности.

- [Потребление без передачи](https://habrastorage.org/r/w1560/getpro/habr/upload_files/3cc/135/6fa/3cc1356fa7333fb52f3f854b1d7b082e.png) 

- [Среднее потребление](https://habrastorage.org/r/w1560/getpro/habr/upload_files/f72/952/6b1/f729526b16d59799514b212f987c7bf2.png)  
##  [[Сеть и данные]]
Далее данные попадают на сервер **NB-Fi**, где их можно будет получить через **API**. 
 
Информацию можно выводить [сюда](https://narodmon.ru/). Можно добавить почти любой сенсор, но нужно установить датчики снаружи здания.
## [[Что можно добавить]]
##### 1. Установить всепогодные датчики. 
##### 2. Сделать дополнительный кейс для установки снаружи зданий для защиты от дождя и снега. 
##### 3.  Установить дополнительные сенсоры опасных веществ. 
##### 4.  Установить сбор солнечной энергии для полной автономности. 
##### 5. Проработать применение этой технологии в других сферах, например в теплицах