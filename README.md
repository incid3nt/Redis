# Домашнее задание к занятию "Кеширование Redis/memcached" - Еноктаев Олег


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

Задание 1. Кеширование
Приведите примеры проблем, которые может решить кеширование.

Задание 2. Memcached
Установите и запустите memcached.

Задание 3. Удаление по TTL в Memcached
Запишите в memcached несколько ключей с любыми именами и значениями, для которых выставлен TTL 5.

Задание 4. Запись данных в Redis
Запишите в Redis несколько ключей с любыми именами и значениями.
1. Задание 1 ответ:
Повышение скорости доступа к данным, Снижение нагрузки на базу данных, Оптимизация работы распределенных систем,
Минимизация задержек при доступе к удаленным ресурсам, Обеспечение доступности данных при сбоях

2. Задание 2 ответ: root@postgres:/home/oleg# systemctl status memcached
● memcached.service - memcached daemon
     Loaded: loaded (/lib/systemd/system/memcached.service; enabled; preset: enabled)
     Active: active (running) since Mon 2025-03-03 22:11:37 MSK; 7s ago
       Docs: man:memcached(1)
   Main PID: 1104 (memcached)
      Tasks: 10 (limit: 2264)
     Memory: 1.9M
        CPU: 21ms
     CGroup: /system.slice/memcached.service
             └─1104 /usr/bin/memcached -m 64 -p 11211 -u memcache -l 127.0.0.1 -P /var/run/memcached/memcached.pid

мар 03 22:11:37 postgres systemd[1]: Started memcached.service - memcached daemon.

3.  Задание 3 Ответ:

oleg@postgres:~$ telnet localhost 11211

```
Trying ::1...
Connected to localhost.
Escape character is '^]'.
add oleg 0 20 5
value
STORED
get oleg 0 5
VALUE oleg 0 5
value
END
get oleg
END
```

4. Задание 4 ответ:
```
root@postgres:/home/oleg# redis-cli
127.0.0.1:6379> set key1 value1
OK
127.0.0.1:6379> set key2 value2
OK
127.0.0.1:6379> set key3 value3
OK
127.0.0.1:6379> get key1
"value1"
127.0.0.1:6379> get key2
"value2"
127.0.0.1:6379> get key3
"value3"
```