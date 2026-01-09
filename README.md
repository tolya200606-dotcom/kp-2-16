# simple-express-api

REST API на Express.js зі **статичними даними** (масиви об'єктів) + прості fake JWT токени.

## Вимоги
- Node.js 18+ (або 16+)

## Встановлення та запуск
```bash
npm install
npm run dev
```

Сервер буде доступний: http://localhost:5000

## Швидкі тести (curl)

### 1) Статус
```bash
curl http://localhost:5000/api/status
```

### 2) Реєстрація
```bash
curl -X POST http://localhost:5000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{ "username":"newuser", "email":"newuser@example.com", "password":"mypassword123" }'
```

### 3) Логін (admin)
```bash
curl -X POST http://localhost:5000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{ "email":"admin@example.com", "password":"admin123" }'
```

### 4) Профіль (потрібен токен)
Замініть TOKEN на значення з відповіді login/register.
```bash
curl http://localhost:5000/api/auth/profile \
  -H "Authorization: Bearer TOKEN"
```

### 5) Отримати продукти
```bash
curl http://localhost:5000/api/products
```

### 6) Фільтри + пагінація + сортування
```bash
curl "http://localhost:5000/api/products?category=electronics&page=1&limit=2&sort=price_asc"
```

### 7) Створити продукт (потрібен токен)
```bash
curl -X POST http://localhost:5000/api/products \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer TOKEN" \
  -d '{ "name":"Новий продукт", "description":"Опис", "price": 999.99, "category":"electronics", "quantity":10 }'
```
