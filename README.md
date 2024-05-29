![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)  ![Django](https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=django&logoColor=white)  ![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)  ![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white)  ![Gunicorn](https://img.shields.io/badge/gunicorn-%298729.svg?style=for-the-badge&logo=gunicorn&logoColor=white)  ![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white)  ![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white)


# Приложение для планирования своих задач

## Деплой проекта Taski в **Docker контейнерах** на удалённый сервер

### Описание проекта

Это полностью рабочий проект, который состоит из бэкенд-приложения на **Django** и фронтенд-приложения на **React**. 

### Возможности проекта: 

Можно добавить новую задачу на сайт или изменить существующую, а также просматривать созданные ранее задачи в двух разделах: завершённые (Complete) и незавершённые (Incomplete).


Проект Taski размещён в нескольких контейнерах.
В контейнере бэкенда настроен **WSGI-сервер Gunicorn** для работы с бэкенд-приложением проекта, во втором контейнере настроен так же веб-сервер **Nginx** для перенаправления запросов и работы со статикой проекта. На веб-сервере настроено шифрование запросов по протоколу **HTTPS**.


### Настройка CI/CD

Деплой проекта на удалённый сервер настроен через CI/CD с помощью GitHub Actions, для этого создан workflow, в котором:

* проверяется код бэкенда в репозитории на соответствие PEP8;
* настроено автоматическое тестирование фронтенда и бэкенда;
* в случае успешного прохождения тестов образы должны обновляться на Docker Hub;
* обновляются образы на сервере и перезапускается приложение при помощи Docker Compose;
* выполняются команды для сборки статики в приложении бэкенда, переноса статики в volume; выполняются миграции;
* происходит уведомление в Telegram об успешном завершении деплоя.

Пример данного workflow сохранен в файле taski_workflow.yml в корневой директории проекта, при необходимости запуска перепишите содержимое файла в .github/workflows/main.yml.

Сохраните следующие переменные с необходимыми значениями в секретах GitHub Actions:

```
DOCKER_USERNAME - логин в Docker Hub
DOCKER_PASSWORD - пароль для Docker Hub
SSH_KEY - закрытый SSH-ключ для доступа к продакшен-серверу
SSH_PASSPHRASE - passphrase для этого ключа
USER - username для доступа к продакшен-серверу
HOST - адрес хоста для доступа к продакшен-серверу
TELEGRAM_TO - ID своего телеграм-аккаунта
TELEGRAM_TOKEN - токен Telegram-бота
```

Файл docker-compose.yml для локального запуска проекта и файл docker-compose.production.yml для запуска проекта на облачном сервере находятся в корневой директории проекта.


### Технологии

- Python 3.9
- Django 3.2.3
- Django REST framework 3.12.4
- PostgreSQL
- Docker
- Nginx
- Gunicorn
- GitHub Actions


### Запуск проекта в dev-режиме

Клонировать репозиторий и перейти в него в командной строке: 
```
git clone git@github.com:miscanth/taski-docker.git
```
Cоздать и активировать виртуальное окружение: 
```
python3.9 -m venv venv 
```
* Если у вас Linux/macOS 

    ```
    source venv/bin/activate
    ```
* Если у вас windows 
 
    ```
    source venv/scripts/activate
    ```
```
python3.9 -m pip install --upgrade pip
```
Установить зависимости из файла requirements.txt:
```
pip install -r requirements.txt
```
Задайте учётные данные БД в .env файле, используя .env.example:
```
POSTGRES_USER=логин
POSTGRES_PASSWORD=пароль
POSTGRES_DB=название БД
DB_HOST=название хоста
DB_PORT=5432
```

**Запустить Docker Compose с дефолтной конфигурацией (docker-compose.yml):**

* Выполнить сборку контейнеров: *sudo docker compose up -d --build*

* Применить миграции: *sudo docker compose exec backend python manage.py migrate*

* Создать суперпользователя: *sudo docker compose exec backend python manage.py createsuperuser*

* Собрать файлы статики: *sudo docker compose exec backend python manage.py collectstatic*

* Скопировать файлы статики в /backend_static/static/ backend-контейнера: *sudo docker compose exec backend cp -r /app/collected_static/. /backend_static/static/*

* Перейти по адресу 127.0.0.1:8000


## Разработчик (исполнитель):
👩🏼‍💻 Юлия: https://github.com/miscanth