# Домашнее задание к занятию "8.4 Работа с Roles"

## Описание проделанной работы
В рамках выполнения домашнего задания были исправлены ошибки в локальных ролях, настроен файл зависимостей `requirements.yml` со ссылками на персональные репозитории, а также успешно запущен плейбук `site.yml`.

### 1. Исправление роли Vector
* Версия Vector обновлена на `0.39.0`.
* Исправлен URL скачивания с GitHub Releases под формат deb-пакета (`amd64`).
* Для установки скачанного пакета использован модуль `apt`.

### 2. Исправление роли LightHouse
* Перед клонированием добавлено удаление стандартной директории Nginx `/var/www/html` через `ansible.builtin.file` (`state: absent`).
* В конфигурации Nginx убран нерабочий `proxy_pass` и настроена раздача статических файлов напрямую из `/var/www/html`.

## Ссылки на репозитории ролей
* Vector: https://github.com/alexandr-bobkov/vector-role
* LightHouse: https://github.com/alexandr-bobkov/lighthouse-role

## Проверка установки ролей через requirements.yml
Корректность скачивания ролей из внешнего репозитория и персональных форков проверена командой:
```bash
ansible-galaxy install -r requirements.yml -p /tmp/test-roles/ --force