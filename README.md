# MQTT-IOT
实现云端服务器和客户端之间的消息传输包括发送和接收，其中云服务器使用的是阿里云服务器非阿里云的IOT平台云服务器，所以得提前在阿里云上部署好MQTT服务，这里使用的是开源的EMQ，代码中的client和server事实上都是指代客户端，可以看作一个是发布端另一个是订阅端，但为了节省内存和流量，一个端即定义了发布也定义了订阅，也就是说client和server都既是发布者也是订阅者，中间的云服务器只是作为中介进行消息的转发。

# MQTT Framework
![](https://github.com/FanDady/MQTT-IOT/blob/images/1.jpg)

# How to use
- 注册阿里云或者其他的云服务器
