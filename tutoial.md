# 🦖 Pterodactyl Tutorial

![Pterodactyl](https://img.shields.io/badge/Pterodactyl-Panel-blue)
![Docker](https://img.shields.io/badge/Docker-Required-blue)
![Linux](https://img.shields.io/badge/OS-Ubuntu-orange)
![Author](https://img.shields.io/badge/Author-DarkRezet-purple)

Полный пошаговый туториал по установке и настройке **Pterodactyl Panel**, **Wings**, а также добавлению поддержки **Python**, **Node.js**, **Java** и других языков.

---

## 📌 Что такое Pterodactyl

**Pterodactyl** — это open-source панель управления серверами, построенная на Docker.  
Подходит для игровых серверов, Discord-ботов, backend-приложений и скриптов.

### Компоненты
- 🧠 **Panel** — веб-панель (Laravel + PHP)
- 🪽 **Wings** — демон управления контейнерами
- 🐳 **Docker** — контейнеризация

---

## 🧰 Требования

### Сервер
- Ubuntu 20.04 / 22.04
- 2 GB RAM (рекомендуется 4+)
- Root-доступ

### ПО
- Docker
- PHP 8.1+
- MySQL / MariaDB
- Nginx
- Git, Curl

---

## 🚀 Установка базовых пакетов

```bash
apt update && apt upgrade -y
apt install -y curl wget git sudo unzip
```

---

## 🐳 Установка Docker

```bash
curl -fsSL https://get.docker.com | sh
systemctl enable --now docker
```

Проверка:
```bash
docker --version
```

---

## 🧠 Установка Pterodactyl Panel

### Установка PHP
```bash
apt install -y php8.1 php8.1-cli php8.1-gd php8.1-mysql php8.1-mbstring php8.1-xml php8.1-curl php8.1-zip
```

### Загрузка панели
```bash
mkdir -p /var/www/pterodactyl
cd /var/www/pterodactyl

curl -Lo panel.tar.gz https://github.com/pterodactyl/panel/releases/latest/download/panel.tar.gz
tar -xzvf panel.tar.gz
chmod -R 755 storage/* bootstrap/cache/
```

### Установка Composer
```bash
curl -sS https://getcomposer.org/installer | php
mv composer.phar /usr/local/bin/composer
composer install --no-dev --optimize-autoloader
```

---

## 🗄️ Настройка базы данных

```sql
CREATE DATABASE panel;
CREATE USER 'pterodactyl'@'localhost' IDENTIFIED BY 'strong_password';
GRANT ALL PRIVILEGES ON panel.* TO 'pterodactyl'@'localhost';
FLUSH PRIVILEGES;
```

---

## ⚙️ Настройка панели

```bash
php artisan key:generate --force
php artisan p:environment:setup
php artisan p:environment:database
php artisan migrate --seed --force
php artisan p:user:make
```

---

## 🪽 Установка Wings

```bash
mkdir -p /etc/pterodactyl
curl -L -o /usr/local/bin/wings https://github.com/pterodactyl/wings/releases/latest/download/wings_linux_amd64
chmod +x /usr/local/bin/wings
```

### Systemd
```bash
curl -o /etc/systemd/system/wings.service https://raw.githubusercontent.com/pterodactyl/wings/develop/wings.service

systemctl daemon-reexec
systemctl enable --now wings
```

---

## 🌐 Добавление Node (Ноды)

1. Зайти в **Admin Panel**
2. Locations → Create
3. Nodes → Create
4. Скопировать конфигурацию
5. Вставить в `/etc/pterodactyl/config.yml`
6. Перезапустить Wings

```bash
systemctl restart wings
```

---

## 🐍 Python (Egg)

### Пример Python Egg
```json
{
  "name": "Python App",
  "docker_image": "python:3.11",
  "startup": "python main.py",
  "files": {
    "main.py": "print('Hello from Pterodactyl!')"
  }
}
```

### Подходит для
- Discord-ботов
- Flask / FastAPI
- Парсеров
- Worker-скриптов

---

## ➕ Дополнительные языки

- Node.js
- Java
- Go
- Rust
- Bash
- Cron

---

## 🔐 Безопасность

- SSL (Let's Encrypt)
- Firewall (ufw)
- Закрытые порты
- Изоляция Docker

---

## 📚 Полезные ссылки

- https://pterodactyl.io
- https://github.com/pterodactyl

---

## 👤 Автор
**DarkRezet**

---
