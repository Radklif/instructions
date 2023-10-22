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

Например:
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

- **host_vars** - метсоположение переменных хостов inventory.
- **group_vars** - местоположение переменных групп inventory.

Например:
> ansible_ssh_pass    : test
> 
> ansible_become_pass : '{{ ansible_ssh_pass }}'

