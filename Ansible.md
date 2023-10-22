**Ansible** — система управления конфигурациями, применяемая для автоматизации настройки и развертывания ПО. Используется декларативный язык разметки для описания конфигураций. Написана на Python.

Общая организация:
-----------------
- **ansible.cfg** - конфигурационный файл. Задает набор параметров, например:
  - **[delfaults]** -  секция, описывающая общие параметры по умолчанию;
    - **host_key_checking** - проверка ключей при подключении по SSH;
    - **inventory** - местоположение hosts;
    - **roles_path** - местоположение ролей;
    - **remote_user** - пользователь из-под которого будет работать ansible;
    - **private_key_file** - файл ssh-ключа.

> [delaults]
>
> host_key_checking = false
> 
> inventory = ./hosts
> 
> roles_path = ./roles
> 
> remote_user = user
> 
> private_key_file = id_rsa

- **hosts** - файл inventory. Содержит данные о хостах для подключения:
  - **[GROUP]** - объединение хостов в группу при необходимости;
  - **ansible_host** - имя или ip-адрес хоста;
  - **ansible_ssh_pass** - пароль для ssh подключения;
  - **new_password** - задать новый пароль;
  - **ansible_port** - ssg порт;
  - **ansible_become_pass** - пароль root
  - **postgres_pass** - пароль СУБД PostgreSQL.
 
> [GROUP]
>
> HOST1  ansible_host=10.10.10.1  ansible_ssh_pass=123  new_password=1234  ansible_port=2222  ansible_become_pass=1234  postgres_pass=4321
>
> HOST1  ansible_host=10.10.10.2  ansible_ssh_pass=123  new_password=1234  ansible_port=2222  ansible_become_pass=1234  postgres_pass=4321
   
- **host_vars** - метсоположение переменных хостов inventory.
- **group_vars** - местоположение переменных групп inventory.

> ansible_ssh_pass    : test
> 
> ansible_become_pass : '{{ ansible_ssh_pass }}'


