### Об авторе:
Меня зовут Юлия, и учусь в ЯндексПрактикуме в 21 когорте курса «Python-разработчик плюс».

## Деплой проекта Taski в **Docker контейнерах** на удалённый сервер.
Приложение для планирования своих задач.

Это полностью рабочий проект, который состоит из бэкенд-приложения на **Django** и фронтенд-приложения на **React**. Пользователь может получить доступ к проекту Taski по следующему доменному имени: https://taskirescue.ddns.net/

Возможности проекта: можно добавить новую задачу на сайт или изменить существующую, а также просмотривать созданные ранее задачи в двух разделах: завершённые (Complete) и незавершённые (Incomplete).

На удалённом сервере настроен **WSGI-сервер Gunicorn** для работы с бэкенд-приложением проекта, а так же веб-сервер **Nginx** для перенаправления запросов и работы со статикой проекта. На веб-сервере настроено шифрование запросов по протоколу **HTTPS**.