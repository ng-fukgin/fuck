
1\. 硬盘检查
--------

### 1.1 确认硬盘

首先，你需要检查新硬盘是否被系统识别。在终端中执行以下命令:

`sudo fdisk -l`

### 1.2 获取UUID

使用以下命令获取硬盘的UUID：

`blkid`

2\. 创建挂载点
---------

### 2.1 挂载目录

选择一个位置创建一个目录，这将是你硬盘的挂载点。例如：

`sudo mkdir /media/mydrive`

### 2.2 赋予用户权限

确保所有用户都能访问该挂载点:

`sudo chown -R $USER:$USER /media/mydrive`

3\. 硬盘挂载
--------

### 3.1 手动挂载

使用/dev路径挂载:

`sudo mount -t ext4 /dev/sdb1 /media/mydrive`

或使用UUID挂载:

`sudo mount -t ext4 UUID=YOUR_UUID /media/mydrive`

4\. 自动挂载
--------

### 4.1 编辑fstab

为了确保每次系统启动时硬盘都能自动挂载，你需要编辑 `/etc/fstab` 文件。

`sudo nano /etc/fstab`

### 4.2 添加自动挂载信息

使用/dev路径，在文件末尾添加以下行:

`/dev/sdb1 /media/mydrive ext4 defaults 0 2`

或使用UUID挂载:

`UUID=YOUR_UUID /media/mydrive ext4 defaults 0 2`

5\. 权限与测试
---------

### 5.1 测试挂载

为了测试硬盘是否正确挂载，你可以重启你的机器并确认硬盘是否已挂载到指定目录。

6\. 结束
------

至此，你已经成功设置了硬盘的挂载。确保每次系统启动时，硬盘都会挂载到指定的目录。