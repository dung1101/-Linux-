# 12 Volume Manager, a real example
```
pvcreate /dev/sdb1
vgcreate vgdb /dev/sdb1
lvcreate -l 100%FREE -n lvol1 vgdb
mkfs -t ext3 /dev/vgdb/lvol1
mkdir /db
mount /dev/sdb1 /db
apt-get install mysql
nano /etc/mysql/my.cnf
...
datadir=/db/mysql
...
systemctl start mysqld
systemctl status mysqld
systemctl enable mysqld
apt-get install git
git clone https://github.com/datacharmer/test_db.git
cd /db/test_db
mysql < employees.sql
mysql < employees_partitioned.sql
mysql  -t < test_employees_md5.sql
pvcreate -f /dev/sdc
pvcreate -f /dev/sdd
lvextend -L +400G /dev/vgdb/lvol1
resize2fs -p /dev/vgdb/lvol1
cd /db/test_db
mysql  -t < test_employees_md5.sql
systemctl stop mysql
systemctl status mysql
tar cvf data_backup.tar *
gzip data_backup.tar
mv data_backup.tar /data_backup_folder
umount /db
e2fsck -ff /dev/vgdb/lvol1
fsadm -e -y resize /dev/vgdb/lvol1 476940M
lvreduce -L 476940M /dev/vgdb/lvol1
vgreduce vgdb /dev/sdd
pvremove /dev/sdd
e2fsck -ff /dev/vgdb/lvol1
mount /dev/vgdb/lvol1 /db
systemctl start mysqld
cd /db/test_db/
mysql  -t < test_employees_md5.sql
```
