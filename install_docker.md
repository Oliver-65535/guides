# Краткое руководство по установке Docker и Docker Compose

## Введение

**Docker** --- платформа для запуска приложений в контейнерах.\
**Docker Compose** --- инструмент для управления многоконтейнерными
приложениями.

------------------------------------------------------------------------

## 1. Установка Docker

### Linux (Ubuntu / Debian)

1.  Обновление системы:

``` bash
sudo apt update && sudo apt upgrade -y
```

2.  Установка зависимостей:

``` bash
sudo apt install ca-certificates curl gnupg -y
```

3.  Добавление GPG-ключа:

``` bash
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo tee /etc/apt/keyrings/docker.asc > /dev/null
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

4.  Добавление репозитория:

``` bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo $VERSION_CODENAME) stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

5.  Установка Docker:

``` bash
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```

6.  Проверка:

``` bash
docker --version
```

------------------------------------------------------------------------

### macOS / Windows

1.  Скачайте Docker Desktop:
    https://www.docker.com/products/docker-desktop\
2.  Установите приложение\
3.  Проверьте:

``` bash
docker --version
```

------------------------------------------------------------------------

## 2. Настройка (опционально)

Запуск без sudo:

``` bash
sudo usermod -aG docker $USER
newgrp docker
```

------------------------------------------------------------------------

## 3. Docker Compose

Проверка:

``` bash
docker compose version
```

Установка (если требуется):

``` bash
sudo apt install docker-compose-plugin
```

------------------------------------------------------------------------

## 4. Пример docker-compose.yml

``` yaml
version: "3.9"

services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
```

Запуск:

``` bash
docker compose up -d
```

Остановка:

``` bash
docker compose down
```

------------------------------------------------------------------------

## 5. Полезные команды

``` bash
docker ps
docker images
docker logs <id>
docker exec -it <id> bash
```

------------------------------------------------------------------------

## Итог

-   Docker устанавливается через официальный репозиторий или Docker
    Desktop\
-   Docker Compose обычно встроен\
-   Основные команды: `docker` и `docker compose`
