Тестовая роль для установки postgres_exporter<br>

Установочный файл располагается в директории **files**<br>
(Пока я не придумаю как лучше оптимизировать автоматическое доставание новойверсии).<br>

Необходимо понять, как передавать пароль корректно (или использовать ТУЗ/SecMan, другие способы выполнения задач).<br>
На данный момент role можно запустить, например, так:<br>
```
---
- hosts: your_host
  gather_facts: false
  roles:
    - install_postgres_exporter
  vars_files:
    - password
```
где в переменной **file** указывается установочный заархивированный файл,<br>
и в переменной **passwd2** хранится пароль для user'a postgres_exporter (этот же пароль идёт в строку подключения в template pg_exporter.env.