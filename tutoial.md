# 🦖 Pterodactyl Tutorial

![Pterodactyl](https://img.shields.io/badge/Pterodactyl-Panel-blue)
![Docker](https://img.shields.io/badge/Docker-Required-blue)
![Linux](https://img.shields.io/badge/OS-Ubuntu-orange)
![Author](https://img.shields.io/badge/Author-DarkRezet-purple)

Полный пошаговый туториал по установке и настройке **Pterodactyl Panel**, **Wings**, а также добавлению поддержки **Python**, **Node.js**, **Java** и других языков.

---

## 📌 Что такое Pterodactyl?

**Pterodactyl** — это open-source панель управления серверами, построенная на Docker.  
Чаще всего используется для игровых серверов, ботов и backend-приложений.

### Основные компоненты:
- 🧠 **Panel** — веб-панель (Laravel + PHP)
- 🪽 **Wings** — демон для запуска контейнеров
- 🐳 **Docker** — изоляция и безопасность

---

## 🧰 Требования

### Сервер
- Ubuntu **20.04 / 22.04**
- Минимум **2 GB RAM** (рекомендуется 4+)
- Root-доступ

### Зависимости
- Docker
- PHP 8.1+
- MySQL / MariaDB
- Nginx
- Curl, Git

---

## 🚀 Быстрая установка зависимостей

```bash
apt update && apt upgrade -y
apt install -y curl wget git sudo
