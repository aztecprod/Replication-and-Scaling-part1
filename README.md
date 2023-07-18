# Репликация и масштабирование. Часть 1 - Александр Шевцов
![image](https://github.com/aztecprod/Replication-and-Scaling-part1/assets/25949605/0a31ac85-d622-4ba7-aab1-2394c40c348b)
Master — это основной сервер БД, куда поступают все данные. Все изменения в данных (добавление, обновление, удаление) должны происходить на этом сервере.

Slave — это вспомогательный сервер БД, который копирует все данные с мастера. С этого сервера следует читать данные. Таких серверов может быть несколько.

В случае репликации master-slave лишь на мастере могут происходить изменения бд, slave сервер лишь копирует себе эти изменения. В случае master-master оба сервера могут изменяться , так как копирование этих изменений происходит уже обе стороны.
![image](https://github.com/aztecprod/Replication-and-Scaling-part1/assets/25949605/b3fb5083-fc8f-4573-8764-ef2b46795237)

Конфиг. Файл master-ноды:

![image](https://github.com/aztecprod/Replication-and-Scaling-part1/assets/25949605/0797233e-c2ab-4187-a501-6f2d057e33a7)
![image](https://github.com/aztecprod/Replication-and-Scaling-part1/assets/25949605/d6d78962-f597-40bb-8342-23474c7ca402)

Конфиг. Файл slave-ноды:

![image](https://github.com/aztecprod/Replication-and-Scaling-part1/assets/25949605/39a6fe73-6793-474f-9f4e-b131a9223c01)

"""
CHANGE MASTER TO MASTER_HOST = '192.168.0.108', MASTER_USER = 'replication', MASTER_PASSWORD = 'password', MASTER_LOG_FILE = 'debian2-bin.000001', MASTER_LOG_POS = 1567;
Start Slave;
Show slave status\g ;
"""

![image](https://github.com/aztecprod/Replication-and-Scaling-part1/assets/25949605/2534bf03-f08e-4bed-a2bc-1c1038151cf9)

До изменения БД в мастер-ноде:
![image](https://github.com/aztecprod/Replication-and-Scaling-part1/assets/25949605/9d264973-50fe-4a68-95c1-06cb02a12820)
После создания БД на мастер ноде:
![image](https://github.com/aztecprod/Replication-and-Scaling-part1/assets/25949605/495a9161-1dcc-4679-a9a6-a1f60d401f06)
