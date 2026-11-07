# Linux Incident Lab

Учебный стенд для будущего инженера первой линии. Моделируем два инцидента: **HTTP 503** и **таймаут**. Учимся собирать диагностику Linux, фиксировать проверенные факты и оформлять тикеты по процессу Jira.

## Запуск на Linux / WSL

Понадобится Python 3.10+ и curl. Откройте терминал в этой папке.

~~~bash
python3 demo_service.py --mode healthy --port 8080
~~~

Во втором терминале:

~~~bash
curl -i http://127.0.0.1:8080/health
bash diagnose.sh 8080
~~~

Остановить сервер Ctrl+C и последовательно попробовать режимы:

~~~bash
python3 demo_service.py --mode error
python3 demo_service.py --mode slow
~~~

В error код HTTP 503. В slow ответ задерживается на 4 секунды, а диагностический curl ждёт только 2 секунды.

## Проверка тестов

~~~bash
python3 -m unittest discover -s tests -v
~~~

## Материалы

- [Jira: жизненный цикл инцидента](docs/JIRA_WORKFLOW.md)
- [INC-DEMO-001: HTTP 503](docs/INC-001.md)
- [INC-DEMO-002: таймаут](docs/INC-002.md)
- [План изучения Active Directory](docs/ACTIVE_DIRECTORY.md)

Скрипт diagnose.sh не изменяет систему и не требует sudo. Все Jira-тикеты вымышленные, настоящая Jira пока не подключена. Не публикуйте реальные логи с личными данными.

**Статус:** учебная версия v0.1; для дальнейшей личной практики и улучшений.
