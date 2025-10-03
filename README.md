# 🚀 Digital Editor System

<div align="center">

![Django](https://img.shields.io/badge/Django-5.2.6-092E20?style=for-the-badge&logo=django)
![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python)
![SQLite](https://img.shields.io/badge/SQLite-07405E?style=for-the-badge&logo=sqlite)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

**Система управления цифровой редакцией с продвинутой системой ролей и workflow**

[Особенности](#-особенности) • [Демо](#-демо) • [Установка](#-установка) • [Документация](#-документация) • [Разработка](#-разработка)

</div>

## 📋 Оглавление

- [Особенности](#-особенности)
- [Демо](#-демо)
- [Быстрый старт](#-быстрый-старт)
- [Установка](#-установка)
- [Документация](#-документация)
- [API Reference](#-api-reference)
- [Разработка](#-разработка)
- [Тестирование](#-тестирование)
- [Деплой](#-деплой)
- [Вклад в проект](#-вклад-в-проект)
- [Лицензия](#-лицензия)
- [Контакты](#-контакты)

## ✨ Особенности

### 🎯 Основной функционал
- **Многоуровневая система ролей** - Владелец, Редактор, Дизайнер, Автор
- **Полный workflow статей** - Черновик → На проверке → Одобрено → Опубликовано
- **Система комментариев и рецензирования** - Комментарии к конкретным фрагментам текста
- **Разграничение прав доступа** - Каждая роль имеет свои права и возможности
- **Личные кабинеты** - Персонализированные интерфейсы для разных типов пользователей

### 🔧 Технические особенности
- **Кастомная модель пользователя** с расширенными полями
- **Гибкая система разрешений** на основе декораторов и миксинов
- **RESTful архитектура** с четким разделением ответственности
- **Модульная структура** для легкого расширения
- **Панель администратора Django** с кастомизацией

### 🛡 Безопасность
- **Аутентификация** по логину/паролю
- **Авторизация** на основе ролей
- **CSRF защита**
- **Валидация данных** на всех уровнях
- **SQL injection protection** через ORM Django

## 🎮 Демо

### Онлайн демо
- **URL**: [Демо будет доступно после деплоя]
- **Тестовые пользователи**:

| Роль | Логин | Пароль | Доступ |
|------|-------|--------|---------|
| Владелец | `owner` | `testpass123` | Полный доступ |
| Редактор | `editor` | `testpass123` | Управление контентом |
| Автор | `author1` | `testpass123` | Создание статей |

### Локальный запуск демо

git clone https://github.com/YaEvgeshka/digital-editor-system.git
cd digital-editor-system
# Следуйте инструкциям в разделе Установка
## 🚀 Быстрый старт
### Требования
- **Python 3.8+**
- **Django 5.2.6**
- **SQLite (для разработки) / PostgreSQL (для продакшена)**
- 
Установка за 5 минут

### 1. Клонирование репозитория

```bash
git clone https://github.com/YaEvgeshka/digital-editor-system.git
cd digital-editor-system
```
### 2. Создание виртуального окружения

```bash
python -m venv venv
source venv/bin/activate  # Linux/MacOS
venv\Scripts\activate     # Windows
```
### 3. Установка зависимостей
```
pip install -r requirements.txt
```
### 4. Настройка базы данных
```
python manage.py migrate
```
### 5. Создание суперпользователя
```
python manage.py createsuperuser
```
### 6. Запуск сервера разработки
```
python manage.py runserver
```

После этого откройте http://localhost:8000 в браузере.

## ⚙️ Установка

Подробная установка для разработки
### 1. Подготовка окружения

*Клонирование репозитория*
```
git clone https://github.com/YaEvgeshka/digital-editor-system.git
cd digital-editor-system
```
*Создание виртуального окружения*
```
python -m venv venv
```
*Активация окружения (Linux/MacOS)*
```
source venv/bin/activate
```
*Активация окружения (Windows)*
```
venv\Scripts\activate
```
### 2. Установка зависимостей

*Обновление pip*
```
pip install --upgrade pip
```
*Установка зависимостей*
```
pip install -r requirements.txt
```
*Или установка в режиме разработки*
```
pip install -e .
```
### 3. Настройка базы данных
```bash
# Применение миграций
python manage.py migrate
```
*Создание фикстур с тестовыми данными*
```
python manage.py create_test_data  # Если есть management command
```
### 4. Создание администратора
```bash
python manage.py createsuperuser
```

Следуйте инструкциям в терминале для создания учетной записи администратора.

### 5. Запуск сервера
```bash
# Стандартный запуск
python manage.py runserver

# Запуск на определенном порту
python manage.py runserver 8080

# Запуск на всех интерфейсах
python manage.py runserver 0.0.0.0:8000
```
### Настройка для продакшена
- **Настройки базы данных (config/settings.py)**
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'digital_editor',
        'USER': 'your_username',
        'PASSWORD': 'your_password',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```
- **Настройки статических файлов**
```python
STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')
STATICFILES_STORAGE = 'whitenoise.storage.CompressedManifestStaticFilesStorage'
```
## 📚 Документация
🏗 Архитектура проекта
```text
digital-editor-system/
├── config/                 # Настройки проекта Django
│   ├── settings.py        # Основные настройки
│   ├── urls.py            # Корневые URL patterns
│   └── wsgi.py            # WSGI конфигурация
├── journal/               # Основное приложение
│   ├── models.py          # Модели данных (User, Article, Category, Comment)
│   ├── views.py           # Логика представлений
│   ├── urls.py            # URL patterns приложения
│   ├── admin.py           # Конфигурация админки
│   ├── forms.py           # Формы Django
│   ├── decorators.py      # Кастомные декораторы для прав доступа
│   ├── mixins.py          # Миксины для классов-представлений
│   └── templates/         # HTML шаблоны
│       └── journal/
│           ├── base.html          # Базовый шаблон
│           ├── home.html          # Главная страница
│           ├── login.html         # Страница входа
│           ├── dashboard.html     # Личный кабинет
│           ├── create_article.html # Создание статьи
│           └── article_detail.html # Детали статьи
├── requirements.txt       # Зависимости Python
├── manage.py             # Утилита управления Django
└── README.md             # Документация
```
👥 Система ролей
Владелец (Owner)
● Права: Полный доступ ко всем функциям системы
● Возможности:
○ Просмотр всей аналитики
○ Управление пользователями
○ Утверждение финальных версий номеров
○ Доступ ко всем материалам
Редактор (Editor)
● Права: Управление контентом и workflow
● Возможности:
○ Распределение заданий между авторами
○ Контроль статусов статей
○ Внесение правок и комментариев
○ Сборка номеров и отправка на утверждение
Дизайнер (Designer)
● Права: Работа с визуальной частью
● Возможности:
○ Доступ к одобренным материалам
○ Верстка и макетирование
○ Публикация финальных макетов
Автор (Author)
● Права: Создание и управление собственным контентом
● Возможности:
○ Создание и редактирование статей
○ Загрузка медиафайлов
○ Отправка статей на проверку
○ Просмотр комментариев редактора
## 📊 Workflow статей
graph TD
    A[Черновик] -->|Автор отправляет| B[На проверке]
    B -->|Редактор проверяет| C[Правки]
    C -->|Автор исправляет| B
    B -->|Редактор одобряет| D[Одобрено]
    D -->|Дизайнер верстает| E[В номере]
    E -->|Владелец утверждает| F[Опубликовано]
## 🔌 API Reference
Аутентификация
Вход в систему
http
POST /login/
Content-Type: application/x-www-form-urlencoded

username=user&password=pass
Response:
json
{
    "redirect": "/dashboard/",
    "user": {
        "username": "user",
        "role": "author"
    }
}
Выход из системы
http
GET /logout/
Статьи
Получение списка статей
http
GET /dashboard/
Authorization: Session cookie
Response: HTML страница с списком статей для текущего пользователя
Создание статьи
http
POST /articles/create/
Content-Type: application/x-www-form-urlencoded

title=Заголовок&content=Текст&category=1
Response: Redirect to /dashboard/
Редактирование статьи
http
POST /articles/1/edit/
Content-Type: application/x-www-form-urlencoded

title=Новый заголовок&content=Новый текст&category=2
Полная документация API
Для полной документации API создайте файл API.md или настройте Django REST Framework.
## 🛠 Разработка
Настройка среды разработки
1. Клонирование и настройка
bash
git clone https://github.com/YaEvgeshka/digital-editor-system.git
cd digital-editor-system
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
2. Настройка IDE (VS Code)
Создайте файл .vscode/settings.json:
json
{
    "python.defaultInterpreterPath": "./venv/bin/python",
    "python.linting.enabled": true,
    "python.linting.pylintEnabled": true,
    "python.formatting.autopep8Path": "./venv/bin/autopep8",
    "python.formatting.provider": "autopep8"
}
Стандарты кода
Структура коммитов
text
feat: добавление новой функциональности
fix: исправление ошибок
docs: изменение документации
style: исправление форматирования, отсутствие изменений в коде
refactor: рефакторинг кода
test: добавление тестов
chore: обновление зависимостей, настройка инструментов
Пример коммита
bash
git commit -m "feat: add email notifications for article status changes"
Процесс разработки
1. Создание ветки
bash
git checkout -b feature/name-of-feature
1. Разработка функциональности
2. Тестирование
bash
python manage.py test
python manage.py check
1. Коммит изменений
bash
git add .
git commit -m "feat: description of changes"
1. Пуш в репозиторий
bash
git push origin feature/name-of-feature
1. Создание Pull Request
## 🧪 Тестирование
Запуск тестов
bash
# Все тесты
python manage.py test

# Конкретное приложение
python manage.py test journal

# С покрытием кода
coverage run manage.py test
coverage report
Создание тестовых данных
bash
python manage.py shell
python
from journal.models import User, Category, Article

# Создание тестовых пользователей
users = [
    {'username': 'test_owner', 'password': 'test123', 'role': User.ROLE_OWNER},
    {'username': 'test_editor', 'password': 'test123', 'role': User.ROLE_EDITOR},
    {'username': 'test_author', 'password': 'test123', 'role': User.ROLE_AUTHOR}
]

for user_data in users:
    User.objects.create_user(**user_data)
## 🚀 Деплой
Деплой на Railway
1. Подготовка
bash
# Установка gunicorn
pip install gunicorn whitenoise

# Создание runtime.txt
echo "python-3.10" > runtime.txt

# Создание Procfile
echo "web: python manage.py migrate && gunicorn config.wsgi" > Procfile
2. Настройка settings.py для продакшена
python
import os
from pathlib import Path

BASE_DIR = Path(__file__).resolve().parent.parent

DEBUG = False
ALLOWED_HOSTS = ['*']  # Замените на ваш домен

# База данных
import dj_database_url
DATABASES = {
    'default': dj_database_url.config(default=os.environ.get('DATABASE_URL'))
}

# Статические файлы
STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')
STATICFILES_STORAGE = 'whitenoise.storage.CompressedManifestStaticFilesStorage'

# Security
SECRET_KEY = os.environ.get('SECRET_KEY', 'your-secret-key')
CSRF_TRUSTED_ORIGINS = ['https://your-domain.railway.app']
Деплой на Heroku
bash
# Создание heroku приложения
heroku create your-app-name

# Настройка переменных окружения
heroku config:set SECRET_KEY=your-secret-key
heroku config:set DEBUG=False

# Деплой
git push heroku main

# Миграции
heroku run python manage.py migrate
## 🤝 Вклад в проект
Мы приветствуем вклад в развитие проекта!
Процесс внесения вклада
1. Форкните репозиторий
2. Создайте ветку для функции
bash
git checkout -b feature/amazing-feature
1. Закоммитьте изменения
bash
git commit -m 'feat: Add amazing feature'
1. Запушьте ветку
bash
git push origin feature/amazing-feature
1. Откройте Pull Request
Руководство по код-стайлу
● Следуйте PEP 8 для Python кода
● Используйте Black для форматирования
● Документируйте все новые функции
● Пишите тесты для новой функциональности
Шаблон для Issues
При создании Issue используйте следующий шаблон:
text
## Описание
[Краткое описание проблемы или функциональности]

## Шаги для воспроизведения (для багов)
1. 
2. 
3. 

## Ожидаемое поведение
[Что должно происходить]

## Фактическое поведение  
[Что происходит на самом деле]

## Дополнительная информация
[Скриншоты, логи, версии и т.д.]
## 📄 Лицензия
Этот проект распространяется под лицензией MIT. Подробнее см. в файле LICENSE.
## 📞 Контакты
● Автор: YaEvgeshka
● Email: [your-email@example.com]
● GitHub: https://github.com/YaEvgeshka
● Проект: https://github.com/YaEvgeshka/digital-editor-system
🙏 Благодарности
● Команда Django за отличный фреймворк
● Сообщество Python за бесценные ресурсы и помощь
● Все контрибьюторы, которые помогают улучшать проект
<div align="center">
Если этот проект был полезен для вас, поставьте ⭐ звезду на GitHub!
</div> ```
