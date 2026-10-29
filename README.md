
# DevOps — Лабораторная работа №2

## Тема
Работа с Docker и Docker Compose.

## Компоненты

- Frontend 2.0 — Nginx, HTML, CSS, JavaScript
- Backend 2.0 — Python, Flask
- Docker Compose — управление контейнерами

## Репозитории

- Frontend: https://github.com/wownter/frontend
- Backend: https://github.com/wownter/backend

## Структура проекта

LR1_Git/
├── frontend/
├── backend/
└── DevOps/
    ├── docker-compose.yml
    └── README.md

## Запуск

Все три репозитория должны находиться в соседних папках.

Перейти в папку DevOps:

    cd DevOps

Собрать и запустить контейнеры:

    docker compose up -d --build

Проверить состояние:

    docker compose ps

Просмотреть журналы:

    docker compose logs

Остановить приложение:

    docker compose down

## Доступ к приложению

http://127.0.0.1:8080

## Особенности

- Образы собираются автоматически из Dockerfile.
- Контейнеры используют отдельную Docker-сеть.
- Backend не публикует порт на хосте.
- Frontend зависит от готовности backend.
- Данные сохраняются в backend/data.txt вне контейнера.
- Настроена политика restart: unless-stopped.
