# lsblk /dev/loop0
~~~
gao@fedora:~$ lsblk /dev/loop0
NAME      MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
loop0       7:0    0    1G  0 loop 
├─loop0p1 259:4    0  511M  0 part 
└─loop0p2 259:5    0  511M  0 part 
~~~

# Вывод blkid
~~~
/dev/loop0p1: LABEL="DATA1" UUID="c164ced7-6f55-4d7d-aa6f-ff2a68b9244a" BLOCK_SIZE="1024" TYPE="ext4" PARTLABEL="data1" PARTUUID="0950cc46-8683-4258-a855-4db2490c9cc4"
/dev/loop0p2: LABEL="DATA2" UUID="83ab9cb7-1311-4579-a023-7ea06782247a" BLOCK_SIZE="512" TYPE="xfs" PARTLABEL="data2" PARTUUID="581b2bc9-7215-4a8a-a11b-02ef9c0a5061"
~~~

# Вывод df -hT
~~~
gao@fedora:~$ df -hT /mnt/data1 /mnt/data2
Файловая система Тип  Размер Использовано  Дост Использовано% Cмонтировано в
/dev/loop0p1     ext4   469M         141K  440M            1% /mnt/data1
/dev/loop0p2     xfs    447M          35M  413M            8% /mnt/data2
~~~

# Вопрос
После создания файловой системы ext4,место занимается служебной информацией inode, журналом файловой системы и каталогом lost+found
