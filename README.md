# ApiTest 介绍
+ API接口测试bash脚本，运行在CentOS7环境下
+ 因为主要文件由bash脚本编写，只要熟悉bash命令，接口测试就非常容易实现批量化，或者做压测，或者二次开发
+ 配置灵活，只需修改run文件的配置，或者复制run为其他名字，改成自己需要的配置，执行对应的命令就行
+ 对于做接口测试的开发人员，测试人员来说，非常高效稳定可信赖

# 原理
+ bash脚本读取文件，和命令行参数，然后执行curl函数请求接口

# 使用实例
```
[root@dhcp-10-100-1-201 send_goods_app]# sh run  Printer_unbind 


curl -H "Content-Type:application/json" -X POST --data '{ "user_id":6, "token":"c6916ff47e6a4b8ca65e2f17c86bfb67", "printer_code":"18170001AL" }' 127.0.0.1:8010/appapi/Printer/unbind


  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   133    0    45  100    88     54    106 --:--:-- --:--:-- --:--:--   106


{"code":200,"msg":"解绑完成","data":true}
```
# 实例说明

+ 在CentOS的/home/ApiTest/send_goods_app目录下执行`sh run  Printer_unbind `，run文件会被执行
+ 然后去读取Printer_unbind中的json内容，然后把内容发送给127.0.0.1:8010/appapi/Printer/unbind，并输入返回数据
+ 127.0.0.1:8010/appapi/在run文件中由host配置


# 文件夹和文件介绍
+ boss、elabel、open_api、send_goods_app四个文件，代表了四个不同项目的API测试文件

+ 每个项目中起关键作用的是 run* 文件，这个文件读取命令行参数提供的文件名后，发送请求到对应的接口

+ Template_delete 类似的文件是代表接口地址，里面的json是提交的参数

+ run*文件中 host='127.0.0.1:8015/api'代表一个项目中，所有接口的URL共同部分


# 本项目也可以拿来学习sh脚本






