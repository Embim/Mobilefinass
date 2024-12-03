---
title: ERD
sidebar_position: 1
---

# Модель данных

import Drawio from '@theme/Drawio'
import diagram from '!!raw-loader!./model.drawio';

<Drawio content={diagram} editable={false} />

## Сущности и их атрибуты

### **User (Пользователь)**

| Название    | Тип     | Описание                           |
| ----------- | ------- | ---------------------------------- |
| user_id     | int     | Уникальный идентификатор пользователя |
| name        | varchar | Имя пользователя                   |
| email       | varchar | Электронная почта пользователя     |
| password    | varchar | Хэшированный пароль                |
| created_at  | datetime| Дата регистрации                   |

### **Transaction (Транзакция)**

| Название     | Тип     | Описание                         |
| ------------ | ------- | -------------------------------- |
| transaction_id | int   | Уникальный идентификатор транзакции |
| user_id      | int     | Ссылка на пользователя           |
| amount       | float   | Сумма транзакции                 |
| category     | varchar | Категория транзакции (например, продукты, транспорт) |
| date         | datetime| Дата транзакции                  |

### **Budget (Бюджет)**

| Название    | Тип     | Описание                           |
| ----------- | ------- | ---------------------------------- |
| budget_id   | int     | Уникальный идентификатор бюджета  |
| user_id     | int     | Ссылка на владельца бюджета       |
| amount      | float   | Сумма бюджета                     |
| category    | varchar | Категория бюджета (например, продукты, развлечения) |
| created_at  | datetime| Дата создания бюджета             |

### **AnalyticsReport (Аналитический отчет)**

| Название      | Тип     | Описание                           |
| ------------- | ------- | ---------------------------------- |
| report_id     | int     | Уникальный идентификатор отчета   |
| user_id       | int     | Ссылка на пользователя            |
| total_amount  | float   | Общая сумма расходов              |
| report_date   | datetime| Дата формирования отчета          |

### **Course (Курс)**

| Название    | Тип     | Описание                           |
| ----------- | ------- | ---------------------------------- |
| course_id   | int     | Уникальный идентификатор курса    |
| title       | varchar | Название курса                    |
| description | varchar | Описание курса                    |
| progress    | float   | Прогресс пользователя в курсе (от 0 до 100%) |

---
