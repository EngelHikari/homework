# Домашнее задание к занятию «Система мониторинга Zabbix» - Борисов Игорь


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

### Задание 1



1. устанавливаю Postgres командой sudo apt install postgresql
2. с помощью конфигуратора на сайте Zabbix скачиваю и устанавливаю репозиторий командами
   wget https://repo.zabbix.com/zabbix/6.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_6.0-4+ubuntu22.04_all.deb

   dpkg -i zabbix-release_6.0-4+ubuntu22.04_all.deb

   apt update
4.  устанавливаю Zabbix сервер, веб-интерфейс и агент командой
   apt install zabbix-server-pgsql zabbix-frontend-php php8.1-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
5. создал базу данных командой
   sudo -u postgres createuser --pwprompt zabbix
   
   sudo -u postgres createdb -O zabbix zabbix
7. импортирую начальную схему
   zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix 
8. отредактирова zabbix_server.conf записав туда пароль
9. запустил командой
   systemctl restart zabbix-server zabbix-agent apache2
   

![Снимок экрана 2024-06-20 183557](https://github.com/EngelHikari/homework/assets/165402013/dec69a5d-2026-4e3f-abef-8a0cf062c4f6)
![Снимок экрана 2024-06-20 183711](https://github.com/EngelHikari/homework/assets/165402013/ca6e486f-11a4-44c6-87be-8e20e1c8f7a0)
![Снимок экрана 2024-06-20 183755](https://github.com/EngelHikari/homework/assets/165402013/e07b70fd-eb4e-455e-8dd6-d715aab2a732)
![Снимок экрана 2024-06-20 183839](https://github.com/EngelHikari/homework/assets/165402013/9c38a0db-7c7c-4de5-a085-3cabf45051e7)
![Снимок экрана 2024-06-20 184627](https://github.com/EngelHikari/homework/assets/165402013/4144a84a-1ccf-4d21-ae1d-4db7bd330dee)

---

### Задание 2


1. с помощью конфигуратора на сайте Zabbix на хосты  скачиваю и устанавливаю репозиторий командами

   wget https://repo.zabbix.com/zabbix/6.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_6.0-4+ubuntu22.04_all.deb

   dpkg -i zabbix-release_6.0-4+ubuntu22.04_all.deb

   apt update
3. устанавливаю Zabbix агент командой

   apt install zabbix-agent
   
5. запускаю Zabbix и настраиваю его запуску при загрузке ос команндами

   systemctl restart zabbix-agent
   
   systemctl enable zabbix-agent
6. прописываю в настройках агента адрес сервера

   nano /etc/zabbix/zabbix-agentd.conf
  
7. перезапускаю агенты заббикса

   systemctl restart zabbix-agent
8. проверяю работу в веб версии


![Снимок экрана 2024-06-20 202746](https://github.com/EngelHikari/homework/assets/165402013/18dbebdc-4a9f-4f3c-8f26-a0b19612938a)
![Снимок экрана 2024-06-20 203317](https://github.com/EngelHikari/homework/assets/165402013/42e050e9-a468-4ab8-841a-c6ca01cbe8a4)
![Снимок экрана 2024-06-20 203410](https://github.com/EngelHikari/homework/assets/165402013/6633ae91-9aa0-4f6f-abf8-58d8ae7d08da)
![Снимок экрана 2024-06-20 203531](https://github.com/EngelHikari/homework/assets/165402013/fdc50410-ebee-4ec2-ae11-ccb0c7acad08)
![Снимок экрана 2024-06-20 203553](https://github.com/EngelHikari/homework/assets/165402013/9fe7d7de-9755-42d4-a783-a30198b1ef37)




---

### Задание 3

`Приведите ответ в свободной форме........`

1. `Заполните здесь этапы выполнения, если требуется ....`
2. `Заполните здесь этапы выполнения, если требуется ....`
3. `Заполните здесь этапы выполнения, если требуется ....`
4. `Заполните здесь этапы выполнения, если требуется ....`
5. `Заполните здесь этапы выполнения, если требуется ....`
6. 

```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота](ссылка на скриншот)`

### Задание 4

`Приведите ответ в свободной форме........`

1. `Заполните здесь этапы выполнения, если требуется ....`
2. `Заполните здесь этапы выполнения, если требуется ....`
3. `Заполните здесь этапы выполнения, если требуется ....`
4. `Заполните здесь этапы выполнения, если требуется ....`
5. `Заполните здесь этапы выполнения, если требуется ....`
6. 

```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота](ссылка на скриншот)`
