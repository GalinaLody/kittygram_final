![main.yml](https://github.com/GalinaLody/kittygram_final/actions/workflows/main.yml/badge.svg)
## Описание проекта.

Kittygram - это проект в формате социальной сети, в котором пользователи могут публиковать информацию и фотографии своих домашних котов. Данный проект является Rest API.

## Технологический стек проекта.
- Python 3.12  
- Django  
- Django REST Framework (DRF)  
- PostgreSQL  
- REST API
- Gunicorn
- Nginx
- Docker
- Docker Compose


### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/yandex-praktikum/kittygram_final.git
```

```
cd kittygram_final
```

В корневой папке проекта создать файл .env и заполнить его согласно примеру из файла .env.exampl.

В корневой директории(по месту нахождения файла docker-compose.production.yml) запустить контейнеры:
```
sudo docker compose up --build
```

В новом терминале в директории по месту нахождения файла docker-compose.production.yml выполнить миграции:
```
sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate
```

Собрать статику приложения и скопировать в папку /backend_static/static/:
```
sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
```
```
sudo docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /backend_static/static/
```

#  Как работать с репозиторием финального задания

## Что нужно сделать

Настроить запуск проекта Kittygram в контейнерах и CI/CD с помощью GitHub Actions

## Как проверить работу с помощью автотестов

В корне репозитория создайте файл tests.yml со следующим содержимым:
```yaml
repo_owner: ваш_логин_на_гитхабе
kittygram_domain: полная ссылка (https://доменное_имя) на ваш проект Kittygram
taski_domain: полная ссылка (https://доменное_имя) на ваш проект Taski
dockerhub_username: ваш_логин_на_докерхабе
```

Скопируйте содержимое файла `.github/workflows/main.yml` в файл `kittygram_workflow.yml` в корневой директории проекта.

Для локального запуска тестов создайте виртуальное окружение, установите в него зависимости из backend/requirements.txt и запустите в корневой директории проекта `pytest`.

## Чек-лист для проверки перед отправкой задания

- Проект Taski доступен по доменному имени, указанному в `tests.yml`.
- Проект Kittygram доступен по доменному имени, указанному в `tests.yml`.
- Пуш в ветку main запускает тестирование и деплой Kittygram, а после успешного деплоя вам приходит сообщение в телеграм.
- В корне проекта есть файл `kittygram_workflow.yml`.

Автор: Galina Lodygina
