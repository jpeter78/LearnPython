为了方便的通过网页进行编程，可以在vps部署code-server，也就是网页版vscode
官方git地址
https://github.com/cdr/code-server
# 1. 安装
```
curl -fsSL https://code-server.dev/install.sh | sh
```
# 2. code-server配置
安装好以后，运行
```
code-server
```
会自动在当前用户的根目录下生成.config/code-server/config.yaml，默认是只能通过本机8080浏览，可以修改该文件，允许通过网络访问
```
bind-addr: 0.0.0.0:8080
auth: password
password: 此处修改成你自己的密码，默认是随机生成一个密码
cert: false
```
# 3. 设置开机启动
可以通过systemctl添加服务，设置成开机启动
在/etc/systemd/system/目录下创建code-server.service文件，
```
touch /etc/systemd/system/code-server.service
nano /etc/systemd/system/code-server.service
```
编辑内容为
```
[Unit]  
Description=codeserver  
After=network.target  
   
[Service]  
Type=simple  
ExecStart=/usr/bin/code-server
ExecReload=  
ExecStop=/usr/bin/code-server  
PrivateTmp=true  
   
[Install]  
WantedBy=multi-user.target
```
文件创建好以后，执行语句
```
systemctl enable code-server.service #创建服务
systemctl start code-server # 启动服务
```
# 4. 测试验证
重启vps，过1分钟后，浏览器上直接输入vps地址+端口，看能访问到web版code-server，如果能正常访问，说明已经安装成功。
