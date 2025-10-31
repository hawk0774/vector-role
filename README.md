# Ansible Role: Vector

[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-vector-blue.svg)](https://galaxy.ansible.com/hawk0774/vector)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

Устанавливает и настраивает **Vector** — лёгкий, высокопроизводительный инструмент для сбора, обработки и передачи логов.

---

## Требования

- ОС: **CentOS 7/8**, **RHEL 7/8**, **Rocky Linux**, **AlmaLinux**
- Ansible: **>= 2.14**
- Права: `become: yes`
- Интернет-доступ для загрузки пакета

---

## Зависимости

Нет

---

## Переменные роли

| Переменная | Описание | Тип | По умолчанию |
|-----------|----------|-----|---------------|
| `vector_version` | Версия Vector для установки | string | `0.35.0` |
| `vector_config_dir` | Путь к директории конфигурации | string | `/etc/vector` |
| `vector_service_enabled` | Включить автозапуск сервиса | bool | `true` |
| `vector_service_state` | Состояние сервиса (`started`, `stopped`) | string | `started` |

> **Примечание**: Пакет загружается с официального сайта:  
> `https://packages.timber.io/vector/{{ vector_version }}/vector-{{ vector_version }}-1.x86_64.rpm`

---

## Пример использования

```yaml
# playbook.yml
- hosts: logs
  become: yes
  roles:
    - role: vector
      vector_version: "0.36.0"
      vector_service_state: started
