### Шанс вопроса: 3%

1. `docker run`: Запускает новый контейнер из образа.
   ```bash
   docker run -d -p 8080:80 --name my_container nginx
   ```

2. `docker ps`: Отображает список запущенных контейнеров.
   ```bash
   docker ps
   ```

3. `docker stop <CONTAINER_ID>`: Останавливает указанный контейнер.
   ```bash
   docker stop my_container
   ```

4. `docker rm <CONTAINER_ID>`: Удаляет указанный контейнер.
   ```bash
   docker rm my_container
   ```

5. `docker images`: Отображает список образов, доступных на локальном реестре.
   ```bash
   docker images
   ```

6. `docker pull <IMAGE_NAME>`: Скачивает образ из Docker Hub.
   ```bash
   docker pull ubuntu
   ```

7. `docker build`: Создаёт новый образ на основе Dockerfile.
   ```Dockerfile
   FROM ubuntu:latest
   RUN apt-get update && apt-get install -y nginx
   CMD ["nginx", "-g", "daemon off;"]
   ```
   ```bash
   docker build -t my_nginx .
   ```

8. `docker exec`: Выполняет команду внутри запущенного контейнера.
   ```bash
   docker exec -it my_container bash
   ```

9. `docker network create`: Создаёт новую сеть Docker.
   ```bash
   docker network create my_network
   ```

10. `docker volume create`: Создаёт новый том Docker.
    ```bash
    docker volume create my_volume
    ```