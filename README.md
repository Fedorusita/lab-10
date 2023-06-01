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

``` $ ssh-copy-id <username>@<VM2_IP> ```   
``` <username>@<VM2_IP>  ``` - это то что находится в верху терминала на VM2   
Нас попросят ввести пароль с вм2.   
**Первая часть выполнена**  

# Часть 2   








