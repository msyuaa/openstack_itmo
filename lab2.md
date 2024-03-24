University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Year: 2023/2024  
Group: K4113c  
Author: Iumadilova Angela\
Lab: Lab2

## Лабораторная работа №2 Создание ВМ

### Ход работы:


- Активированы переменные окружения для корректной авторизации в Keystone поде учетной записью пользователя admin и создана сеть провайдера

<img width="486" alt="lab2_1screen" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/dfa97786-36c4-491c-bf91-bd91ef116dfd">


- Создана подсеть в сети провайдера. 
<img width="502" alt="lab2_3" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/b0b01349-8511-4bf7-bf5c-f738505d90b8">


- Создана локальная сеть и подсеть. 

<img width="526" alt="lab2_4" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/f7d55314-32ce-4a10-a4f2-f66b6abeddfd">

<img width="532" alt="lab2_5" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/e9d1338a-a522-495c-be18-a00018b1aa04">


- Создан роутер и подключить созданные сети. Данный шаг необходим для обеспечения маршрутизации трафика между виртуальной сетью OpenStack и сетью провайдера:


<img width="573" alt="lab2_6" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/ee1ec60b-8e4d-42c1-bcf6-0836c5db03b1">

<img width="586" alt="lab2_7" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/6dd946a3-35c0-4c88-bed3-06d1a689f9db">


- Создан флейвор виртуальной машины. При запуске ВМ необходимо выбрать её размер. Данная команда создаёт ограничение по оперативной памяти в 256МБ:

<img width="551" alt="lab2_8" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/3574268f-c9dd-4701-b199-c1a2543cb29c">


- Создан ключ доступа. 

<img width="616" alt="lab2_9" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/db03f2cf-117a-4913-8261-5901ede1f4b9">

- Загружен образ Cirros в OpenStack Glance. 

<img width="676" alt="lab2_11" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/ef182006-9858-4f94-9bab-d271a48da9cc">


- Создано блочное устройство в Cinder. 

<img width="673" alt="lab2_12" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/801c1c51-e047-461e-a321-44cc3b2834a7">


- Создана виртуальная машина в веб-панели. Пререквизиты:
-- имя произвольное
-- источник: ранее созданный диск
-- флейвор: созданный ранее (можно другой, если позволяют ресурсы ВМ)
-- сеть: ранее созданная приватная

  <img width="639" alt="lab2_13" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/fe59a9e8-cfdd-4718-8627-dcdafccd0e95">


- Консоль доступа к ВМ.

  <img width="825" alt="lab2_14" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/47fd1088-d91e-47a4-a240-440d860e107b">

<img width="412" alt="lab2_15" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/559671c3-c676-49bc-a30d-8cb3f3176b4b">


### Задание:

1. Через Horizon создана еще одну приватная сеть+подсеть, подключена к уже существующему роутеру
   
   <img width="495" alt="lab2_16" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/c7adb817-393d-4844-9ee4-cb904019a670">

3. Через Openstack CLI сделана копия ранее созданного блочного устройства
   
   <img width="612" alt="lab2_17" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/b14681b6-37c7-4364-944f-70305c2d02d3">

5. Через Openstack CLI создана еще ВМ

<img width="607" alt="lab2_18" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/83234492-81a7-4a02-848f-adef2ec598d2">

<img width="756" alt="lab2_19" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/6dae3389-80e7-4583-bf33-403711cc4489">

<img width="738" alt="lab2_20" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/9dcc7c45-ef8b-4797-b8d2-205da04edc2d">


### Результаты:

1. Созданы публичные и приватные сети Neutron
2. Создан и присвоен флейвор Glance
3. Создано и подключено блочное устройство Cinder
4. Создан рабочий инстанс Nova
