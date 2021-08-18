# MQTT-IOT
实现云端服务器和客户端工控板之间的消息传输包括发送和接收，其中云服务器使用的是阿里云服务器非阿里云的IOT平台云服务器，所以得提前在阿里云上部署好MQTT服务，这里使用的是开源的EMQX，代码中的client和server事实上都是指代客户端，可以看作一个是发布端另一个是订阅端，但为了节省内存和流量，一个端即定义了发布也定义了订阅，也就是说client和server都既是发布者也是订阅者，中间的云服务器只是作为中介进行消息的转发。

# MQTT Framework  
![MQTT](https://z3.ax1x.com/2021/08/18/fIR8dx.jpg)  

# Environment
- Python3.6
- Socket
- paho-mqtt
- threading

# How to use
- Step1 : 注册阿里云或者其他的云服务器,在服务器上部署[EMQX](https://www.emqx.com/zh/downloads?product=broker)
```
# 下载emqx-centos8-4.3.7-amd64.zip(这里以centOS举例)
$ wget https://www.emqx.com/zh/downloads/broker/4.3.7/emqx-centos8-4.3.7-amd64.zip

# 安装emqk
$ unzip emqx-centos8-4.3.7-amd64.zip

# 后台一直运行emqx,如需停止运行将start改为stop即可
$ ./bin/emqx start
```
- Step2 : 在阿里云界面或其他云服务器界面开放1883/18083/8083端口

| 端口 | 说明 |
| :----:| :----: |
| 1883	 | MQTT/TCP 协议端口 |
| 11883	 | MQTT/TCP 协议内部端口，仅用于本机客户端连接 |
| 8883	 | MQTT/SSL 协议端口 |
| 8083	 | MQTT/WS 协议端口	 |
| 8084	 | 	MQTT/WSS 协议端口|

- Step3 :（可选）下载[MQTT unility](https://repo.eclipse.org/content/repositories/paho-releases/org/eclipse/paho/org.eclipse.paho.ui.app/1.1.1/)来调试云服务器的MQTT是否可行
```
# 输入云服务器的公网IP和开放的端口号1883
# 自定义topic主题和发布的消息内容，并在订阅栏订阅相应的topic
# 如果发布的消息在订阅中接收到说明EMQX搭建成功
```
![paho](https://z3.ax1x.com/2021/08/18/fIoF9P.png)
- Step4 : （可选）在浏览器中输入公网IP+18083端口号可进入EMQX的后端访问界面设置与云服务器的EMQX通信的账号密码  
![UI](https://z3.ax1x.com/2021/08/18/fIHtHg.png)


- Step4 ：在客户端即工控机上运行```python client.py```并设置好相应的参数，其中```server.py```不需要在云服务器上运行，其只是在另外一台设备上进行订阅测试的代码；其中client.py中代码可移植到需要的具有检测功能性代码中即在工控机上执行检测功能的主运行代码中去。

