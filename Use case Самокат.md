@startuml
title Use case сервиса Самокат
left to right direction
Пользователь--> (Вход в систему) 
(Вход в систему)..>(Добавить номер телефона):include
(Добавить номер телефона)..>(Ввести код из сообщения):include
actor "Служба сообщений" as SMS
:SMS:-up-->(Подтвердить номер)
(Ввести код из сообщения)..>(Подтвердить номер):include
(Подтвердить номер)..>(Сохранить данные):include 
note "Шаги у регистрации и авторизации совпадают" as N
:N:-right->(Вход в систему)
Пользователь--> (Просмотреть товар)
:Data:-up-->(Просмотреть товар)
Пользователь--> (Выполнить поиск)
:Data:-up-->(Выполнить поиск)
Пользователь--> (Добавить товар в раздел избранное)
(Добавить товар в раздел избранное)..>(Сохранить данные):include
actor "База данных" as Data 
:Data:-up-->(Сохранить данные)
Пользователь--> (Изменить данные пользователя)
note "Если пользователь не ввел имя, то по-умолчанию в лк будет указан номер телефона вместо имени" as N2
:N2:-right->(Изменить данные пользователя)
(Изменить данные пользователя)<..(Изменить имя):extend
(Изменить данные пользователя)<..(Изменить адрес):extend
(Изменить имя)..>(Сохранить данные):include
(Изменить адрес)..>(Сохранить данные):include
Пользователь--> (Добавить товар в корзину)
(Добавить товар в корзину)..>(Сохранить данные):include
Пользователь--> (Просмотр прошлых заказов)
:Data:-up-->(Просмотр прошлых заказов)
Пользователь--> (Оформить заказ)
(Оформить заказ)..>(Произвести оплату):include
(Произвести оплату)..>(Ввести данные карты):include
actor "Платежная система" as Pay 
:Pay:-up-->(Произвести оплату)
@enduml
