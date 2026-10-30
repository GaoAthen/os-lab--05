# ./test.sh
~~~
До
root@fedora:/mnt/data1# ./test.sh
скрипт запустился

После
root@fedora:/# /mnt/data1/test.sh
bash: /mnt/data1/test.sh: Отказано в доступе
~~~

# Вывод findmnt
~~~
root@fedora:/# findmnt /mnt/data1 -o TARGET,OPTIONS
TARGET     OPTIONS
/mnt/data1 rw,relatime,seclabel
/mnt/data1 rw,noexec,relatime,seclabel
~~~

# Связь с 4 лекцией
noexec для /tmp полезен тем, что он препятствует запуску исполняемых файлов из временного раздела,куда потенциально могут попасть вредоносные программы

# Опции nosuid/nodev
`nosuid` - Запрещает применение SUID/SGID-битов
`nodev` - запрещает использование файлов устройств на разделе
