Яндекс.Практикум
курс Python-разработчик
студент Липатов Павел
Учебный проект sprint_9. API для Yatube.
Цель работы над проектом - получить навыки работы с Django REST framework. Задание представляет из себя по заданным правилам поведения АПИ и нескольким достаточно простым моделям со связанными отношениями реализовать логику работы АПИ.

Установка.

Клонировать репозиторий и перейти в его папку в командной строке:

git clone https://github.com/Juniee5/api_final_yatube
cd api_final_yatube
Cоздать и активировать виртуальное окружение:

python -m venv venv
Для *nix-систем:

source venv/bin/activate
Для windows-систем:

source venv/Scripts/activate
Установить зависимости из файла requirements.txt:

python -m pip install --upgrade pip
pip install -r requirements.txt
Выполнить миграции:

cd yatube_api
python manage.py migrate
Создать суперпользователя django:

python manage.py createsuperuser
Запустить проект:

python manage.py runserver
Сам проект и админ-панель искать по адресам:

http://127.0.0.1:8000

http://127.0.0.1:8000/admin
Некоторые примеры запросов к API.

Получение списка сообществ:

эндпойнт:

/api/v1/groups/
разрешённые HTTP-методы:

GET
в ответе:

[
  {
    "id": 0,
    "title": "string",
    "slug": "string",
    "description": "string"
  }
]
response status code 200
Создание подписки

эндпойнт:

/api/v1/follow/
http-метод:

POST
Payload:

{
  "following": "string"
}
Варианты ответов:

удачное выполнение - статус 201 и созданный экземпляр подписки
{
  "user": "string",
  "following": "string"
}
отклонение запроса - статус 400 - пропущен обязательный параметр
{
  "following": [
    "Обязательное поле."
  ]
}
отклонение запроса - статус 401 - запрос от неаутенфицированного пользователя
{
  "detail": "Учетные данные не были предоставлены."
}
Полный перечень запросов АПИ есть в ReDoc по адресу "http://127.0.0.1:8000/redoc/"
