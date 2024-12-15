---
title: Use case диаграмма 
sidebar_position: 2
---
# use case диаграмма 

```plantuml

@startuml

actor "Пользователь" as U

actor "Организатор" as O

actor "Платежная система" as PS

package "Система для бронирования" {

usecase "Поиск мастер-класса" as SearchClass

usecase "Бронирование мастер-класса" as BookClass

usecase "Оплата мастер-класса" as PayClass

usecase "Добавление мастер-класса" as AddClass

usecase "Подтверждение бронирования" as ConfirmBooking

usecase "Отмена бронирования" as CancelBooking

usecase "Напоминание о мастер-классе" as Reminder

}

U --> SearchClass : Использует

BookClass --> SearchClass : include

BookClass --> PayClass : include

U --> BookClass : Использует

U --> PayClass : Использует

O --> AddClass : Добавляет

PayClass --> PS : Запрос на оплату

ConfirmBooking --> BookClass : extend

CancelBooking --> BookClass : extend

Reminder --> BookClass : extend

@enduml





