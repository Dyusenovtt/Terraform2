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
```
## Задание 3
### Файл vms_platform.tf:

```hcl
### VM web variables

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

### VM db variables

variable "vm_db_name" {
  type    = string
  default = "netology-develop-platform-db"
}

variable "vm_db_platform_id" {
  type    = string
  default = "standard-v3"
}

variable "vm_db_cores" {
  type    = number
  default = 2
}

variable "vm_db_memory" {
  type    = number
  default = 2
}

variable "vm_db_core_fraction" {
  type    = number
  default = 20
}

variable "vm_db_image_family" {
  type    = string
  default = "ubuntu-2004-lts"
}
```
<img width="3111" height="525" alt="image" src="https://github.com/user-attachments/assets/c0f76f5e-fb7f-4584-be0f-3f1172cb05e2" />
## Задание 4: Outputs
<img width="1921" height="451" alt="image" src="https://github.com/user-attachments/assets/3ec2a547-5967-465b-be22-3dd09b81afec" />

## Задание 5 
<img width="1896" height="957" alt="image" src="https://github.com/user-attachments/assets/adbe31f3-3e2b-4941-a488-ff4a3d5c55ad" />

<img width="1905" height="400" alt="image" src="https://github.com/user-attachments/assets/374d4006-d13c-4bbc-91e5-b0d2830dba0d" />

```hcl
locals {
  web_vm_name = "netology-${var.vpc_name}-web-${var.vm_web_cores}-core"
  db_vm_name  = "netology-${var.vpc_name}-db-${var.vm_db_cores}-core"
}
```
## Задание 6 
vms_platform.tf
```hcl
variable "vms_resources" {
  type = map(object({
    cores         = number
    memory        = number
    core_fraction = number
  }))
  default = {
    web = {
      cores         = 2
      memory        = 2
      core_fraction = 20
    }
    db = {
      cores         = 2
      memory        = 2
      core_fraction = 20
    }
  }
}
```
variables.tf
```hcl
variable "metadata" {
  type = map(string)
  default = {
    serial-port-enable = "1"
  }
}
```
закомментировали ненужное. 
```hcl
root@myterra:~/ter-homeworks/02/src# cat vms_platform.tf 
### VM web variables

# variable "vm_web_name" {
#   type    = string
#   default = "netology-develop-platform-web"
# }

# variable "vm_web_platform_id" {
#   type    = string
#   default = "standard-v3"
# }

# variable "vm_web_cores" {
#   type    = number
#   default = 2
# }

# variable "vm_web_memory" {
#   type    = number
#   default = 2
# }

# variable "vm_web_core_fraction" {
#   type    = number
#   default = 20
# }

# variable "vm_web_image_family" {
#   type    = string
#   default = "ubuntu-2004-lts"
# }

### VM db variables

# variable "vm_db_name" {
#   type    = string
#   default = "netology-develop-platform-db"
# }

# variable "vm_db_platform_id" {
#   type    = string
#   default = "standard-v3"
# }

# variable "vm_db_cores" {
#   type    = number
#   default = 2
# }

# variable "vm_db_memory" {
#   type    = number
#   default = 2
# }

# variable "vm_db_core_fraction" {
#   type    = number
#   default = 20
# }

# variable "vm_db_image_family" {
#   type    = string
#   default = "ubuntu-2004-lts"
# }

### VM resources variable

variable "vms_resources" {
  type = map(object({
    cores         = number
    memory        = number
    core_fraction = number
  }))
  default = {
    web = {
      cores         = 2
      memory        = 2
      core_fraction = 20
    }
    db = {
      cores         = 2
      memory        = 2
      core_fraction = 20
    }
  }
}
```
Итог 
<img width="1905" height="381" alt="image" src="https://github.com/user-attachments/assets/947b941c-4ca8-49ef-a209-ff161b2ca64e" />



