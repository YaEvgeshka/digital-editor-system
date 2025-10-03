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
```bash
git clone https://github.com/YaEvgeshka/digital-editor-system.git
cd digital-editor-system
# Следуйте инструкциям в разделе Установка
🚀 Быстрый старт
Требования

    Python 3.8+

    Django 5.2.6

    SQLite (для разработки) / PostgreSQL (для продакшена)

Установка за 5 минут
# 1. Клонирование репозитория
git clone https://github.com/YaEvgeshka/digital-editor-system.git
cd digital-editor-system

# 2. Создание виртуального окружения
python -m venv venv
source venv/bin/activate  # Linux/MacOS
# или
venv\Scripts\activate     # Windows

# 3. Установка зависимостей
pip install -r requirements.txt

# 4. Настройка базы данных
python manage.py migrate

# 5. Создание суперпользователя
python manage.py createsuperuser

# 6. Запуск сервера разработки
python manage.py runserver
После этого откройте http://localhost:8000 в браузере.
⚙️ Установка
Подробная установка для разработки
1. Подготовка окружения
# Клонирование репозитория
git clone https://github.com/YaEvgeshka/digital-editor-system.git
cd digital-editor-system

# Создание виртуального окружения
python -m venv venv

# Активация окружения (Linux/MacOS)
source venv/bin/activate

# Активация окружения (Windows)
venv\Scripts\activate
2. Установка зависимостей
# Обновление pip
pip install --upgrade pip

# Установка зависимостей
pip install -r requirements.txt

# Или установка в режиме разработки
pip install -e .
3. Настройка базы данных
# Применение миграций
python manage.py migrate

# Создание фикстур с тестовыми данными
python manage.py create_test_data  # Если есть management command
4. Создание администратора
python manage.py createsuperuser
Следуйте инструкциям в терминале для создания учетной записи администратора.
5. Запуск сервера
# Стандартный запуск
python manage.py runserver

# Запуск на определенном порту
python manage.py runserver 8080

# Запуск на всех интерфейсах
python manage.py runserver 0.0.0.0:8000
Настройка для продакшена
Настройки базы данных (config/settings.py)
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
Настройки статических файлов
STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')
STATICFILES_STORAGE = 'whitenoise.storage.CompressedManifestStaticFilesStorage'
