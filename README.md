# MQTT-IOT
实现云端服务器和客户端之间的消息传输包括发送和接收，其中云服务器使用的是阿里云服务器非阿里云的IOT平台云服务器，所以得提前在阿里云上部署好MQTT服务，这里使用的是开源的EMQ，代码中的client和server事实上都是指代客户端，可以看作一个是发布端另一个是订阅端，但为了节省内存和流量，一个端即定义了发布也定义了订阅，也就是说client和server都既是发布者也是订阅者，中间的云服务器只是作为中介进行消息的转发。

# MQTT Framework  
![MQTT](https://github.com/FanDady/MQTT-IOT/blob/master/images/1.jpg)  

# Environment
- Socket
- paho-mqtt
- threading

# How to use
- Step1 : 注册阿里云或者其他的云服务器,在服务器上部署[EMQ](https://www.emqx.com/zh/downloads?product=broker)
- Step2 : 在阿里云界面开放1883/18083/8083端口
- Step3 ：可选择下载[MQTT unility](https://repo.eclipse.org/content/repositories/paho-releases/org/eclipse/paho/org.eclipse.paho.ui.app/1.1.1/)来调试云服务器的MQTT是否可行
- Step4 ：先后运行```python server.py```和```python client.py```其中的参数可自行调整

