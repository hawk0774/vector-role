# Ansible Role: Vector

[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-vector-blue)](https://galaxy.ansible.com/hawk0774/vector_role)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

**Лёгкая и надёжная установка Vector — ультрабыстрого агента для сбора, обработки и передачи логов.**

---

## Особенности

- Установка последней или указанной версии Vector
- Автоматическая загрузка `.rpm` пакета с [официального сайта Timber](https://packages.timber.io)
- Гибкая настройка через переменные
- Поддержка `systemd`: автозапуск и управление сервисом
- Идемпотентность: безопасно для повторных запусков

---

## Поддерживаемые платформы

- **CentOS 7 / 8**
- **RHEL 7 / 8**
- **Rocky Linux**
- **AlmaLinux**

> Требуется: `ansible >= 2.14`, `become: yes`, доступ в интернет

---

## Переменные роли

| Переменная | Описание | Тип | По умолчанию |
|-----------|---------|-----|--------------|
| `vector_version` | Версия Vector для установки | `string` | `0.35.0` |
| `vector_config_dir` | Директория конфигурации | `string` | `/etc/vector` |
| `vector_service_enabled` | Включить автозапуск | `bool` | `true` |
| `vector_service_state` | Состояние сервиса | `string` | `started` |

> Пакет загружается с:  
> `https://packages.timber.io/vector/{{ vector_version }}/vector-{{ vector_version }}-1.x86_64.rpm`

---

## Пример Playbook

```yaml
# playbook.yml
- name: Установка Vector
  hosts: logs
  become: yes
  roles:
    - role: hawk0774.vector_role
      vector_version: "0.36.0"
      vector_service_state: started
