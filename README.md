# Terraform2
Домашнее задание к занятию «Основы Terraform. Yandex Cloud»
# Задание 1
<img width="974" height="202" alt="image" src="https://github.com/user-attachments/assets/e8a712f8-36e1-41d4-897a-c92cfb013780" />
<img width="974" height="624" alt="image" src="https://github.com/user-attachments/assets/99acd33d-51b0-4a66-b0df-ce0b2c52ae26" />

| 1 | `platform_id = "standart-v4"` | main.tf | Исправлено на `platform_id = "standard-v3"` (т.к. зона `ru-central1-e` не поддерживает `standard-v4`) | (необходимо исправить t на d)

| 2 | `service_account_key_file = file("~/.authorized_key.json")` | providers.tf | скачал и загрузил через SFTP 

| 3 | `core_fraction = 5` | main.tf | Исправлено на `core_fraction = 20` (минимальное значение для зоны `ru-central1-e`) |

| 4 | `cores = 1` | main.tf | Исправлено на `cores = 2` (минимальное значение для `standard-v3`) |

| 5 | Отсутствие ролей у сервисного аккаунта | Yandex Cloud | Назначена роль `editor` через консоль |

| 6 | Отсутствие файла с переменными | - | Создан файл `personal.auto.tfvars` с реальными значениями |

# Зачем нужны параметры preemptible = true и core_fraction = 5

1 preemptible = true (прерываемая ВМ)
2 core_fraction = 5 (гарантированная доля ядра)

## Задание 2
<img width="1910" height="554" alt="image" src="https://github.com/user-attachments/assets/385332cf-ca84-46f3-981f-4f636f24bcdb" />


В файл `variables.tf` добавлены переменные с префиксом `vm_web_`:

```hcl
variable "vm_web_name" {
  type    = string
  default = "netology-develop-platform-web"
}
variable "vm_web_platform_id" {
  type    = string
  default = "standard-v3"
}
variable "vm_web_cores" {
  type    = number
  default = 2
}
variable "vm_web_memory" {
  type    = number
  default = 2
}
variable "vm_web_core_fraction" {
  type    = number
  default = 20
}
variable "vm_web_image_family" {
  type    = string
  default = "ubuntu-2004-lts"
}
### В main.tf хардкод заменен на переменные.
` ``` `
