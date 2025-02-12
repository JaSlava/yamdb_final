![example workflow](https://github.com/JaSlava/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

# Проект YaMDb

Проект YaMDb собирает отзывы (Review) пользователей на произведения (Titles). Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий (Category) может быть расширен администратором (например, можно добавить категорию «изобразительное искусство» или «Ювелирка»).

## Как запустить проект:

В проекте настроен workflow, - автоматически запускается и разворачивается на сервре с помощь команды git push. Убедитесь, что на вашем сервере установлен Docker.

**Проект подразумевает использование dotenv, поэтому необходимо:**

- Cоздать файл '.env' в дериктории '/infra/'**

- Открыть его и наполнить в соответствии с примером ниже**

```
DB_ENGINE='django.db.backends.postgresql'
DB_NAME='postgres'
POSTGRES_USER='postgres'
POSTGRES_PASSWORD='postgres'
DB_HOST='db' 
DB_PORT='...' 
SECRET_KEY = '...'
```

**Запустить docker-compose**

1. Создать контейнеры:
$ docker-compose up -d --build

2. Выполнить миграции:
$ docker-compose exec web python manage.py makemigrations
$ docker-compose exec web python manage.py migrate

3. Создать скперпользвателя:
$ docker-compose exec web python manage.py createsuperuser

4. Сделать статику:
$ docker-compose exec web python manage.py collectstatic --no-input


**Основные URLs:**
- http://84.201.153.187/api/v1/ - главная страница
- http://84.201.153.187/admin - доступ к админке
- http://84.201.153.187/redoc - доступ к reoc с подробным описанем проекта и его API

## Как запустить проект (локально):

**Клонировать репозиторий и перейти в него в командной строке:**

cd api_yamdb

**Cоздать виртуальное окружение:**

python -m venv venv (Windows)
python3 -m venv venv (Linux)

**Активировать виртуальное окружение:**

source venv/Scripts/activate (Windows)
source venv/bin/activate (Linux)

**Установить зависимости из файла requirements.txt:**

1) python -m pip install --upgrade pip (Windows)
   python3 -m pip install --upgrade pip (Linux)
   
2) cd api_yambd
   pip install -r requirements.txt

**Заменить везде ИП**
Так как проект рассчитан для выгрузки на сервер, то везде прописан ужаленный ИП (84.201.153.187), для работу локально его нужно заменить на 120.0.0.1

**Запустить docker-compose**

1. Создать контейнеры:
   docker-compose up -d --build

2. Выполнить миграции:
   docker-compose exec web python manage.py migrate

3. Создать скперпользвателя:
   docker-compose exec web python manage.py createsuperuser

4. Соделать статику:
   docker-compose exec web python manage.py collectstatic --no-input

**API для проекта YaMDb**

Просле запуска проекта, по адресу http://127.0.0.1/redoc/ будет доступна документация для API YaMDb. Там есть и примеры запросов к API.

## Создагте дампа (резервной копии) базы

docker-compose exec web python manage.py dumpdata > fixtures.json

Просле запуска проекта, по адресу http://127.0.0.1:8000/redoc/ будет доступна документация для API YaMDb. Там есть и примеры запросов к API.
## MIT License

Copyright (c) [2022] [Yakushkin Vyacheslav]

Настоящим предоставляется бесплатное разрешение любому лицу, получившему копию
данного программного обеспечения и связанных с ним файлов документации ("Программное обеспечение"), для
в Программном обеспечении без ограничений, включая, помимо прочего, права
использовать, копировать, изменять, объединять, публиковать, распространять, сублицензировать и/или продавать
копий Программного обеспечения, а также разрешить лицам, которым Программное обеспечение
предоставляется для этого при соблюдении следующих условий:

Вышеприведенное уведомление об авторских правах и это уведомление о разрешении должны быть включены во все
копии или существенные части Программного обеспечения.

ПРОГРАММНОЕ ОБЕСПЕЧЕНИЕ ПРЕДОСТАВЛЯЕТСЯ «КАК ЕСТЬ», БЕЗ КАКИХ-ЛИБО ГАРАНТИЙ, ЯВНЫХ ИЛИ
ПОДРАЗУМЕВАЕТСЯ, ВКЛЮЧАЯ, ПОМИМО ПРОЧЕГО, ГАРАНТИИ КОММЕРЧЕСКОЙ ЦЕННОСТИ,
ПРИГОДНОСТЬ ДЛЯ ОПРЕДЕЛЕННОЙ ЦЕЛИ И НЕНАРУШЕНИЕ ПРАВ. НИ ПРИ КАКИХ ОБСТОЯТЕЛЬСТВАХ
АВТОРЫ ИЛИ ВЛАДЕЛЕЦ АВТОРСКИХ ПРАВ НЕСУТ ОТВЕТСТВЕННОСТЬ ЗА ЛЮБЫЕ ПРЕТЕНЗИИ, УЩЕРБ ИЛИ ДРУГОЕ.
ОТВЕТСТВЕННОСТЬ, БУДУЩАЯ ПО ​​ДОГОВОРУ, ДЕЛИКТУ ИЛИ ИНЫМ ОБРАЗОМ, ВОЗНИКАЮЩАЯ ИЗ,
ВНЕ ИЛИ В СВЯЗИ С ПРОГРАММНЫМ ОБЕСПЕЧЕНИЕМ ИЛИ ИСПОЛЬЗОВАНИЕМ ИЛИ ДРУГИМИ СДЕЛКАМИ В
ПРОГРАММНОГО ОБЕСПЕЧЕНИЯ.
