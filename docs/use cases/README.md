# Модель прецедентів

В цьому файлі необхідно перелічити всі документи, розроблені в проекті та дати посилання на них.



## Відношення узагальнення

"Користувач" as User and "Адміністратор" as Admin

@startuml

actor "User" as User
actor "Admin" as Admin

usecase "<b>USR.REG</b>\nРеєстрація" as USR.REG
usecase "<b>USR.LOG</b>\nАвторизація" as USR.LOG
usecase "<b>USR.QRY_CR</b>\nСтворення\n запиту" as USR.QRY_CR
usecase "<b>USR.QRY_ED</b>\nКерування\n запитом" as USR.QRY_ED
usecase "<b>USR.QRY_EXP</b>\nЕкспорт\n результатів" as USR.QRY_EXP
usecase "<b>USR.QRY_VIS</b>\nВізуалізація\n результатів" as USR.QRY_VIS
usecase "<b>USR.HELP</b>\nДопомога\n адміністратора" as USR.HELP

User -l-> USR.REG
User -u-> USR.LOG
User -u-> USR.QRY_CR
User -u-> USR.QRY_ED
User -u-> USR.QRY_EXP
User -u-> USR.QRY_VIS
User -r-> USR.HELP

usecase "<b>ADM.QRY_SRC</b>\nКерування\n джерелами" as ADM.QRY_SRC
usecase "<b>ADM.USR_RIGHTS</b>\nКерування правами\n користувача" as ADM.USR_RIGHTS
usecase "<b>ADM.HELP</b>Допомога\n адміністратора" as ADM.HELP

Admin -d-> ADM.QRY_SRC
Admin -d-> ADM.USR_RIGHTS
Admin -d-> ADM.HELP

Admin -u-|> User

@enduml



## Структурування моделі варіантів використання для користувача

@startuml

actor "User" as User

usecase "<b>USR.REG</b>\nРеєстрація" as USR.REG
usecase "<b>USR.LOG</b>\nАвторизація" as USR.LOG
usecase "<b>USR.QRY_CR</b>\nСтворення\n запиту" as USR.QRY_CR
usecase "<b>USR.QRY_ED</b>\nКерування\n запитом" as USR.QRY_ED
usecase "<b>USR.QRY_EXP</b>\nЕкспорт\n результатів" as USR.QRY_EXP
usecase "<b>USR.QRY_VIS</b>\nВізуалізація\n результатів" as USR.QRY_VIS
usecase "<b>USR.HELP</b>\nДопомога\n адміністратора" as USR.HELP

User -d-> USR.REG
User -d-> USR.LOG
User -u-> USR.QRY_CR
User -u-> USR.QRY_ED
User -d-> USR.QRY_EXP
User -d-> USR.QRY_VIS
User -d-> USR.HELP

usecase "<b>USR.QRY_CR1</b>\nКастомізація\n за власними\n параметрами" as USR.QRY_CR1
usecase "<b>USR.QRY_CR2</b>\nЗа сталим\n шаблоном" as USR.QRY_CR2
usecase "<b>USR.QRY_ED1</b>\nРедегування\n параметрів\n запиту" as USR.QRY_ED1
usecase "<b>USR.QRY_ED2</b>\nОновлення\n результатів\n запиту" as USR.QRY_ED2
usecase "<b>USR.QRY_ED3</b>\nВидалення\n запиту" as USR.QRY_ED3

USR.QRY_CR1 ...> USR.QRY_CR :extends
USR.QRY_CR2 ...> USR.QRY_CR :extends
USR.QRY_ED1 ...> USR.QRY_ED :extends
USR.QRY_ED2 ...> USR.QRY_ED :extends
USR.QRY_ED3 ...> USR.QRY_ED :extends
@enduml



## Структурування моделі варіантів використання для адміністратора

@startuml

actor "Admin" as Admin

usecase "<b>ADM.QRY_SRC</b>\nКерування\n джерелами" as ADM.QRY_SRC
usecase "<b>ADM.USR_RIGHTS</b>\nКерування правами\n користувача" as ADM.USR_RIGHTS
usecase "<b>ADM.HELP</b>\nДопомога\n адміністратора" as ADM.HELP

Admin -u-> ADM.QRY_SRC
Admin -d-> ADM.USR_RIGHTS
Admin -d-> ADM.HELP

usecase "<b>ADM.QRY_SRC1</b>\nВидалити\n джерела" as ADM.QRY_SRC1
usecase "<b>ADM.QRY_SRC2</b>\nРозширити\n об'єм\n джерел" as ADM.QRY_SRC2
usecase "<b>ADM.USR_RIGHTS1</b>\nСхвалити\n запит по\n допомогу" as ADM.USR_RIGHTS1
usecase "<b>ADM.USR_RIGHTS0</b>\nВідхилити\n запит по\n допомогу" as ADM.USR_RIGHTS0
usecase "<b>ADM.HELP1</b>\nДодати\n додаткові\n права" as ADM.HELP1
usecase "<b>ADM.HELP0</b>\nОбмежити\n права" as ADM.HELP0

ADM.QRY_SRC1 ...> ADM.QRY_SRC :extends
ADM.QRY_SRC2 ...> ADM.QRY_SRC :extends
ADM.USR_RIGHTS1 ...> ADM.USR_RIGHTS :extends
ADM.USR_RIGHTS0 ...> ADM.USR_RIGHTS :extends
ADM.HELP1 ...> ADM.HELP :extends
ADM.HELP0 ...> ADM.HELP :extends

@enduml

## Основні сценарії

### Користувач

##### USR.REG: Створення нового облікового запису

![Scen1](http://www.plantuml.com/plantuml/png/ZL8rGhGn4Es_KwpK_myjxb3ZLBYxLhYxkyC9rdqtUuMP6_6Ih7iycPdtCbA_iZgqlBesDsiO9jKsw8q4xv2VTtcFzyb9TZxUK4BTb47AlT94JdH1RlB3ui84Omy_AFCT61_n4mKemaycQDZbeIf1zQjfo4DXic-aWqQ10YHoyXFly3K_Q1uFK3mAhWIU5CJvXTKnq_BKnEIgoJe-NewM8gmUhgKxybEGGdp5nv800DULrMN3jUbgtPqT_pjQsWPQ-Z9aO_EZYiD8z-8NtZbbG84B3mGvGF448e5dFmLCvCDdep8EwfZc91J2vC_Zg1PgPsENgWpoRya2RJVsC7XL48FPwPMqKJmA4rvZ_ut7m8GDA9Wk4faEgCSK5tY_ggGwgjGsS1I1EU5zdLmyyGE5PIdn4rzLfHNTmcALKOyWerJ_0000)

#### USR.LOG: Авторизація користувача

![Scen2](http://www.plantuml.com/plantuml/png/XL8pOeH15Exd53_ge8rjErLiiufjsya9riOPldUZ38BrlcRuuQ5uSQb_OMbvUeenJSOgdX6cJNXfYxPf1tPOwM1LFggGW8XphWOxx0Z32Iz7d6eSxA9R2T_au7swXmyXkjVWX5LiylwalfGCN0Z2kXf5ob5Ek13YhrxQvIS_xT2j1d-yErZp8g2HBB32JjiA0KzAWWZOpEpIiBOmFZgsf9aZ8zay8Xxp1mfn3I_y2D0vXtABtEH5RdxMG67qjuwsripwfghUYkwOj-6P8Qd1eglu1gkeK8n7X9L7sj6Yir6bfNCDTess_Wifwfk-cKhI8oZXeaqwLCMnIzvR14K_1NjULETdv_9OCRVFv-KR)

##### QRY.SRCH: Запит на пошук та аналіз даних

![Scen3](http://www.plantuml.com/plantuml/png/ZLGrTbn14Cpt5FEUOqDgvWFOaPtOOcQ8nCpCB9tWyp9SeVj6gfwb-SiZs6sgwkg1BvDJxHDJqyD3aOZIQvQkASkB5ESbNkOLSidcZLa4YqiN6FOxHNTaayzB5ASKiayLnU380M9PKOPiXUzPtWHOKl6osBQuASNd55FaYudajVUb5fxoz1HGccoJtEIbUrwMHYdDAo7ILzKTyQeMXKpmWVYWc9ub5-G1_ZBYJ5PhboRUjpGTJEAY3ChxmglbPkfsKvJSN3d0JRqc2FGUmutUAIEXLkSjC_3Wys5cOIW0E83KOV37wyv3mKXhcRRalG_lKFKQ6PtgLXFzlNrJwaLFpnii8-r3nwT2_odCRAEu6Uy-lExu54xxzVll_vz_AlpT8rqQlyufKU6HAd93euAwBCL4DAz150Q1eUbq6t-wKFArnjRnNS3uSXHvLnW2CAn0tMuUjcMe63aKy2AsoAkwLxLsHjWLdujFelXsOTG0nZMfMplJLSUkMavHHFWQkBhrJLq48oOAzA7nqTV--z2BCZhsFl856ubtw1a0)

##### QRY.EXPRT: Експорт результатів

![Scen4](http://www.plantuml.com/plantuml/png/jLGrTXr14Cpt5FEUOqDgPaTcTc9c4aTYPcQMRl2PuGhLDrBrnqMn9jfjAXYurTBwgRcrxTzVopAbrO4r5AG7AUcLFkb7124Pxc2okaeDjlyh1fi88IQzI27BwWM390D5fAJF88-GGHmPfeiwc37fOI39sLcPa3w4YBE4oDKQWTqoE8jo2DcXxQZOOXjf8YVz3iWBNZuoeCXQQH0ZwdIrl41vUUBaaTTWngjSILmzb3VqORa-LAOKb-BeG22RgkI3bLyns6QFZYvG0cNAX2aPEa8U6PjyrHWnigHp58TVo_OqdVON6hhgvxHz_Mze_MQQV_tusMhEVVz-YSjMTktp3SnHOmPPQX-kcdhbsiNFDvnbpvw_-t3_hIl-xV_Nqlo0tJRgFFA88Av7IBVSvnWP5Lz0c9aGYrD81-vfRHUqBq2vTHRIBpnu_kZbCVGhW7tpoJ-4DBBSMnydcCiXfGUtjWvvY6ttoj_a2mORA221UFbOiHzvJJ54QaZLg5sjId3UaF8UZfJ6yuSpP04vbSQpEdNLyTGqD5wrRj4RFb1x)

##### QRY.ED: Редагування запиту

![Scen5](http://www.plantuml.com/plantuml/png/ZLGrOYj13Ett58RwG-qm7I2faYRCZ5MOcPcJ6vWPhY3TA4yByOnvp3FIezMwUMbvO75vPMRQC5pcMgCNol8MnNcRTtYNWkJdmpKvj9VPeFpskUYT_1JcROfJ2jLtBefX8mU87HTboEy2N8J2s0jPWDZCyALInhikFgOiQh8kx6Jv28L9sTr1kpJWbU87Yc4FLTX0stxTh-PlIozeqkHNrQf2wGDCS4PftjLK_Yssm7jc2ccBBvLNcuM137Xi2ydYi4H4NKrn8hh7F2XVWDSod2chnh5StJd0Fz4Zq1Aif7ocXAkdJq4NFmYEyE3RethyWDEIHlrrUjB5QtPkUSIrE34slkpoZex-nrBAwWSRwORYW4x1-w4Jgg_-ts2ZNjRPrTFNqLsmFp8xREANkTek6piBJ5nknNhnL2apPHftIPSPNKfKoSXGN13yoC2F7n7UiR_5wohog-4NWIQiEmD33HbdeeftwWm5fDOfqWUx1AYZJ1-y87ni8HDfme-Op1gbHJ56uA9Ek-ddvkkCPaIElueV)

### Адміністратор

##### ADM_HELP: Допомога адміністратора

![Scen6](http://www.plantuml.com/plantuml/png/ZL93baH14Dp_K-HxinujnpPFCBQr6zkspj2shX1veuwsyLbLaHcHakYrXny4zGXkFTOJFOKLPhtSCoHvRUzCRksaxUi5_p33hiTmmqVhDu6B1o5Id0X2v0eAx0Zo90W_NvkUDXW9jIT2Vlr0G3-YYaTaE8b4i9UfKT1E48nktOHFiyIjTB0BlBaPmToGnb--52pSyWkVFcQ8DOZa9rnRtvcLhSNvXHsfc9khuPK6DauruuzyJlZWZeJRM3tLd8ctTGvLzNODZexN5i5gih3PjPceS6v8-VkRNOHyHjc5ZlOpMk5eNtrm8C2QFOfUyu27QTM9TZn7v9Em5Guzqgie8pVqq3UoaO3LVsWmCYPlVQF120C0)

##### ADM.RIGHTS: Керування правами користувача 

@startuml

|Адміністратор|
start
:Виконує пошук\n користувача;
note right: USR_0:\n Шуканий користувач\n не існує;

|Система|
:Знаходить шуканого\n користувача;

|Адміністратор|
:Додає/віднімає\n відповідні права;
note right: USR.RIGHTS_0:\n Користувачу вже\n були надані/відняті права 
note right: ADM_0:\n Користувач є адміністратором

|Користувач|
:Отримує\n повідомлення;

|Адміністратор|
:Завершує взаємодію;
stop

@enduml

#### ADM.QRY_SRC: Керування об'ємом оброблюваних джерел

@startuml

|Адміністратор|
start
:Виконує пошук\n користувача;
note right: USR_0:\n Шуканий користувач\n не існує;

|Система|
:Знаходить шуканого\n користувача;

|Адміністратор|
:додає/обмежує\n відповідний об'єм\n джерел;
note right: USR.SRC_0:\n Користувачу вже були\n додані/видалені\n конкретні джерела 

|Користувач|
:Отримує\n повідомлення;

|Адміністратор|
:Завершує взаємодію;
stop

@enduml

## Виключні сценарії

#### USR.REG_EX: Відхилення запиту на реєстрацію

![Scen7](http://www.plantuml.com/plantuml/png/ZLB5GKKn4BodYjH1gg41_8QxkpjKyDsjXPcEc2J0z-S-bjsrOLl32xhSGftRtE4kYiZpSCtO_srvPNPfPU1znk8TUPI5kxF-XWuV_4EBbrP25Tu5gIq13lZ0HsV-dBwZ2ofe8xyshFafeiWeYhB5om5jDm0SvE16SfSAt8hmZjXDlvQWqvIFo9bKfD4LhgxKPnOzlIY5FdILioMjZWIqjkE0wjhub_ke3_n5JJwzeB7hi-GdrUB26PEXx6QmC1-1NqURkxoRdWuzRatBDhqhWtRJEpGSw15v57stU1GZ5VtQUIUAwXDNEJW-ymlE_000)

#### USR.LOG_EX: Відхилення запиту на авторизацію

![Scen8](http://www.plantuml.com/plantuml/png/fPB5MKKn58JtgUBKmQs61l0TxkxkKC6xxjB2J4T4S8UNLVGV-I9sJE42BUUGSvuBN4G8dwjJIfx7-CJWsCIhzO3W03bAj6Yuo2E1Zv0B3e8CFbTumXrFFV7l7Hi9QlXJRqctIFIp1A5-CiTTGulXQ_29z-hYwpTMF4IBM6CNk2Neq9htUgD5ZKhJ6WtO5QxRMwsuKouZVtLgdAApZ4NHU_wNETGlYbAlGzrmmJ9gMy-N_j1nhdzthqlwkl6F9ayDqBJFDMSpjDGZrAOrntxz2OP7FFK0)

#### QRY_EX: Відхилення запиту користувача на обрані маніпуляції над обраним запитом

![Scen9](http://www.plantuml.com/plantuml/png/lPB5cTqm58Ntha9rnDMaWV0kP0WECsC5XaTcj_2VZkQJFSoiZV0UqZNT-COMZJmo-GeKaXBhxpV7d8xFNzv--d9k_yQmIynGFXabiLOC4s9QCWM6cjZGaCWZfjQQeUeNj0efDQy_MjDwzv3XkQTaLEUGQAXSvqJZOQ-FaKNxTb7DdW9vjbhX1ItkkMSNAvR8D4zgrTYAcX653K6UNIcmShiuPix1ARm9qEAHqZ0awujQ6bAjCRGkA1bHKslUw7_tgZ7zhNwJdRizpzNbyxJid7jyi7Dpa3UQe9NtIXREntrxArnqiavCoaYU_lLUKeki5IgRlzOqvrxeyFSVNES8)

