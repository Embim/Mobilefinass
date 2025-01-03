---
title: Диаграмма последовательности
sidebar_position: 2
---

# Диаграмма Последовательности для Mobile Finance Assistant
```plantuml
@startuml

actor Пользователь

participant Графический_интерфейс

participant Система

database "База данных" as DB

participant "ИТ система поддержки" as Jira

== Начало процесса регистрации ==

Пользователь -> Графический_интерфейс: Нажать на кнопку регистрации

Графический_интерфейс -> Система: Запрос на вывод графического отображения регистрации

Система --> Графический_интерфейс: Вывод информации о странице регистрации

Графический_интерфейс --> Пользователь: Отображение страницы регистрации

== Ввод данных ==

Пользователь -> Графический_интерфейс: Ввести данные (email, пароль)

Графический_интерфейс -> Система: Передача данных (email, пароль)

Система -> Система: Проверить данные

alt Неверные данные

Система --> Графический_интерфейс: Показать сообщение об ошибке

Графический_интерфейс --> Пользователь: Отображение сообщения об ошибке

else Данные верны

Система -> DB: Проверка email на уникальность

DB --> Система: Email уникален

Система --> Графический_интерфейс: Попросить ввести код подтверждения

Графический_интерфейс --> Пользователь: Отображение запроса на ввод кода подтверждения

end

== Генерация и отправка кода ==

Система -> Система: Сгенерировать код подтверждения

Система --> Пользователь: Отправить код на email

Система -> DB: Сохранить код подтверждения

DB --> Система: Код сохранен

== Ввод кода ==

Пользователь -> Графический_интерфейс: Ввести код

Графический_интерфейс -> Система: Передать код

Система -> DB: Проверка кода подтверждения

DB --> Система: Код правильный

alt Неправильный код

Система --> Графический_интерфейс: Показать сообщение об ошибке

Графический_интерфейс --> Пользователь: Отображение сообщения об ошибке

else Код правильный

Система -> DB: Сохранить учетную запись

DB --> Система: Учетная запись сохранена

Система --> Графический_интерфейс: Учетная запись активирована

Графический_интерфейс --> Пользователь: Отображение уведомления об успешной активации и автоматический вход

end

== Ошибки/проблемы ==

alt Проблема с регистрацией

Система -> Jira: Сообщить об ошибке

Jira --> Система: Подтверждение получения сообщения

end

@enduml


```


## Описание процесса регистрации

### Начало процесса регистрации
1. **Пользователь** нажимает на кнопку регистрации.
2. **Графический интерфейс** отправляет запрос на вывод графического отображения страницы регистрации.
3. **Система** выводит информацию о странице регистрации.
4. **Графический интерфейс** отображает страницу регистрации пользователю.

### Ввод данных
1. **Пользователь** вводит свои данные (email, пароль).
2. **Графический интерфейс** передает данные (email, пароль) в систему.
3. **Система** проверяет данные:
   - Если данные неверны, система отправляет ошибку на экран.
   - Если данные верны, система проверяет уникальность email в базе данных.

### Генерация и отправка кода подтверждения
1. **Система** генерирует код подтверждения.
2. **Система** отправляет код на email пользователя.
3. **Система** сохраняет код подтверждения в базе данных.

### Ввод кода подтверждения
1. **Пользователь** вводит код подтверждения.
2. **Графический интерфейс** передает код в систему.
3. **Система** проверяет код подтверждения в базе данных:
   - Если код неправильный, система отправляет сообщение об ошибке.
   - Если код правильный, система сохраняет учетную запись и активирует её.

### Ошибки и проблемы
1. Если возникает проблема с регистрацией, система отправляет сообщение об ошибке в **ИТ систему поддержки (Jira)**.
2. **ИТ система поддержки (Jira)** подтверждает получение сообщения.

## Статус регистрации
- Процесс завершен успешно, если код подтверждения правильный и учетная запись активирована.
