![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)    ![Django](https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=django&logoColor=white)  ![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)  ![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white)  ![Gunicorn](https://img.shields.io/badge/gunicorn-%298729.svg?style=for-the-badge&logo=gunicorn&logoColor=white)  ![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white)


# Приложение для планирования своих задач.

## Деплой проекта Taski в **Docker контейнерах** на удалённый сервер.

### Описание проекта

Это полностью рабочий проект, который состоит из бэкенд-приложения на **Django** и фронтенд-приложения на **React**. 

### Возможности проекта: 

Можно добавить новую задачу на сайт или изменить существующую, а также просматривать созданные ранее задачи в двух разделах: завершённые (Complete) и незавершённые (Incomplete).


### Технологии


Проект Taski размещён в контейнерах и его запуск настроен через CI/CD с помощью GitHub Actions.

В контейнере бэкенда настроен **WSGI-сервер Gunicorn** для работы с бэкенд-приложением проекта, во втором контейнере настроен так же веб-сервер **Nginx** для перенаправления запросов и работы со статикой проекта. На веб-сервере настроено шифрование запросов по протоколу **HTTPS**.

- Python 3.9
- Django 2.2.19
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
В папке taski-docker/backend с файлом manage.py выполните команду:
```
python3 manage.py runserver
```

## Разработчик (исполнитель):
👩🏼‍💻 Юлия: https://github.com/miscanth