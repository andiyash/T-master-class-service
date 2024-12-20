---
title:  Sequence diagram
sidebar_position: 1
---
# Сценарий бронирования мастер-класса пользователем

```plantuml

@startuml

actor "Пользователь" as U

participant "Система поиска" as SS

participant "Система бронирования" as BS

participant "Платежная система" as PS

U -> SS : Открыть страницу поиска

SS -> U : Отобразить форму поиска

U -> SS : Ввести параметры поиска

SS -> SS : Обработка запроса поиска

SS -> U : Отобразить результаты поиска

alt Результаты устраивают

U -> SS : Выбрать мастер-класс

SS -> BS : Передать данные мастер-класса для бронирования

else Результаты не устраивают

U -> SS : Применить фильтры

SS -> SS : Обработка запроса с фильтрами

SS -> U : Отобразить обновленные результаты поиска

U -> SS : Выбрать мастер-класс

SS -> BS : Передать данные мастер-класса для бронирования

end

BS -> BS : Проверка доступности мест

alt Места есть

BS -> U : Отобразить детали мастер-класса

else Мест нет

BS -> U : Сообщение об отсутствии мест

return

end

U -> BS : Забронировать место

BS -> BS : Обновить количество доступных мест

U -> BS : Ввести данные для оплаты

BS -> PS : Проверка платежных данных

PS -> BS : Подтверждение платежа

BS -> U : Подтверждение бронирования

U -> BS : Просмотреть бронирование в ЛК

@enduml





