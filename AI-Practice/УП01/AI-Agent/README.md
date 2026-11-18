python3 -m venv .venv
./.venv/bin/python -m pip install -r requirements.txt
./.venv/bin/python final_day15.py

# Помощник по выбору фильмов
ИИ-агент на базе GigaChat. Подбирает фильмы и сериалы по предпочтениям пользователя.

## Возможности
- диалог с пользователем
- подбор фильма по жанру, настроению и другим параметрам
- история чата
- команды: выход, очистить, история

## Модель
GigaChat-2 (Sber)

## Требования
- Python 3.8+
- ключ GigaChat
- сертификат Russian_Trusted_Root_CA.cer


## Запуск

Создаем окружение с доступом к системным библиотекам и включаем его
python3 -m venv --system-site-packages venv
source venv/bin/activate

Создаем файл .env и открываем его в редакторе
touch .env

python3 final_day15.py

## Ограничения
- нужен интернет и рабочий ключ
- путь к сертификату нужно проверить