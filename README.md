## Thoth: Bitrix24 Integration Hub 

### Описание

Одна инсталляция Thoth позволяет создавать и обслуживать неограниченное количество локальных и тиражных приложений Битрикс24 с OAuth 2.0 авторизацией.

## Видеоинструкции на Youtube

https://www.youtube.com/playlist?list=PLeniNJl73vVmmsG1XzTlimbZJf969LIpS


## Установка 

+ Python 3.12
+ PostgreSQL 16
+ Redis

```
cd /opt
git clone https://github.com/vaestvita/thoth
cd thoth

python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements/production.txt

cp docs/example/env_example .env 
nano .env
заменить ALLOWED_HOSTS, CSRF_TRUSTED_ORIGINS на свои значения

python manage.py migrate
python manage.py collectstatic
python manage.py createsuperuser


python manage.py runserver 0.0.0.0:8000 (для тестирования и отладки)

```

## База данных 
Модуль [DJ-Database-URL](https://github.com/jazzband/dj-database-url?tab=readme-ov-file#url-schema) позволяет подключать различные базы. См документацию по ссылке.

После запуска сервера в файле .env будет создан ADMIN_URL, который необходимо исопльзовать для входа в админку

## Прокси сервер 
+ Процесс настройки Nginx и Gunicorn можно посмотреть [здесь](https://www.digitalocean.com/community/tutorials/how-to-set-up-django-with-postgres-nginx-and-gunicorn-on-ubuntu)
+ Примеры файлов конфигураций есть в [документации](docs/example)

## Логирование 
При необходимости можно включить подробные логи в консоль. Для этого в файле .env укажите уровень логиования LOG_LEVEL=DEBUG, перезапустите thoth и введите команду 

```
journalctl -u thoth -f
```

## Подключение 

+ [Битрикс](docs/bitrix.md)
+ [(WhatsApp) WABA](docs/waba.md)
+ [OLX](docs/olx.md)
