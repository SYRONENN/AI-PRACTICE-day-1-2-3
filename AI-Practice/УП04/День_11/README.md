 День 11. Восстановление ИИ агента

Имя архива: ~/up04-backup/agent-day11.tar.gz
Путь восстановления:/home/gribov/up04-restore.a1MHLZ/AI-Practice/УП01/AI-Agent

Выполненные команды

ROOT=\$(git rev-parse --show-toplevel)
mkdir -p ~/up04-backup && chmod 700 ~/up04-backup
git -C "\$ROOT" rev-parse --short HEAD
git -C "\$ROOT" archive --format=tar.gz -o ~/up04-backup/agent-day11.tar.gz HEAD AI-Practice/УП01/AI-Agent
tar -tzf ~/up04-backup/agent-day11.tar.gz

ORIG_DIR=\$(pwd)
RESTORE=\$(mktemp -d ~/up04-restore.XXXXXX)
tar -xzf ~/up04-backup/agent-day11.tar.gz -C "\$RESTORE"
cd "\$RESTORE/AI-Practice/УП01/AI-Agent"
cp "\$ORIG_DIR/.env" .env && chmod 600 .env

sudo docker compose -p up04-restore config --quiet
sudo docker compose -p up04-restore build
sudo docker compose -p up04-restore run --rm agent
sudo docker compose -p up04-restore down


Результаты испытаний

1 Наличие файлов после восстановления |

Все файлы распакованы в /home/gribov/up04-restore.a1MHLZ/AI-Practice/УП01/AI-Agent

2 Образ собирается командой docker compose -p up04-restore build без ошибок. Образ my-ai-agent:1.0 успешно собран за 0.6 с без ошибок

3 Агент запускается в контейнере и отвечает на запрос пользователя. Получен корректный ответ от GigaChat

4 Повторный запуск и другой запрос. Новый контейнер запускается повторно и принимает следующий запрос. Новый контейнер запустился без ошибок, агент готов к работе

Ошибки и вывод

Ошибки: правило .env.* в .gitignore заблокировало файл .env.example (исправлено добавлением исключения !.env.example)

Вывод: Резервное копирование без секретов и развёртывание проекта в изолированный каталог выполнены успешно. Контейнерное развёртывание полностью воспроизводимо, тестовые контейнеры остановлены
