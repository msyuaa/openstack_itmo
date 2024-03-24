University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Year: 2023/2024  
Group: K4113c  
Author: Iumadilova Angela\
Lab: Lab3

## Лабораторная работа №3 Работа с Openstack API

### Ход работы:

### Ход работы:

- Запрошен  у Keystone токен для дальнейшей работы 

<img width="930" alt="lab3_1" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/7361bbec-0f05-4634-a900-e766ababe9eb">

- Проверка, что токен рабочий

<img width="940" alt="lab3_2" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/7f1deb3f-da15-4631-b104-1b9d50ad9266">


- Создание новую ВМ через Nova API 

<img width="942" alt="lab3_3" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/83726c70-832f-4195-a0f6-4e91acbe1419">


### Задание:

- Повторена операцию по созданию ВМ через API, но с помощью  Python
```
import requests

url_token = 'http://localhost:5000/v3/auth/tokens'
url_server = 'http://localhost:8774/v2.1/servers'
user_name = input("Enter user name: ")
user_domain_id = input("Enter user domain id: ")
user_password = input("Enter user password: ")
project_name = input("Enter project name: ")
project_domain_id = input("Enter project domain id: ")

data1 = {
    "auth": {
        "identity": {
            "methods": [
                "password"
            ],
            "password": {
                "user": {
                    "name": user_name,
                    "domain": {
                        "id": user_domain_id
                    },
                    "password": user_password
                }
            }
        },
        "scope": {
            "project": {
                "name": project_name,
                "domain": {
                    "id": project_domain_id
                }
            }
        }
    }
}
response = requests.post(url_token, json=data1)
x_subject_token = response.headers.get('x-subject-token')

name = input("Enter server name: ")
imageRef = input("Enter imageRef: ")
flavorRef = input("Enter flavorRef: ")
network_uuid = input("Enter network UUID: ")
security_group_name = input("Enter security group name: ")

x_auth_token = x_subject_token

headers = {
    'Content-Type': 'application/json',
    'x-subject-token': x_subject_token,
    'x-auth-token': x_auth_token
}

data2 = {
    "server": {
        "name": name,
        "imageRef": imageRef,
        "flavorRef": flavorRef,
        "networks": [
            {
                "uuid": network_uuid
            }
        ],
        "security_groups": [
            {
                "name": security_group_name
            }
        ]
    }
}

response = requests.post(url_server, headers=headers, json=data2)

print(response.status_code)
print(response.text)
```
Результат вывода:
```
Enter user name: admin
Enter user domain id: default
Enter user password: 3cba083518cc4c1e
Enter project name: admin
Enter project domain id: default
Enter server name: myservertest
Enter imageRef: df3ba398-2bee-4592-9b79-20ddb263029a
Enter flavorRef: a9a79d92-db41-4f6e-a272-d3c32a758206
202
{"server": {"id": "c2c993a9-11b9-4540-8234-43c6c4ca9574", "links": [{"rel": "self", "href": "http://localhost:8774/v2.1/servers/c2c993a9-11b9-4540-8234-43c6c4ca9574"}, {"rel": "bookmark", "href": "http://localhost:8774/servers/c2c993a9-11b9-4540-8234-43c6c4ca9574"}], "OS-DCF:diskConfig": "MANUAL", "security_groups": [{"name": "fbc91437-172e-432f-9682-3a0dbc972786"}], "adminPass"/c2c993a9-11b9-4540-8234-43c6c4ca95: "qu6rMwwqBZdq"}}                                                                                                             "MANUAL", "security_groups": [{"nam
```
<img width="774" alt="lab3_5" src="https://github.com/msyuaa/openstack_itmo/assets/97636484/97041b4a-d8be-4b24-9455-a2f7eb7e7e11">



### Результаты:

1. Знакомство с Openstack API
2. Навык авторизации по паролю и токену
3. Навык управления ресурсами Openstack через эндпоинты
