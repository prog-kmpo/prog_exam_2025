# prog_exam_2025
Материалы для подготовки к экзаменам 4 курс ИС зима 2025/26

# Полезные материалы по Computer Science

## Big O Notation (О-нотация)
### Основные концепции
| Концепция | Описание | Примеры |
|-----------|----------|---------|
| **Временная сложность** | Как быстро растёт время выполнения при увеличении входных данных | `O(1)`, `O(log n)`, `O(n²)` |
| **Пространственная сложность** | Как растёт потребление памяти при увеличении входных данных | `O(1)`, `O(n)`, `O(n²)` |
| **Асимптотический анализ** | Анализ производительности при больших объёмах данных | Отбрасывание констант, учет только доминирующего члена |

### Распространенные классы сложности
| Сложность | Название | Когда встречается | Визуализация |
|-----------|----------|-------------------|--------------|
| **O(1)** | Константная | Доступ по индексу, хеширование | ──────────── |
| **O(log n)** | Логарифмическая | Бинарный поиск, деревья | ───────/\─── |
| **O(n)** | Линейная | Линейный поиск, обход массива | ─────/\/\─── |
| **O(n log n)** | Линейно-логарифмическая | Эффективные сортировки | ────/\/\/\── |
| **O(n²)** | Квадратичная | Вложенные циклы, пузырьковая сортировка | ──/\/\/\/\─ |
| **O(2ⁿ)** | Экспоненциальная | Рекурсивные вычисления Фибоначчи | /\/\/\/\/\/\ |

### Полезные ресурсы
- [**Big O Cheat Sheet**](https://www.bigocheatsheet.com) - полная шпаргалка по сложности алгоритмов
- [**VisualGo**](https://visualgo.net) - визуализация алгоритмов с анализом сложности
- [**О-нотация на Хабр**](https://habr.com/ru/post/444594/) - подробное объяснение на русском

## UML Диаграммы

### Диаграмма прецедентов (Use Case Diagram)


**Основные элементы:**
- **Актеры** (Actors) - роли, взаимодействующие с системой
- **Прецеденты** (Use Cases) - цели, достигаемые в системе
- **Отношения**: ассоциации, включения (include), расширения (extend)

**Полезные ссылки:**
- [Диаграмма прецедентов на Wikipedia](https://ru.wikipedia.org/wiki/Диаграмма_прецедентов)
- [Примеры и шаблоны диаграмм](https://www.uml-diagrams.org/use-case-diagrams.html)


### Диаграмма классов (Class Diagram)
```mermaid
classDiagram
    class User {
        -String id
        -String username
        -String email
        -String passwordHash
        +register()
        +login()
        +updateProfile()
        +getOrders() List~Order~
    }
    
    class Order {
        -String orderId
        -Date orderDate
        -OrderStatus status
        -double totalAmount
        +addItem()
        +removeItem()
        +calculateTotal()
        +checkout()
    }
    
    class Product {
        -String productId
        -String name
        -String description
        -double price
        -int stock
        +updateStock()
        +getDetails()
    }
    
    class ShoppingCart {
        -List~CartItem~ items
        +addProduct()
        +removeProduct()
        +getTotal()
        +clear()
    }
    
    class OrderItem {
        -int quantity
        -double unitPrice
        +getSubtotal()
    }
    
    User "1" --> "*" Order : places
    Order "*" --> "*" Product : contains
    User "1" --> "1" ShoppingCart : has
    ShoppingCart "*" --> "*" Product : includes
    Order "1" --> "*" OrderItem : consists of
