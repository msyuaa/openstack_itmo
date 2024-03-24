University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Year: 2023/2024  
Group: K4113c  
Author: Iumadilova Angela\
Lab: Lab1 

## Лабораторная работа №1 Подготовка к развертыванию OpenStack"

### Описание

### Ход работы:

- Создана ВМ в VirtualBox на базе образа Alma Linux3 (https://repo.almalinux.org/almalinux/9.3/isos/x86_64/AlmaLinux-9.3-x86_64-minimal.iso). Настроен проброс порта  127.0.0.1:2222->`ip`:22 и 127.0.0.1:8080->`ip`:80
  <img width="479" alt="ports" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/fa2e8a70-43d9-497d-bbf2-384d0becdd86">

- Установлен git: `dnf install git -y`
- Склонирован себе проект: `git clone https://gitlab.com/itmo_samon/openstack_lab.git`
- Выполнен `./prepare.sh`
- Выполнен `./config.sh`
  <img width="345" alt="2" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/1a5fe5b4-6002-4638-b500-b195fec130f4">

- Установлен OpenStack: `packstack --answer-file=answer.cfg`
  <img width="441" alt="preparesh" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/69913777-15bd-4269-8bc3-7c9a05f771e3">


- Команда `cat ~/keystonerc_admin`
  <img width="399" alt="keystonerc" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/a70d2722-b174-40ae-aead-9605595eec11">

- КОманда `source ~/keystonerc_admin`, чтобы данные для входа попали в переменные среды
  <img width="477" alt="openstack endpoint" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/0532907e-5d1d-4fa5-bd3e-03a90593963c">

- Команда `openstack endpoint list`, чтоб получить список эндпоинтов для сервисов Openstack
- Команду `openstack user list`
  <img width="406" alt="userlist" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/fa3a7c8e-2325-4490-bfdc-e825055596af">

- Команда `openstack project list`
  <img width="414" alt="project" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/bd185977-79cc-45f8-9bf2-614b7f267183">

- Команда `openstack project create --domain default --description "Demo Project" demo` и `openstack project list`
<img width="476" alt="demo+list" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/df50e691-6dbe-4310-bdff-e021d2bca68b">
- Подключение к веб-панели (*Horizon*) через браузер
<img width="749" alt="web" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/22bce797-ec76-4925-af5a-21e588073a59">

- Создание проекта и пользователя проекта в интерфейсе Horizon
<img width="492" alt="project_web_new" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/43e8bd57-eda2-464c-aef6-eda4299c0546">

<img width="490" alt="members" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/489a17c7-4b9f-488d-bbd1-bfb7d6c28806">

- Авторизация под созданным пользователем
  <img width="907" alt="angela_user" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/626b71f7-7d87-4828-91fc-ea05bcf7f559">


### Результаты:

1. Развернута ВМ на базе образа Alma Linux 9.3
2. Настроена среды для установки Openstack
3. Установлен OpenStack
4. Изучены возможности OpenStack CLI
5. Вход в Openstack через Horizon
6. Изучены способы создания проектов и пользователей
