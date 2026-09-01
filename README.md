# Terraform2
Домашнее задание к занятию «Основы Terraform. Yandex Cloud»
# Задание 1
<img width="974" height="202" alt="image" src="https://github.com/user-attachments/assets/e8a712f8-36e1-41d4-897a-c92cfb013780" />
<img width="974" height="624" alt="image" src="https://github.com/user-attachments/assets/99acd33d-51b0-4a66-b0df-ce0b2c52ae26" />
| 1 | `platform_id = "standart-v4"` | main.tf | Исправлено на `platform_id = "standard-v3"` (т.к. зона `ru-central1-e` не поддерживает `standard-v4`) |
| 2 | `service_account_key_file = file("~/.authorized_key.json")` | providers.tf | Исправлено на `service_account_key_file = "key.json"` |
| 3 | `core_fraction = 5` | main.tf | Исправлено на `core_fraction = 20` (минимальное значение для зоны `ru-central1-e`) |
| 4 | `cores = 1` | main.tf | Исправлено на `cores = 2` (минимальное значение для `standard-v3`) |
| 5 | Отсутствие ролей у сервисного аккаунта | Yandex Cloud | Назначена роль `editor` через консоль |
| 6 | Отсутствие файла с переменными | - | Создан файл `personal.auto.tfvars` с реальными значениями |

# Зачем нужны параметры preemptible = true и core_fraction = 5

# preemptible = true (прерываемая ВМ)

# core_fraction = 5 (гарантированная доля ядра)
