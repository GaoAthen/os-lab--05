# df -h | df -i
~~~
gao@fedora:/$ df -i
Файловая система  Iнодов IИспользовано IСвободно IИспользовано% Cмонтировано в
/dev/nvme0n1p3         0             0         0              - /
devtmpfs          492726           541    492185             1% /dev
tmpfs             499671             5    499666             1% /dev/shm
tmpfs             819200          1122    818078             1% /run
none                1024             2      1022             1% /run/credentials/systemd-journald.service
none                1024             2      1022             1% /run/credentials/systemd-resolved.service
tmpfs            1048576            38   1048538             1% /tmp
/dev/nvme0n1p2    131072           392    130680             1% /boot
/dev/nvme0n1p3         0             0         0              - /home
tmpfs              99934           175     99759             1% /run/user/1000
/dev/sr0               0             0         0              - /run/media/gao/Fedora-WS-Live-44

gao@fedora:/$ df -h
Файловая система Размер Использовано  Дост Использовано% Cмонтировано в
/dev/nvme0n1p3      23G         5,7G   17G           26% /
devtmpfs           1,9G            0  1,9G            0% /dev
tmpfs              2,0G          92K  2,0G            1% /dev/shm
tmpfs              781M         1,6M  780M            1% /run
none               1,0M            0  1,0M            0% /run/credentials/systemd-journald.service
none               1,0M            0  1,0M            0% /run/credentials/systemd-resolved.service
tmpfs              2,0G         8,0K  2,0G            1% /tmp
/dev/nvme0n1p2     2,0G         387M  1,5G           22% /boot
/dev/nvme0n1p3      23G         5,7G   17G           26% /home
tmpfs              391M         120K  391M            1% /run/user/1000
/dev/sr0           2,7G         2,7G     0          100% /run/media/gao/Fedora-WS-Live-44
~~~
# На каком по счёте файле программа дала сбой
На самом первом файле /dev/nvme0n1p3, данный файл отвечает за раздел на SSD диске
# Ошибка "Нет места"
Она возникает из за того что файловая система использовала все доступные inode
# Пример
Сервер с большим кол-вом маленьких файлов/кэша или сессий, это всё может исчерпать количество inode раньше чем закончится место на диске
