# ls -li и hard/orig.txt

~~~
root@fedora:/mnt/data1# ls -li
итого 14
13 -rw-r--r--. 2 root root    30 окт 30 18:43 hard.txt
11 drwx------  2 root root 12288 окт 30 18:23 lost+found
13 -rw-r--r--. 2 root root    30 окт 30 18:43 orig.txt
14 lrwxrwxrwx. 1 root root     8 окт 30 18:44 soft.txt -> orig.txt

root@fedora:/mnt/data1# stat orig.txt | head -5
  Файл: orig.txt
  Размер: 30        	Блоков: 2          Блок В/В: 1024   обычный файл
Устройство: 259/4	Инода: 13          Ссылки: 2
Доступ: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Контекст: unconfined_u:object_r:unlabeled_t:s0

root@fedora:/mnt/data1# stat hard.txt | head -5
  Файл: hard.txt
  Размер: 30        	Блоков: 2          Блок В/В: 1024   обычный файл
Устройство: 259/4	Инода: 13          Ссылки: 2
Доступ: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Контекст: unconfined_u:object_r:unlabeled_t:s0

root@fedora:/mnt/data1# cat hard.txt
исходные данные

root@fedora:/mnt/data1# cat soft.txt
исходные данные
~~~

# Почему жёсткая ссылка пережила а символическая нет
Жёсткая - указывает на сам inode, поэтому удаление 1 имени не уничтожит сам файл
Символическая - хранит путь к оригиналу, если удалить оригинал то путь станет недействительным

# Вопрос
Потому что у каждой файловой системы собственный inode
