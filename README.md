# Terraform2
Домашнее задание к занятию «Основы Terraform. Yandex Cloud»
# Задание 1
<img width="974" height="202" alt="image" src="https://github.com/user-attachments/assets/e8a712f8-36e1-41d4-897a-c92cfb013780" />
<img width="974" height="624" alt="image" src="https://github.com/user-attachments/assets/99acd33d-51b0-4a66-b0df-ce0b2c52ae26" />
# Орфографическая ошибка "standart-v4" меняем на "standard -v3" т.к у меня выбрана новая зона доступности ru-central1-e
# service_account_key_file = file("~/.authorized_key.json") создал сервисную уз + ключ и загрузил через SFTP
# на моей зоны доступности минимальные значения core_fraction = 20, а 5 не поддерживается так же и standard-v3 минимальное количество ядер = 2
# добавил роль editor для сервисного аккаунта 
# Подставляем реальные значения в personal.auto.tfvars с яндекс cloud 
# Зачем нужны параметры preemptible = true и core_fraction = 5
# preemptible = true (прерываемая ВМ)
# core_fraction = 5 (гарантированная доля ядра)
