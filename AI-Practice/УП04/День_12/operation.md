Инструкция по эксплуатации
Все команды выполняются в терминале Ubuntu Server.
    1. Получение проекта и проверка Docker
      
      Команды:
git clone github.com ~/projects/AI-PRACTICE-day-1-2-3
docker --version && sudo docker compose version
sudo systemctl status docker —no-pager
      
Ожидаемый результат: Репозиторий склонирован в ~/projects/AI-PRACTICE-day-1-2-3, отображаются версии Docker и Compose, служба docker.service находится в статусе active (running)

    2. Создание локального .env из шаблона
      Рабочая папка: ~/projects/AI-PRACTICE-day-1-2-3/AI-Practice/УП01/AI-Agent
      Команды:
cp .env.example .env
nano .env
chmod 600 .env
(В файле .env необходимо указать действующий ключ в переменной GIGACHAT_CREDENTIALS)
      Создан локальный файл .env с рабочим ключом API и правами доступа 600 (чтение и запись только для владельца)
      
    3. Сборка образа
Дальнейшие шаги инструкции описывают сборку Docker-образа через docker compose build, запуск консольного интерфейса агента с помощью docker compose run --rm agent, а также процедуры обновления и пересборки контейнера после внесения изменений в код проекта
