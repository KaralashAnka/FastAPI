# Advertisement Service API

FastAPI сервис для управления объявлениями купли/продажи.

## Описание

Сервис предоставляет REST API для создания, обновления, удаления и поиска объявлений. Данные хранятся в памяти (in-memory storage).

## Поля объявления

- **title** (str): Заголовок объявления
- **description** (str): Описание объявления  
- **price** (float): Цена
- **author** (str): Автор объявления
- **created_at** (datetime): Дата создания (автоматически)
- **id** (str): Уникальный идентификатор (автоматически)

## API Эндпоинты

### Создание объявления
```
POST /advertisement
```
Тело запроса:
```json
{
    "title": "Продам автомобиль",
    "description": "Отличный автомобиль в хорошем состоянии",
    "price": 500000.0,
    "author": "Иван Иванов"
}
```

### Получение объявления по ID
```
GET /advertisement/{advertisement_id}
```

### Обновление объявления
```
PATCH /advertisement/{advertisement_id}
```
Тело запроса (только поля для обновления):
```json
{
    "price": 450000.0,
    "description": "Новый текст описания"
}
```

### Удаление объявления
```
DELETE /advertisement/{advertisement_id}
```

### Поиск объявлений
```
GET /advertisement?title=автомобиль&author=Иван&min_price=100000&max_price=600000
```

Параметры запроса:
- `title`: Фильтр по заголовку (частичное совпадение, нечувствительно к регистру)
- `author`: Фильтр по автору (частичное совпадение, нечувствительно к регистру)
- `min_price`: Минимальная цена
- `max_price`: Максимальная цена

## Запуск проекта

### Локальный запуск
1. Установите зависимости:
```bash
pip install -r requirements.txt
```

2. Запустите сервис:
```bash
python main.py
```

Сервис будет доступен по адресу: http://localhost:8000

### Docker запуск
1. Сборка и запуск через docker-compose:
```bash
docker-compose up --build
```

2. Или сборка Docker образа и запуск:
```bash
docker build -t advertisement-service .
docker run -p 8000:8000 advertisement-service
```

## Документация API

После запуска сервиса документация доступна по адресам:
- Swagger UI: http://localhost:8000/docs
- ReDoc: http://localhost:8000/redoc
