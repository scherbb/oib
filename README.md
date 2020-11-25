# oib
# Практика 1
***
Компания ООО «Теремок». Управление компании использует телефонную связь и защищенное интернет соединение. Бухгалтерия использует телефонную связь и защищенное интернет соединение. Штат – 271 сотрудников. 1 – Генеральный директор. 3 - Архитектор. 5 - Руководитель проэкта. 1 - Секретарь. 1 - Главный бухгалтер.  10 – Отдел безопасности. 15 – Финансовый отдел. 20 – Бухгалтерия. 15 – Охрана. 200 - Строители. Руководство получает заказы на стройку проэктов, используя телефонную связь (передача шифрованной речи осуществляется по каналам CSD 9600 бит/с) и уведомление о передаче этапов работы на компьютер. Передача этапов работы происходит через защищенное интернет соединение. Вся документация защищена паролями. Отдел безопасности занимается организацией и обеспечением защиты любой информации, полученной на территории организации. Обеспечивают руководство физическим вводом ключа при получении. Использует любую связь, исключительно скрытую. Имеет доступ к местам хранения информации организации. Отдел безопасности защищает все каналы связи компании, по которым передаются и получаются важные договора и документы. Вся важная информация, полученная компанией, сохраняется на сервер организации. Также отдел безопасности имеет доступ ко всем ПК сотрудников и камерам. Бухгалтерия занимается: учетом финансов, составлением таблиц с затратами компании, налогами, подтверждением документов на те или иные ресурсы, требующиеся для работ. Бухгалтерия использует телефонную связь. Имеет доступ к помещениям бухгалтерии. Охрана находится на территории всей организации. На выходе из организации установлен пункт досмотра. Каждый входящий и выходящий из организации обязан пройти досмотр на присутствие запрещенных предметов. Имеет доступ к местам перемещения по организации, могут запросить доступ к другим помещениям по необходимости. Технический регламент для отдела безопасности: -Постоянный анализ информационного пространства с целью выявления уязвимостей. -Своевременное обнаружение проблем, потенциально способных повлиять на информационную безопасность, корректировка моделей угроз и нарушителя. -Исключать возможность доступа третьих лиц к документам, содержащим конфиденциальную информацию. -Контролировать состояние рабочего места, сообщать руководству обо всех ситуациях, имеющих характер инцидентов информационной безопасности. -Регулярно выявлять основные пути и способы попадания зараженной вирусом информации в систему организации. Инструкция для специалиста по безопасности: Специалист должен знать: -Основы трудового законодательства. -Законодательство о безопасности, о защите информации, об оперативно-розыскной деятельности и др. -Устав организации, правила внутреннего порядка. -Характеристики технических средств защиты объектов, информации от несанкционированного доступа к ним. -Тактику защиты объектов, информации, персонала предприятия от преступных посягательств. -Характеристику технических средств (системы сигнализации, связи, защиты информации, пр.). 
***
***
# Практика 2
***
Для анализа я выбрал сайт ru-forum.com
***
Чтобы узнать ip сайта я открыл консоль и ввел команды ping и nslookup:

<img width="305" alt="Снимок экрана 2020-10-05 193624" src="https://user-images.githubusercontent.com/70718269/95111951-f090e700-0748-11eb-86b7-60008b675b02.png">

И вот что получилось:

<img width="660" alt="практика 2 пинг" src="https://user-images.githubusercontent.com/70718269/95436377-6f11a280-095c-11eb-98ca-d1c373f58d61.png">

Отсюда можно узнать, что ip сайта 91.194.2.84
Затем я использовал команды утилиты nslookup: -query=mx, -query=soa и -query=nx

<img width="672" alt="mx и soa" src="https://user-images.githubusercontent.com/70718269/95437539-c3695200-095d-11eb-83d6-3e81b644e133.png">
<img width="254" alt="nx" src="https://user-images.githubusercontent.com/70718269/95452396-dbe36780-0971-11eb-8d50-320a7ba126fd.png">
Команда nslookup позволяет узнать ip сайта, mx  показывает почтовые сервера для домена, soa показывает cервер с эталонной информацией о домене

Далее для просмотра всех доступных записей DNS я ввел -type=any
<img width="302" alt="-type=any" src="https://user-images.githubusercontent.com/70718269/95972713-741e9800-0e1b-11eb-8c94-bedbd1bd7302.png">

Далее для анализа трафика я использовал фильтр 'ip.src==(ip сайта)' в wireshark
<img width="952" alt="ip src" src="https://user-images.githubusercontent.com/70718269/95974038-13905a80-0e1d-11eb-9762-bbbc767bf489.png">

Потом я ввел фильтр ip.dst, который отвечает за трафик отправленный на ip
<img width="953" alt="ip dsp" src="https://user-images.githubusercontent.com/70718269/95974576-d5e00180-0e1d-11eb-917b-f5abd21e0152.png">

Затем ip.addr, который отвечает за фильрацию трафика, в котором упоминается этот ip
<img width="955" alt="ip addr" src="https://user-images.githubusercontent.com/70718269/95974986-4a1aa500-0e1e-11eb-9463-8ac8fc14a0d2.png">

Я использовал фильтр arp.src.hw_mac, который используется для фильтрации по ARP протокола по mac - адресу
<img width="944" alt="ь" src="https://user-images.githubusercontent.com/70718269/95979978-29098280-0e25-11eb-9b44-5f2644a76e32.png">

Далее я использовал фильтры eth.dst: фильтр трафика по mac - адресу получателя,eth.src: фильтр трафика по mac - адресу отправителя 
<img width="950" alt="ь2" src="https://user-images.githubusercontent.com/70718269/95980302-a1704380-0e25-11eb-8d8d-fb2985798716.png">
<img width="952" alt="ь3" src="https://user-images.githubusercontent.com/70718269/95980347-b4831380-0e25-11eb-97cc-005bd9b6f6ab.png">
***
***
# Практика 3
***
Чтобы посмотреть методанные я взял фотку из своего телефона
![попугй](https://user-images.githubusercontent.com/70718269/98211368-fe59a800-1f52-11eb-940c-5055cd148933.jpg)

Перекинул ее на комп и открыл свойства

<img width="280" alt="спвойства 1" src="https://user-images.githubusercontent.com/70718269/98211824-b25b3300-1f53-11eb-92e7-1b7e58fda8f9.png">
<img width="280" alt="свойства 2" src="https://user-images.githubusercontent.com/70718269/98211835-b71fe700-1f53-11eb-836e-fd5e767fa645.png">

Вроде все на месте
***
Для анализа зарубежного информационного ресурса я выбрал сайт asos.com

<img width="461" alt="Снимок экрана 2020-11-04 131703" src="https://user-images.githubusercontent.com/70718269/98212183-45946880-1f54-11eb-8258-cdfdb8e24c2f.png">

С гуглом у меня выдавало слишком много запросов, поэтому искал информациб тоько в bing и duckduckgo

<img width="727" alt="Снимок экрана 2020-11-04 133307" src="https://user-images.githubusercontent.com/70718269/98213243-cf910100-1f55-11eb-8f41-cb7b3c4bbd78.png">

<img width="134" alt="Снимок экрана 2020-11-04 133734" src="https://user-images.githubusercontent.com/70718269/98213313-efc0c000-1f55-11eb-9943-8e3503449cf0.png">

Я взял первый попавшийся pdf файл и посмотрел методанные

<img width="725" alt="Снимок экрана 2020-11-04 133637" src="https://user-images.githubusercontent.com/70718269/98213598-5e058280-1f56-11eb-88bf-815a11d660b3.png">

Далее CCleaner 

<img width="757" alt="Снимок экрана 2020-11-05 012944" src="https://user-images.githubusercontent.com/70718269/98214077-16cbc180-1f57-11eb-9678-a45790139752.png">

Я нашел одинакове файлы и удалил
<img width="749" alt="Снимок экрана 2020-11-05 100947" src="https://user-images.githubusercontent.com/70718269/98214487-9eb1cb80-1f57-11eb-93e8-94fd2a334bbd.png">

<img width="499" alt="Снимок экрана 2020-11-05 102558" src="https://user-images.githubusercontent.com/70718269/98214508-a40f1600-1f57-11eb-92a0-9d19efc405f2.png">

Чтобы попробовать восстановить удаленные файлы я взял какую то флешку. На ней оказалась куча фоток, которые ,наверное, можно было удалять. 

<img width="482" alt="Снимок экрана 2020-11-04 115406" src="https://user-images.githubusercontent.com/70718269/98217343-70ce8600-1f5b-11eb-8055-33e4c4ceedb7.png">

Чтобы не портить файлы и отношения с родителями я создал: текстовик, документ, и скопировал одну фотку.

<img width="768" alt="Снимок экрана 2020-11-04 114805" src="https://user-images.githubusercontent.com/70718269/98217606-c86cf180-1f5b-11eb-9b52-04bb8a2dee42.png">

Затем я их удалил. Отсканировал флешку в рстудии и нашел даже больше удаленных файлов чем ожидал

<img width="956" alt="Снимок экрана 2020-11-04 120139" src="https://user-images.githubusercontent.com/70718269/98218149-7a0c2280-1f5c-11eb-9c82-7cade6a1ec83.png">

<img width="478" alt="Снимок экрана 2020-11-04 120630" src="https://user-images.githubusercontent.com/70718269/98218270-a162ef80-1f5c-11eb-9677-2038a05e28db.png">

Но потому, что почти все удаленные файлы весят больше чем 256кб, я смог восстановить только какие то фрагменты.

<img width="598" alt="Снимок экрана 2020-11-04 122009" src="https://user-images.githubusercontent.com/70718269/98288009-3f83a380-1fb7-11eb-9ff0-7c7822d41681.png">

Вот что мне удалось восстановить:
<img width="824" alt="Снимок экрана 2020-11-04 125952" src="https://user-images.githubusercontent.com/70718269/98288788-6f7f7680-1fb8-11eb-80c6-46e78e6fcba3.png">

Фотку я смог увидеть только в предпросмотре :/
<img width="334" alt="Снимок экрана 2020-11-04 122421" src="https://user-images.githubusercontent.com/70718269/98289190-e1f05680-1fb8-11eb-9ea8-51b906523811.png">

***
***
#4 практика 
***
Шифрование дериктории с помощью EFS:
Я создал папку на диске C и засунул туда текстовик, зашифровал папку и попытался открыть с другого пользователя

![L1b-hD6rwDs](https://user-images.githubusercontent.com/70718269/99520037-ac2d7380-29a3-11eb-9585-e5487d8f0526.jpg)

![NBi9MzCBfks](https://user-images.githubusercontent.com/70718269/99520738-894f8f00-29a4-11eb-9b46-c2dd31988fbe.jpg)
***
Экспорт сертификата:
Чтобы получить доступ к документу с другого пользователя я экспортировал ключ на флешку

![cicApTXYM5s](https://user-images.githubusercontent.com/70718269/99522285-7e95f980-29a6-11eb-8cee-b7e2f0e9d0be.jpg)

![sV3BsLN4Zvc](https://user-images.githubusercontent.com/70718269/99522745-13005c00-29a7-11eb-9e2f-2d51a4264148.jpg)

![k_tuwuajTPM](https://user-images.githubusercontent.com/70718269/99522197-658d4880-29a6-11eb-97e7-fd7216470576.jpg)

успешно
***
cipher:
я снова создал текстовик на флешке,

![-GZ8HnuqfpE](https://user-images.githubusercontent.com/70718269/99523073-91f59480-29a7-11eb-98f2-fc0c2fc21ba1.jpg)

открыл консоль и зашифровал файл

![gDM-h5mTAJ0](https://user-images.githubusercontent.com/70718269/99523861-b1d98800-29a8-11eb-8fba-ee9a0ba49af3.jpg)

затем создал резервную копию сертификата

![JILq--FiY-Q](https://user-images.githubusercontent.com/70718269/99523399-147e5400-29a8-11eb-815a-09c244b7cbd8.jpg)

Попробовал открыть с другого пользователя

![AtvFnYHTgdo](https://user-images.githubusercontent.com/70718269/99524026-e51c1700-29a8-11eb-9fa4-fa8e2a4f9ea2.jpg)

успешно
***
bitlocker:
я взял пустую флешку и снова создал текстовик

![s6kuw7rcO4U](https://user-images.githubusercontent.com/70718269/99524273-43e19080-29a9-11eb-8e3f-da3bd10b4a9d.jpg)

включил бит локер

![juvItyGOaYA](https://user-images.githubusercontent.com/70718269/99524369-64114f80-29a9-11eb-86ef-b22b7b9ccd65.jpg)

![bG7CuZJi2Sg](https://user-images.githubusercontent.com/70718269/99524593-b3f01680-29a9-11eb-9844-dc2589cb2541.jpg)

![yZfdqEqrRa4](https://user-images.githubusercontent.com/70718269/99524650-c9fdd700-29a9-11eb-8ca6-e2969edb4ec3.jpg)

вся флешка успешно зашифрована

![Ll0gQHCqV70](https://user-images.githubusercontent.com/70718269/99524788-003b5680-29aa-11eb-8313-92b791aa7ad4.jpg)

На другом ноутбуке-
<img width="370" alt="Снимок экрана 2020-11-17 223115" src="https://user-images.githubusercontent.com/70718269/99525004-4d1f2d00-29aa-11eb-8300-5a80d7238874.png">
***
veracrypt:
установил, открыл, поводил мышкой, создал контейнер и поместил туда файл с фамилией

<img width="418" alt="Снимок экрана 2020-11-18 113450" src="https://user-images.githubusercontent.com/70718269/99525392-ce76bf80-29aa-11eb-916b-696572cb4a12.png">
<img width="415" alt="Снимок экрана 2020-11-18 113746" src="https://user-images.githubusercontent.com/70718269/99525438-dc2c4500-29aa-11eb-8e6b-500fcf0c62fb.png">
<img width="501" alt="Снимок экрана 2020-11-18 114231" src="https://user-images.githubusercontent.com/70718269/99525485-ef3f1500-29aa-11eb-9fbc-4d57a1b60e5e.png">
<img width="502" alt="Снимок экрана 2020-11-18 114348" src="https://user-images.githubusercontent.com/70718269/99525540-01b94e80-29ab-11eb-8734-7b2daa804492.png">
<img width="503" alt="Снимок экрана 2020-11-18 114727" src="https://user-images.githubusercontent.com/70718269/99525637-27deee80-29ab-11eb-976b-8f3818178f05.png">
<img width="506" alt="Снимок экрана 2020-11-18 114817" src="https://user-images.githubusercontent.com/70718269/99525694-3b8a5500-29ab-11eb-8b19-8b65ad22ebf5.png">
Вроде все получилось, пароль: 123456
***
***
#Практика 5

***
Определение типа hash:

Я установил утилиту и посмотрел хэш пароля

![2](https://user-images.githubusercontent.com/70718269/100166168-1b87f380-2ecd-11eb-9a8f-a83b855f9841.png)

$6 перед солью и самим хэшем показывает тип шифрования и означает, что хэш типа SHA-512

Чтобы в этом убедится, я ввел hashid  –m ‘хэш’

![3](https://user-images.githubusercontent.com/70718269/100166222-3c504900-2ecd-11eb-9ca1-b927196ffbb3.jpg)


Создание hash в Linux:

Создание нового пользователя

![4](https://user-images.githubusercontent.com/70718269/100166262-512cdc80-2ecd-11eb-8843-4186dc579bef.png)
![пользователи](https://user-images.githubusercontent.com/70718269/100167029-22176a80-2ecf-11eb-8db2-cf5f7f5a1661.png)

Изменение хэша пароля нового пользователя

![5](https://user-images.githubusercontent.com/70718269/100166281-5f7af880-2ecd-11eb-90a2-e78f2f5840e4.png)

Я узнал соль и рассчитал хэшированный пароль 

![6](https://user-images.githubusercontent.com/70718269/100166339-8afde300-2ecd-11eb-8095-7cb6199e05ce.png)
![7](https://user-images.githubusercontent.com/70718269/100166383-ad8ffc00-2ecd-11eb-8159-0a7f27be9364.png)


Проверка контрольных сумм:

Скопировал файл /etc/group в домашнюю папку с помощью команды cp и проверил, затем посмотрел и сохранил контрольную сумму

![8](https://user-images.githubusercontent.com/70718269/100166749-7e2dbf00-2ece-11eb-98e6-857bb4ace8a0.png)

Потом удалил первую строку в group

![9](https://user-images.githubusercontent.com/70718269/100166772-8be34480-2ece-11eb-9800-b43eb063a87c.png)

И сравнил их 

![10](https://user-images.githubusercontent.com/70718269/100166788-9ef61480-2ece-11eb-9c3e-aeb6a96a724b.png)

Файл поврежден, отлично


Шифрование данных с помощью пароля:

Я создал файл и зашифровал

![11](https://user-images.githubusercontent.com/70718269/100166891-d82e8480-2ece-11eb-86b7-fddeb0289ea2.png)

Тут вроде все


Шифрование с использованием ключей:

Создал ключ для предыдущего файла

![12](https://user-images.githubusercontent.com/70718269/100167055-3a878500-2ecf-11eb-8466-e6d3cbc44145.png)
![13](https://user-images.githubusercontent.com/70718269/100167082-4a06ce00-2ecf-11eb-8c88-4e70f4f73892.png)

Затем импорт и экспорт

![14](https://user-images.githubusercontent.com/70718269/100167105-5a1ead80-2ecf-11eb-9855-c09bb3f64cfc.png)

Осталось указать доверие

![15](https://user-images.githubusercontent.com/70718269/100167135-6dca1400-2ecf-11eb-8abd-e5096587b2aa.png)


Подписи и шифрование:

Я создал текстовик testing и подписал

![16](https://user-images.githubusercontent.com/70718269/100167348-dc0ed680-2ecf-11eb-89ed-9c91ae1dcbf2.png)
![17](https://user-images.githubusercontent.com/70718269/100167351-dd400380-2ecf-11eb-9da1-031ae3debf82.png)
![18](https://user-images.githubusercontent.com/70718269/100167424-137d8300-2ed0-11eb-8aac-81691be709ae.png)


Письмо:

Установил мозилу, помучался со своей почтой и создал новую

![2 2](https://user-images.githubusercontent.com/70718269/100167724-bb934c00-2ed0-11eb-8810-86d00c0141d6.png)

Вроде создал открытый ключ 

![2 4](https://user-images.githubusercontent.com/70718269/100167871-1b89f280-2ed1-11eb-8d54-7a9c6583d1b9.png)
![Inked2 6_LI](https://user-images.githubusercontent.com/70718269/100167889-2b093b80-2ed1-11eb-9286-262348f60413.jpg)

Загрузил его

![2 7](https://user-images.githubusercontent.com/70718269/100167929-45431980-2ed1-11eb-9799-f8e7317fc389.png)

Подтвердил на почте

![2 8](https://user-images.githubusercontent.com/70718269/100167961-5a1fad00-2ed1-11eb-86fd-38fd535dbb8f.png)

И вот он

![2 9](https://user-images.githubusercontent.com/70718269/100168002-71f73100-2ed1-11eb-854d-808c2add9e5c.png)

Осталось только отправить письмо

![2 10](https://user-images.githubusercontent.com/70718269/100168199-d6b28b80-2ed1-11eb-96df-5b8d67f33114.png)
![последний](https://user-images.githubusercontent.com/70718269/100168231-e7fb9800-2ed1-11eb-9cd3-989af667f0c4.png)








