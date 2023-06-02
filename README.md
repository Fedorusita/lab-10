# lab-10
# Часть 1   

1. Для начала развернём две виртуальные машины. Я выбрал Ubuntu 22.04.
 ![image](https://github.com/Fedorusita/lab-10/assets/112895410/fb9dd739-b5f6-4f21-8d0e-fa59e62af6cd)
2. На первой ВМ установим всё необходимое , в том числе Ansible и сгенерируем ssh-ключ.   

![image](https://github.com/Fedorusita/lab-10/assets/112895410/0b5d53bf-6e04-400a-b1d2-5caef1674407)

![image](https://github.com/Fedorusita/lab-10/assets/112895410/e03c892e-01a6-490f-a701-302077d2070a)   

**После генерации ключа у нас появился следующий файл:**   

![image](https://github.com/Fedorusita/lab-10/assets/112895410/f9e03e0c-88bd-46e7-b207-47d71fd2bdf6)

3. Скопируем ssh ключ на VM2:

``` $ ssh-copy-id <username>@<VM2_IP>```   
``` <username>@<VM2_IP>  ``` - это то что находится в верху терминала на VM2   
Нас попросят ввести пароль с вм2.   
**Первая часть выполнена**  

# Часть 2   

**Создадим необходимые файлы для работы Ansible**   
1. inventory   
```
[my_hosts]
VM1 ansible_host=<VM1_IP>
VM2 ansible_host=<VM2_IP>   
```
2. ansible.cfg   
```
[defaults]
inventory = inventory
```
3. playbook.yml   
```
---
- name: Update packages and prepare VM2
  hosts: VM2
  tasks:
    - name: Update packages
      apt:
        upgrade: yes
        update_cache: yes

    - name: Install Docker dependencies
      apt:
        name: "{{ item }}"
        state: present
      loop:
        - apt-transport-https
        - ca-certificates
        - curl
        - software-properties-common

    - name: Add Docker GPG key
      apt_key:
        url: https://download.docker.com/linux/ubuntu/gpg
        state: present

    - name: Add Docker repository
      apt_repository:
        repo: deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable
        state: present

    - name: Install Docker
      apt:
        name: docker-ce
        state: present

    - name: Install Docker Compose
      pip:
        name: docker-compose
        state: present

    - name: Start Docker service
      service:
        name: docker
        state: started
```
# Часть 3
1.Подключимся к VM2 по ssh. Нам необходимо узнать запущенные контейнеры, их статусы и их логи для этого:   
```
$ docker ps -a   

```
```
docker logs <container_id>
```
2. Отправим запрос на серверный контейнер.   
```
$ curl http://localhost:<port>
```









