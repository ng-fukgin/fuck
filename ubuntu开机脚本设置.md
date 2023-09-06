# 启动脚本设置详细指南
## 1. 脚本基础
### 1.1 创建脚本
在您选择的目录中创建一个名为 setup.sh 的文件：
```bash
touch /path/to/your/setup.sh
```
### 1.2 添加脚本内容
使用您喜欢的文本编辑器打开该文件，例如：

```bash
nano /path/to/your/setup.sh
```
## 2. 脚本内容
### 2.1 基础结构
您的脚本应该以 #!/bin/bash 开始，这是一个特殊的标记，指示系统使用 /bin/bash 来执行该脚本。

### 2.2 进入工作目录
使用 cd 命令进入您的Python脚本所在的目录：
```bash
cd /desired/directory/path/
```
###  2.3 激活conda环境
如果您使用conda管理Python环境，您可以这样激活它：
```bash
source /path/to/conda/bin/activate your_conda_environment_name
```
### 2.4 运行Python脚本
同步运行：这意味着脚本将等待Python程序完成才继续执行。只需使用以下命令：
```bash
python your_python_script.py
```
### 2.5 异步运行：这意味着脚本将立即继续执行，而不管Python程序是否完成。只需使用以下命令：
```bash
python your_python_script.py &
```
### 2.6 退出conda环境
如果您使用conda管理Python环境，您可以这样退出它：
```bash
source /path/to/conda/bin/deactivate
```
### 2.7 退出脚本
您可以使用 exit 命令退出脚本：
```bash
exit
```
## 3. 脚本权限
### 3.1 添加可执行权限
使用 chmod 命令添加可执行权限：
```bash
chmod +x /path/to/your/setup.sh
```
### 3.2 检查权限
使用 ls 命令检查权限：
```bash
ls -l /path/to/your/setup.sh
```
### 3.3 运行脚本
使用 ./setup.sh 命令运行脚本：
```bash
./setup.sh
```
## 4. 脚本设置
### 4.1 设置开机自启动
使用 crontab 命令设置开机自启动：
```bash
crontab -e
```
### 4.2 添加开机自启动
在打开的文件中添加以下内容：
```bash
@reboot /path/to/your/setup.sh
```
### 4.3 保存并退出
使用 Ctrl + X 保存并退出。
### 4.4 检查开机自启动
使用 crontab 命令检查开机自启动：
```bash
crontab -l
```
## 5. 脚本设置
### 5.1 使用Startup Applications设置开机自启动
打开 Startup Applications Preferences：
```bash
gnome-session-properties
``` 
### 5.2 添加开机自启动
点击 Add 按钮，然后输入以下内容：
```bash
Name: Setup
Command: /path/to/your/setup.sh
Comment: Setup script
```
### 5.3 保存并退出
点击 Add 按钮保存并退出。
### 5.4 检查开机自启动
使用 Startup Applications Preferences 检查开机自启动：
```bash
gnome-session-properties
```
## 6. 脚本设置  
### 6.1 使用rc.local设置开机自启动
打开 rc.local 文件：
```bash
sudo nano /etc/rc.local
```
### 6.2 添加开机自启动
在 exit 0 之前添加以下内容：
```bash
/path/to/your/setup.sh
```
### 6.3 保存并退出
使用 Ctrl + X 保存并退出。
### 6.4 检查开机自启动
使用 cat 命令检查开机自启动：
```bash
cat /etc/rc.local
```
## 7. 脚本设置
### 7.1 使用systemd设置开机自启动
打开 systemd 文件：
```bash
sudo nano /etc/systemd/system/setup.service
```
### 7.2 添加开机自启动
添加以下内容：
```bash
[Unit]
Description=Setup

[Service]
ExecStart=/path/to/your/setup.sh

[Install]
WantedBy=multi-user.target
```
### 7.3 保存并退出
使用 Ctrl + X 保存并退出。
### 7.4 检查开机自启动
使用 cat 命令检查开机自启动：
```bash
cat /etc/systemd/system/setup.service
```
### 7.5 重新加载systemd
使用 systemctl 命令重新加载systemd：
```bash
sudo systemctl daemon-reload
```
### 7.6 启用开机自启动
使用 systemctl 命令启用开机自启动：
```bash
sudo systemctl enable setup.service
```
### 7.7 检查开机自启动
使用 systemctl 命令检查开机自启动：
```bash
sudo systemctl is-enabled setup.service
```
### 7.8 重启系统
使用 reboot 命令重启系统：
```bash
sudo reboot
```
### 7.9 检查开机自启动
使用 systemctl 命令检查开机自启动：
```bash
sudo systemctl status setup.service
```

