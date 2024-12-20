# Модель прецедентів

## Діаграми прецедентів бізнес акторів

**Діаграма прецидентів _(діаграма use case_)** - діаграма, що показує різноманітні сценарії взаємодії 
між акторами (користувачами) та прецидентами (випадками використання). [[1]]((https://lvivqaclub.blogspot.com/2008/10/use-case-uml-diagram.html)) [[2]](https://dou.ua/forums/topic/40575/)

<center>
<span id="GeneralUseCase"></span>

### Діаграма use case для всіх бізнес акторів

![](https://www.plantuml.com/plantuml/png/bLF1RjDG4BpxArRDEH5DtQ9UK17Y4pWZAx6X4csGxKeSEAGk99U8vW11ge02_O6G9jI4sFp2x1ynpyPF3fKYY1J9ipipVljsV135NXYV73rp7AyJzqBPmWLoxIFLKqtq33DCTRWbNYIF8Z-KHX3utNtNaiUOOwKJP3ef17tI4sDGIEvtZmwFfR7l1jj1O3NliDHJ_C92-veKl8SldljXB0tVwmI1vpWdaT_n8f_SpsIzjSu3lkLSa277ZFzhv8BbxUDYMXxumUFjcjKOCqrACcwisMPzkwR_P1J8A9WA5GlSaFzJHpJbp6pD13d7IYiZP3ggZ7PgHfTKv_gQv3c-qoSZyVoMrXGhjLjJVz6419wvKjhxqFUYhuhE2kb6lztr6yQSXEiwKSmw-N2cRtJuFyvxzJb9-CORcc1fh_iVRUuwJX6tPlDUkSOwQZjE4QmAxwp3tNMujmxfNARDgl_2RetmaXM-k7Ams0aFdpoD9UZrOYBvyyCO6QPcO4qus90enG_Xb1oP9RPQWW_5tXScEMoPDUg0q9IoCaOjwuYF-8ehN0akS8c1iBjgOT1Y22PbS1dR4PRbjs1bPAV6gDc-qtQBgd_ShKvxm6T-xxy1)
```plantuml
@startuml

actor "Користувач" as User #ffed94
actor "Адміністратор" as Admin #94f1ff
actor "Експерт" as Expert #eacffa

usecase "Реєстрація нового користувача" as UC_1
usecase "Авторизація користувача" as UC_2
usecase "Оцінка результатів опитувань" as UC_3
usecase "Проходження опитування" as UC_4
usecase "Створення нової форми опитування" as UC_5
usecase "Редагування існуючої форми опитування" as UC_6
usecase "Публікація форми опитування" as UC_7

User --> UC_1
User --> UC_2

Admin --> UC_3
Admin --> UC_5
Admin --> UC_6
Admin --> UC_7

Expert --> UC_3
Expert --> UC_4

Expert --|> User
Admin --|> User

right footer
        Аналітичний портал. Модель прецедентів.
        НТУУ КПІ ім.І.Сікорського
        Киів-2024
    end footer
@enduml
```

</center>




### Діаграма use case для Користувача
![](https://www.plantuml.com/plantuml/png/VPFDwjD05CNtVOfBNNUmiHkBIC5dS2sXcMYXDf8FT5aZL1Ub2v4MYb9gNo341ci_qbSuyqRUJ18oHFmF37JktD-TS-vjHa5e-s7qTjeXNlOuz7pgOejSpN5I7rMiFY55eZvtoGxePI1zUkIwqdaww6WY2kJO3YGpUnKZhRWO9qA2CnB6RoekuHUl-gBVeWv8rHf_IYBz3sGHjR2lEE78oPS77tlIrhZXd3aozKqxcrVUOkrqIVYDXBXiZZllA-zVx6T5nL5zAT8C7-oahKcj6RunbjQgxlgz71UrDDnKJMZXkmBNFSoOELObEBHMAyEI2UjnzA9tlUULA2FgJrw_2UiBoxXmlFSpZfiDgXsH47Kb6ieFePmvGPDW5GbJwOPrajLAglJHC-6BwaJ3oMmyZHmPDAgrCd8zBvG-1yg5xyZPT5QqYlkcfxH0faCyK-vDIZZ_-xT48feQF_0J1nm8M-om88Qk0Wk1FV_IR35cdCl1DjYMIswGzgp7ra17sPAfhpFY07yYVm40)
```plantuml
@startuml
    actor "Користувач" as User #ffed94

    usecase "Створити акаунт" as UC_1.1
    usecase "Увійти в акаунт" as UC_1.2  
    usecase "Видалити акаунт" as UC_1.3

    usecase "Зареєструватись за допомогою пошти" as UC_1.1.1

    usecase "Відновити пароль" as UC_1.2.1
    
    usecase "Підтвердити дію" as UC_1.3.1
    
    User -up-> UC_1.1
    User -right-> UC_1.2
    User -down-> UC_1.3

    UC_1.1.1 ..> UC_1.1 :extends
    UC_1.2.1 .left.> UC_1.2 :extends
    UC_1.3.1 <.r. UC_1.3 :includes
    
    right footer
        Модель прецедентів користувача.
        НТУУ КПІ ім.І.Сікорського
        Київ-2024
    end footer
    
@enduml
```



### Діаграма use case для Адмiну
![](https://www.plantuml.com/plantuml/png/dPL1RjD058RtESMeB5ZLeZFTK25Kn1dO8Q4eSI1IcbIn8rWsZHGs5KK8fL95gKelu8QOM8sJNk6V6_6UwycO8SQetTJn_F_t_dcJlDaFmde_71nqQlL6sEkBBNp63AcUOAadUgYFzH4YVOoLFjeIzK2yQ1wqk-BHqztMJgjLgmdw6mH-enxuP3t3zB4-nJnp9EG-4PWBtB8RIKOROKgh7n4ZpNYlNhxPyNOSpbSgVPPP8p97P5eIC4AAHBpkRk9HtgdboLBU2dT8Z0rBufuorLgLO_sknzmBZY6eQ8mvUHVwXFCGXyfkX5hWRWPqgRZ9-ve8FIJxIW-9TKCPJGjlzSX2_cxH5vBFk0CKwHUId9Id6kaXzsdA6eRVF-b94UZsw08HIoZD8WzcdVG_fTUnkpVJBZSR4l94MEIvYgTOSdw8B5LktYoM7EUXIBafw1MnfhcJg1KdgIXNnKOh_B9oNnM4pVs-P4osbPYsCZCeFirFVxHLFiYeo6ZhvXDWkzbxtzr-Rdw_XOL---sxqAp8uah7RwqNL75XS4YltL-B-U8BRt3ecK9Yp_yG-jrcK9H8uJ7wto8bF4vMfh9IoIMDIXPKLY1B1LQbYXXLK5c1h1Ae4e4JLufddcV3xxMxZSwWwGVb8baKkR6bibBbyafKyhzKob6jIsSd8rgzNkZtroluXXLcY7dS2jpnzDLZnDchfPczKTbjXOWdQvAFo1I9Py4N-85hN0kSun9ZGVRK4nXxkAB7R9JmtSLF-8cLzPqJZ-wuRVb4tdzHwJnCwje-VQ1xz3S0)
```plantuml
@startuml
actor "Адміністратор" as Admin #94f1ff

    usecase "Зв'язатись з користувачем" as UC_1.1
    usecase "Дії з акаунтами \nкористувачів" as UC_1.2
    usecase "Дії з опитуваннями" as UC_1.3
    usecase "Оцінка результатів опитування" as UC_1.4
    
    usecase "Обрати спосіб зв'язку" as UC_1.1.1
    usecase "Відстежити статус \nвідповіді" as UC_1.1.2
    usecase "Надіслати повідомлення" as UC_1.1.3
    
    usecase "Видалити акаунт \nкористувача" as UC_1.2.1
    usecase "Відновити акаунт \nкористувача" as UC_1.2.2
    
    usecase "Створити опитування" as UC_1.3.1
    usecase "Видалити опитування" as UC_1.3.2
    usecase "Відновити опитування" as UC_1.3.3
    
    usecase "Підтвердити дію" as UC_1.2.12
    usecase "Підтвердити дію" as UC_1.3.123
    
    Admin -down-> UC_1.1
    Admin -right-> UC_1.2
    Admin -left-> UC_1.3
    Admin -up-> UC_1.4
    
    UC_1.1.1 .up.> UC_1.1 :extends
    UC_1.1.2 .left.> UC_1.1 :extends
    UC_1.1.3 .right.> UC_1.1 :extends
    
    UC_1.2.1 ..> UC_1.2 :extends
    UC_1.2.2 ..> UC_1.2 :extends
    
    UC_1.3.1 ..> UC_1.3 :extends
    UC_1.3.2 ..> UC_1.3 :extends
    UC_1.3.3 ..> UC_1.3 :extends
    
    UC_1.2.12 <.. UC_1.2.1 :includes
    UC_1.2.12 <.. UC_1.2.2 :includes
    
    UC_1.3.123 <.. UC_1.3.1 :includes
    UC_1.3.123 <.. UC_1.3.2 :includes
    UC_1.3.123 <.. UC_1.3.3 :includes
        
    right footer
        Модель прецедентів адміністратора системи.
        НТУУ КПІ ім. І.Сікорського
        Київ-2024
    end footer

@enduml
```




### Діаграма use case для Експерта
![](https://www.plantuml.com/plantuml/png/XPFFpj905CNtVOh9vvg9N-EA449YV0JNfYbJ9K4W_PEmX9eqBeYkX8IeH7c1Mjg82EKLpdqZRuj3AMXeDpDpp-_Sa-bjn_Cjrm_UzWtBzeUkUC0dx6YA8pAQKFWWB4-y68-Kwuidoh8Tnp8CmK_WATlo5EjND46ENnHYAv0pkAMGtY51Z0CEzB6qUFdyrQDyl2A_KaHp5kqG2pR9y9EvtpHZgvX2BYLt3CthB0lM96NozqpTJyJlZSE-oAJfX3SfE-Id5SqkMRDaRwwZq8Md64YrKKfp-b31_sxzesGoR0gcred5kfV-78s-Sln6-w-aLd5xhzzmgNP9kgsGmKXgIZJLs5U3hdSfCONyZw1cnCLMIrQ-pTx0xWTTLVSg6hRRvstTx-nP1XRESEWhzrp1P-H8aHKZ8N0iReOYPENHGSz7TZcjY6L5Vy5thB4MM6A5IB1yBmKYYM-yt25dO4gpOeKDyefROaiB90tpgVciFEMuEfhHuGt_B7y0)
```plantuml
@startuml
actor "Експерт" as Expert #eacffa

    usecase "Пройти опитування" as UC_1.1
    usecase "Оцінка результатів опитування" as UC_1.2

    usecase "Завершити опитування" as UC_1.1.1
    usecase "Змінити відповідь" as UC_1.1.2
    
    usecase "Підтвердити дію" as UC_1.1.1.1
    usecase "Зберегти" as UC_1.1.2.1
    
    Expert -left-> UC_1.1
    Expert -right-> UC_1.2

    UC_1.1.1 .up.> UC_1.1 :extends
    UC_1.1.2 ..> UC_1.1 :extends
    
    UC_1.1.1.1 <<. UC_1.1.1 :includes
    UC_1.1.2.1 .>> UC_1.1.2 :extends
        
    right footer
        Модель прецедентів експерта.
        НТУУ КПІ ім. І.Сікорського
        Київ-2024
    end footer

@enduml
```

## Діаграми діяльностей


### Процес 1: Реєстрація нового користувача
| Поле                | Значення                                                                                  |
|---------------------|-------------------------------------------------------------------------------------------|
| **ID**              | userRegistration                                                                         |
| **Назва**           | Реєстрація нового користувача                                                            |
| **Учасники**        | Користувач (Адміністратор, Експерт), Система                                                                      |
| **Передумови**      | - Користувач не має облікового запису. <br> - Користувач має доступ до інтерфейсу реєстрації. |
| **Результат**       | Користувач успішно зареєстрований у системі.                                            |
| **Виключні ситуації**| Exception 1.1 - Неправильні або неповні дані.<br> Exception 1.2 - Проблеми з сервером.<br> Exception 1.3 - Користувач вже зареєстрований. |
| **Основний сценарій** | 1. Користувач відкриває форму реєстрації.<br> 2. Вводить ім'я, прізвище, email та пароль.<br> 3. Підтверджує введений пароль.<br> 4. Приймає умови використання.<br> 5. Натискає кнопку "Зареєструватися".<br> 6. Система надсилає підтвердження на вказаний email.<br> 7. Користувач підтверджує реєстрацію через email. |


![](https://www.plantuml.com/plantuml/png/hLFDYXD14BxtKpJPguXHK74kwy4ty0M6R6STJ2PXqWjxo64tWwo2x80C4Ro8Rz2E6OqJPto5gZVogsvO6JGh0Gz9ggg_-kghdnmlR9pPi-b4BUa3TNn1Mxxa5UTKaUEhfVBlQl4oIUTn5a_rYHd7PnFxt9pRfvFaD9sQrEeHlaoczd4y-LjOKukVbGIfWLNwW1xGUtB0rbnwz4N01o0NWsWVspToz9Cwk2rVWurplA-5j4RqCx_YDMtmXf30Tbn447na7evZCrhIfy07y0zoaDmFI4ujggZYDJGLNDxHV4LR3UsTVsY0RQdJ4531tU0ZnM0uCIALpgpHMNBwmkgZyVZnyD4zzUnyPEOscQLwU7VOynxqlFjAcVH42uCwG9hpWyrHVeNv-145EP1yhP6n2xgHtI4Omah6mwz1Bnw_eThFK8Fy4amvb_zkvKRjVpa9s906MGtdk8-FiaYWAj_s1cXa30vPPl-yGXavd2rzrt8hj4E9vdSed1OO8ELFrUIY_Jjf9HMM0nOdTzFI5pb1gU1dAwiBNKQtJEoTD2xwFDzN6H00Rm4hRYDSsDbS7MCZ-9V_0W00)
```plantuml
@startuml
|Користувач|
start
skinparam defaultTextAlignment center

|Користувач|
:Користувач натискає на "Зареєструватися";
:Користувач заповнює усі необхідні поля;

|#e6faec|Система|
:Система перевіряє, чи коректно введені дані;
note right #ff8170
Exception 1.1
Exception 1.3
Exception 1.2

end note

:Система перевіряє, чи акаунт з заданою електронною 
поштою ще не існує;
note right #ff8170
Exception 1.1
end note

|Користувач|
:Користувач натискає на кнопку "Підтвердити";

|#e6faec|Система|
:Система реєструє новий обліковий запис користувача;
:Система перенаправляє на головне вікно;

|Користувач|
:Відображається головне вікно;
stop
@enduml
```
### Процес 2: Вхід користувача в систему
| Поле                | Значення                                                                                  |
|---------------------|-------------------------------------------------------------------------------------------|
| **ID**              | userLogin                                                                                |
| **Назва**           | Авторизація користувача                                                                   |
| **Учасники**        | Користувач (Адміністратор, Експерт), Система                                                                      |
| **Передумови**      | - Користувач має обліковий запис.<br> - Знати свої облікові дані (email і пароль).       |
| **Результат**       | Користувач успішно увійшов у систему.                                                   |
| **Виключні ситуації**| Exception 2.1 - Неправильні облікові дані.<br> Exception 2.2 - Забутий пароль.<br> Exception 2.3 - Проблеми з доступом до сервера.<br> Exception 2.4 - Користувач не зареєстрований. |
| **Основний сценарій** | 1. Користувач відкриває сторінку входу в систему.<br> 2. Вводить email та пароль.<br> 3. Натискає кнопку "Увійти".<br> 4. Система перевіряє дані.<br> 5. У разі успіху, користувач отримує доступ до свого профілю.|



![](https://www.plantuml.com/plantuml/png/TL91Ji905DtFAIPXQunWeePkSE4Dl403Ksni2ob3mgABOctS4DqO5kwC5oW8aHGBL_Z_HhufHD84GWBpt_l_lS-RQGsq7UgXxuc8FcZ3CQrup4-Sq9moVeb4oOl1enlqxT3sPKSvzj3JzsgaRpst6_WgqBADBnKAqJoc8MdEKrfGReWIUfU6DvqW2X29wKbfGulo27edGKlwvSGwgOiFPcW5S2ALRxkUn50cQOk66DoQ9vOGKKrTERPgH_HvqAKi4iqgOEQM7AF0nbZk3PjI3cS3vUWg08zBCxXcL60ujKJGqqg6RlT1ovhZtDIlByJTgAtwskq5id5UhrIDIdKfLD2HHi24zoNXbD4FJoKdo60BkvIJC-HHNRD0rw8C4Z-RVIZRif2OYe4z8zerlrhYrCKUpVG_0KuFoUvruGDijXl0wTk0EJQPbRUuH6jYuRtq-gA5VsNUr1y0)
```plantuml
@startuml
|Користувач|
start
skinparam defaultTextAlignment center

:Користувач відкриває сторінку входу в систему;
:Користувач вводить email та пароль;

|#e6faec|Система|
:Система перевіряє коректність даних;
note right #ff8170
Exception 2.1
Exception 2.2
Exception 2.3
end note

:У разі успіху, система надає доступ до профілю;

|Користувач|
:Користувач переходить до особистого кабінету;
stop
@enduml

```
### Процес 3: Оцінка результатів опитувань
| Поле                | Значення                                                                                  |
|---------------------|-------------------------------------------------------------------------------------------|
| **ID**              | surveyResultsEvaluation                                                                   |
| **Назва**           | Оцінка результатів опитувань                                                              |
| **Учасники**        | Адміністратор, Експерт                                                                   |
| **Передумови**      | Опитування завершено з достатньою кількістю відповідей для аналізу.                     |
| **Результат**       | Згенеровано звіт з результатами опитування.                                             |
| **Виключні ситуації**| Exception 3.1 - Відсутність відповідей для аналізу.<br> Exception 3.1 - Технічні проблеми з відображенням результатів.     |
| **Основний сценарій** | 1. Адміністратор відкриває інтерфейс для перегляду результатів опитувань.<br> 2. Обирає конкретне опитування для аналізу.<br> 3. Система агрегує та обробляє відповіді.<br> 4. Генерується звіт з результатами опитування.<br> 5. Адміністратор може завантажити звіт або надіслати його на електронну пошту.|


![](https://www.plantuml.com/plantuml/png/bL9BRk904DttALfYFpFCI3CZl64MSuDSm88siG86cKPYuOMniqGYYX9MKQJSW0y6yx6vGjMDyhf1YWYhB6nrFTNxT5NN-zeDzQ3J5X4zq8eEFAM2fppYX6EQSK8bnz_fcNOyeYDb77CI2KiI_Ji_wBcXsv5DvRc3jhvHG_slxRU2ZWgqRE2dGY5gz0ZH5HHYoca1qITfNH8hTqyPRNaaJ-eebhJd2QqubRRSS0fWZ6wa0MyXgKHlZY8rQX0QEp1vfJd0sChJ3Zs5TSn0B2Yx8e4sSOI8Akgtvwf6H6-Kcrl3yK2p288NW0HdUOh7AHnC7ACv1uQ_YMny5_QcHq3sn5D715sjPEYtRhMiUDxVwfyVul-meNhQxmRorxVgHVLJgA0f3KLS9rZYKDYPcGIqCHwSu70zA7pWv8xuqbfhz6B71sf9QzgRTPr9O-CtEy_RgA_DC2d_Y05iJkNdDHQSsZQxZprwjbGuU3_TdgZZgdXuxm00)
```plantuml
@startuml
|Адміністратор/Експерт|
start
skinparam defaultTextAlignment center

:Відкриває інтерфейс перегляду результатів опитувань;
:Обирає конкретне опитування;

|#e6faec|Система|
:Система агрегує та обробляє відповіді;
note right #ff8170
Exception 3.1
Exception 3.2
end note

:Система генерує звіт з результатами;

|Адміністратор/Експерт|
:Має можливість завантажити звіт або переглянути онлайн;
stop
@enduml

```
### Процес 4: Проходження опитування

| Поле                | Значення                                                                                  |
|---------------------|-------------------------------------------------------------------------------------------|
| **ID**              | surveyParticipation                                                                      |
| **Назва**           | Проходження опитування                                                                   |
| **Учасники**        | Експерт, Система                                                                         |
| **Передумови**      | - Створено опитування, доступне для участі.<br> - Експерт отримав доступ до опитування. |
| **Результат**       | Експерт успішно пройшов опитування, відповіді збережено у системі.                      |
| **Виключні ситуації**| Exception 4.1 - Проблеми з доступом до опитування.<br> Exception 4.2 - Неповне завершення опитування.                   |
| **Основний сценарій** | 1. Експерт відкриває доступне опитування.<br> 2. Ознайомлюється з питаннями.<br> 3. Відповідає на питання.<br> 4. Завершує опитування, натискаючи "Завершити".<br> 5. Система зберігає відповіді та підтверджує завершення. |


![](https://www.plantuml.com/plantuml/png/bLBBJi9G4DtVhvY4lH5ZrC065_w1Fz30BJP28UMIiEY2nuO5aSGWIun_KAkL-g3-mimVUIwDCRLnuQQvS-QScJCdRGoC4vXXjwD2lkCtcV0d9pAMQQZs7JMuzlo-4pXTQcdN6NRCfHwPyuxNzhlQDzJ4HmTArOfgubZM_0nep2d77CcAK6OoaQdCmDfnGfpXaUu1C03jP5d7f0rlKKJy2i87lykDh41QGBiatb8k-XQ0aTQL2Ylwn7LqC-G7TB654tIY4ECA0EKEKS0Wd2vBnW3Rz-8FUtxFQ0gyzfMXYkkULKyFrSMegVl6w_bqV50jL4TA-oso4bNEjyQtDYC0MPvMdX8k_tNYlyxRygDTW7bF-Rouk4JMDk9x-uGejboqNsG6BiHH3icSav_bPUURSZI44U0WlZc0h3mig-ENwlLL0vdWX_i2)
```plantuml
@startuml
|Експерт|
start
skinparam defaultTextAlignment center

:Експерт відкриває доступне опитування;
:Ознайомлюється з питаннями;

|#e6faec|Система|
:Система перевіряє доступність опитування;
note right #ff8170
Exception 4.1
Exception 4.2
end note

|Експерт|
:Відповідає на питання;

|#e6faec|Система|
:Система зберігає відповіді;
:Підтверджує завершення;

|Експерт|
:Опитування успішно завершено;
stop
@enduml

```
### Процес 5: Створення нової форми опитування
| Поле                | Значення                                                                                  |
|---------------------|-------------------------------------------------------------------------------------------|
| **ID**              | createSurveyForm                                                                          |
| **Назва**           | Створення нової форми опитування                                                         |
| **Учасники**        | Адміністратор, Система                                                                   |
| **Передумови**      | - Адміністратор має обліковий запис.<br> - Має доступ до інтерфейсу для створення форм.|
| **Результат**       | Нова форма успішно створена та збережена в системі.                                     |
| **Виключні ситуації**| Exception 5.1 - Помилки при збереженні.<br> Exception 5.2 - Неповна інформація при заповненні форми.<br> Exception 5.3 - Проблеми із сервером.|
| **Основний сценарій** | 1. Адміністратор відкриває інтерфейс для створення нової форми.<br> 2. Вводить назву та опис форми.<br> 3. Додає необхідні поля (текстові поля, радіо-кнопки тощо).<br> 4. Налаштовує валідацію полів і стиль форми.<br> 5. Зберігає форму.|



![](https://www.plantuml.com/plantuml/png/bLBBJi9G4DtVhxW96qsC4OsFm0ON_e4_qC0jDa8XvPAmw88764sC64FOkV0FIgMXbeU_CFUFF5F1f0jDt13cp9apPqvlgQKjJxVhDU7JCyrfPQQqDbFJCttJfS3qQMEwlaXPedNhk4tBi-goecohNTFNggClQqxLhIjNop9-b2T4uNSbII7WEIM0OWe1JoJpq8rCrmmfeW_Jas0ipLZoB4YO0xu62z0mBLSK5x7dXRiWnzZnA449Q84D0ucvGABrYLOlCoJyd3gpBLNswOsRl1cTm8TS1f0OZdWpMuQtCQnIiZMJWBKx3ej32W7EsIKaHkm_-FvR56v3A-avrHijSxPzaJy_4bUTicfgf-7AqyDyfZhEL2T2kHN90kBlprEWIPe3nucz4OgP6N7IpCOb03ZGlVIuXCU1uAu3zXw3Z0jbglP0ctsEzXKNB25ulwKEM3faa6NHkCFCqrOQKFYlQ1Squt0nzxupdIxv-LHcKCIZQpH52H7WUNu1)
```plantuml
@startuml
|Адміністратор|
start
skinparam defaultTextAlignment center

:Адміністратор відкриває інтерфейс для створення форми;
:Вводить назву та опис форми;

|#e6faec|Система|
:Система перевіряє коректність введених даних;
note right #ff8170
Exception 5.1
Exception 5.2
Exception 5.3
end note

|Адміністратор|
:Додає необхідні поля (текстові, вибір тощо);
:Налаштовує валідацію полів;

|#e6faec|Система|
:Система зберігає нову форму;
stop
@enduml

```
### Процес 6: Редагування існуючої форми опитування

| Поле                | Значення                                                                                  |
|---------------------|-------------------------------------------------------------------------------------------|
| **ID**              | editSurveyForm                                                                            |
| **Назва**           | Редагування існуючої форми                                                                |
| **Учасники**        | Адміністратор, Система                                                                   |
| **Передумови**      | Існуюча форма потребує змін                                                               |
| **Результат**       | Зміни успішно збережено, форма оновлена                                                 |
| **Виключні ситуації**| Exception 6.1 - Конфлікти версій при редагуванні.<br> Exception 6.2 - Помилки під час збереження змін.| 
| **Основний сценарій** | 1. Адміністратор відкриває список форм.<br> 2. Обирає форму для редагування.<br> 3. Вносить зміни (додає/видаляє поля).<br> 4. Зберігає оновлену форму.|


![](https://www.plantuml.com/plantuml/png/bPBFIW9H5CRtzoaEk2c8o1OMkR55Rz0B37h7XdIKyGekPZ4wHGIH4M6xe3SO_rY3ZjChdFD6VJSXQsEqy7BlvtT-vvoFgNIC4vXkiw52Vk0PPpBYbOoaBmE9E941vnA5wikbEfUUttO2fqarxJhTXZdNFNFQyEf-K_k6gZXqeDG9Fu8oumK8AKz0UIBfymUdE7DUaEMZIoptSWFnckJAjk6iZDeN7aEBRDMtBZ61jvGXuJN7DU6fn1RDAu26PQN2WYwvZgw6_8foZ0zVnaa8uZCdQol4XDya_XVPRnbDWLU_C5HmtUFYqO4wwrLrstWjdqhxHQNz6bcJsXuXKW4on-Of_hWZVbyxEIKKvOHySbv2cT2E5V1317l44qxjtGvf1xUuMyvtj-_yIx2znZoN2FIffVviBl4cZD6VwnvkrksOLbjLyCJNyma0)
```plantuml
@startuml
|Адміністратор|
start
skinparam defaultTextAlignment center

:Відкриває список існуючих форм;
:Обирає форму для редагування;

|#e6faec|Система|
:Завантажує форму для редагування;
note right #ff8170
Exception 6.1
end note

|Адміністратор|
:Вносить зміни до полів (додає, видаляє тощо);

|#e6faec|Система|
:Система зберігає зміни у формі;
note right #ff8170
Exception 6.2
end note
stop
@enduml

```
### Процес 7: Публікація форми опитування
| Поле                | Значення                                                                                  |
|---------------------|-------------------------------------------------------------------------------------------|
| **ID**              | publishSurveyForm                                                                         |
| **Назва**           | Публікація форми опитування                                                               |
| **Учасники**        | Адміністратор, Система                                                                   |
| **Передумови**      | Форма готова до публікації                                                                |
| **Результат**       | Форма успішно опублікована та доступна для користувачів                                   |
| **Виключні ситуації**| Exception 7.1 - Недоступність сервера під час публікації.<br> Exception 7.2 - Відсутність прав на публікацію.| 
| **Основний сценарій** | 1. Адміністратор відкриває список створених форм.<br> 2. Обирає форму, яку необхідно опублікувати.<br> 3. Перевіряє налаштування форми та вносить необхідні зміни (за потреби).<br> 4. Надає дозвіл на публікацію форми.<br> 5. Система перевіряє доступність сервера та права адміністратора.<br> 6. Форма успішно публікується та стає доступною користувачам.|



![](https://www.plantuml.com/plantuml/png/VPBDJi9G48NtynIJi3VY3nZPuC8ty0KQkCL6AAHS4XPT03N6XH4NXYwDRu08XiWFhp3pHfxMXEIQuAQvPthEV7UchNQj5zbUgqcnlCXSrZgHZKvqg2CTo5H7ijL1JBcBkdT1sF4YhyLrutkzfhqnVNlL31fXouIMQtYOYEZoS2UMhNp8CY-yijvdDJWJHc2bOvQT9Z2iaFs6vG7vj48K5qp9zqmjbdU4qL4MifPf39HJG5uMwBYG6P837GCYdu00BhFzTPxsP5bcvEq1RjYsXgEWSMkvuFiNnV8nNVThfcE3TiZbewAZJXnrwgWpHvqxgaGch7E6eh_ZEDVInDqOJ5F6EL_exr2fflau-P09Th71-Rb2_tvRGD_mOWuvovO7unVm6rZ73EXGTiWyvhtI0ulgsdQ7gfW3Fz8F)
```plantuml
@startuml
|Адміністратор|
start
skinparam defaultTextAlignment center

:Адміністратор обирає форму для публікації;

|#e6faec|Система|
:Система перевіряє готовність форми до публікації;
note right #ff8170
Exception 7.1
Exception 7.2
Exception 7.3
Exception 7.4
Exception 7.5
Exception 7.6
end note

:Система публікує форму та робить її доступною;

|Адміністратор|
:Підтвердження успішної публікації;
stop
@enduml

```
