# Домашнее задание к занятию "Очереди RabbitMQ" - Пергунов Д.В`
P.S скрипт Vagrant опубликован в данном репозитории

### Задание 1
Используя Vagrant развернем сервер с RabbitMQ.
![image](https://github.com/dimindrol/11-04_RabbitMQ/assets/103885836/6af587b3-29d3-4245-9051-3739ddf7a5ca)

### Задание 2
Запустили скрипт producer.py, зашли в интерфейс и нашли очередь  
![image](https://github.com/dimindrol/11-04_RabbitMQ/assets/103885836/a29f653a-dd7f-4ab7-8d50-b8745fe9b8ed)  
Запустили скрипт consumer.py, результат  
![image](https://github.com/dimindrol/11-04_RabbitMQ/assets/103885836/c8543641-d50c-4700-9642-523795a438bf)  
![image](https://github.com/dimindrol/11-04_RabbitMQ/assets/103885836/2e38c8be-b09c-41ee-bcf1-8f59225a346d)  

### Задание 3
Дополнили скрипт Vagrant объеденили Ноды в кластер  
![image](https://github.com/dimindrol/11-04_RabbitMQ/assets/103885836/435c9daa-4d1a-4d31-8c74-618fa6da517e)  
Вывод команды rabbitmqctl cluster_status  
![image](https://github.com/dimindrol/11-04_RabbitMQ/assets/103885836/a47c165e-3b9b-4f78-99ff-7a6c3f8436d2)  
![image](https://github.com/dimindrol/11-04_RabbitMQ/assets/103885836/b41d03e2-50cf-4846-be8b-3df8962c9c54)  
Запустили producer.py, результат выполнения команды rabbitmqadmin get queue='hello'
![image](https://github.com/dimindrol/11-04_RabbitMQ/assets/103885836/c9425f5f-146c-4b95-912b-849159f570be)  
![image](https://github.com/dimindrol/11-04_RabbitMQ/assets/103885836/d0684946-88d8-47bd-931b-c414c5255a28)
Отключили ноду 2, rabbit@rmq02  
Результат выполнения скрипта на ноде 1, rabbit@rmq01  
![image](https://github.com/dimindrol/11-04_RabbitMQ/assets/103885836/f04bc7fe-37ba-488a-b24b-148a4119b562)  
Дополнительные скриншоты:  
![image](https://github.com/dimindrol/11-04_RabbitMQ/assets/103885836/6c2ff81d-7891-4d56-8642-91d54236e219)  
![image](https://github.com/dimindrol/11-04_RabbitMQ/assets/103885836/12c3647a-c9c1-4d60-be81-3aafc0e10d5e)








