### Шанс вопроса: 6%

Multistage в Docker помогает оптимизировать процесс сборки образа, уменьшая его размер за счет того, что каждая стадия сборки выполняется в отдельном контейнере. Это особенно полезно при работе с большими проектами или зависимостями.

Пример использования multistage в Dockerfile:

```dockerfile
# Первая стадия - этап сборки
FROM node:14 AS builder
WORKDIR /app
COPY package.json ./
RUN npm install
COPY . .
RUN npm run build

# Вторая стадия - этап конечного образа
FROM nginx:alpine
COPY --from=builder /app/dist /usr/share/nginx/html
```

В этом примере первая стадия использует Node.js для установки зависимостей и сборки проекта, а вторая стадия использует чистый образ Nginx для развертывания готового фронтенда. Таким образом, в конечном образе остаются только необходимые файлы, что позволяет уменьшить его размер.