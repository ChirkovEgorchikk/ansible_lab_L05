# Лабораторная работа L05: Ansible - Advanced

## Цель работы
Изучить продвинутые возможности Ansible: работу с переменными, циклами (`loop`), условиями (`when`), шаблонами Jinja2, отладкой (`debug`), обработкой ошибок и системой управления секретами Ansible Vault.

## Структура проекта
- `playbook.yml` — главный сценарий (использует `vars_files`).
- `vault/secrets.yml` — зашифрованный файл с паролем (Ansible Vault).
- `roles/webserver/templates/index.html.j2` — шаблон Jinja2.
- `roles/webserver/tasks/main.yml` — задачи с использованием `loop`, `debug`, `ignore_errors`.

## Ход выполнения

### 1. Создание зашифрованного файла (Vault)
С помощью команды `ansible-vault create` был создан файл с секретом.
<img width="596" height="247" alt="Снимок экрана 2026-11-20 010543" src="https://github.com/user-attachments/assets/3efa4635-6ee9-40d9-8277-e571b2085f52" />


### 2. Запуск плейбука
При запуске использовался флаг `--ask-vault-pass`. Ansible выполнил установку пакетов в цикле, вывел отладочную информацию (включая пароль), сгенерировал HTML-страницу из шаблона Jinja2 и проигнорировал заведомо ложную ошибку (`/bin/false`).
<img width="934" height="849" alt="Снимок экрана 2026-11-20 010444" src="https://github.com/user-attachments/assets/ae5d2507-56d4-4402-b04b-84abe2868d41" />


### 3. Результат работы шаблона
Веб-сервер отдает страницу, в которую подставлены переменные (имя хоста и секретный пароль).
<img width="805" height="336" alt="Снимок экрана 2026-11-20 010404" src="https://github.com/user-attachments/assets/375b6d49-7208-40d9-99bf-2929b1eac109" />

