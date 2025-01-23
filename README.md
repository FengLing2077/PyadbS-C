# PyadbS-C
一个简单的Python脚本以实现自动连接安卓设备进行无线调试

## 功能
这个脚本可以做到启动后循环检查（3秒一次）目标安卓设备与本机的连接情况，并在断连/连接时产生反应
### 连接
当设备连接上本机时，会运用Plyer软件库发送一个WindowsToast提醒

![image](https://github.com/user-attachments/assets/c66a55ba-1b62-4ece-aae3-12e35b790b19)

### 断连
当设备与本机的连接处于offline状态时，循环尝试连接（1.5秒一次）到目标设备并通知设备断连，如果尝试失败则输出ADB报错信息

![image](https://github.com/user-attachments/assets/33f8c279-0d75-4882-a8b0-59e9019cecd0)

这些操作在终端中是这样的

![image](https://github.com/user-attachments/assets/2e439063-37e5-44f7-9ce5-8309155713af)

## 如何使用？
1，确保正确安装ADB与Python3.12+ 并添加入PATH （都用这个脚本了应该不可能没ADB和Py部署吧）

 

2，先将你的设备ADB连接本机，输入如下代码以为你的设备创建一个常驻连接端口

（重启后会失效，如果需要永久常驻需要root权限，详细请Google）
```
adb tcpip [HOST]         
```
[HOST]部分改成你想要的端口，例如'11451'，'0721'等

 

3，安装Python软件包Plyer
```
pip install plyer
```

 

4，下载Release页中的 asc.py

 

5，在脚本内进行配置

![image](https://github.com/user-attachments/assets/8e0e6b9f-cdeb-4fd1-ab0d-3197786e4e09)

将第82行的设备IP改成目标安卓设备的IPV4地址
将第83行的设备IP改成你设置的端口
如果需要可以更改84,85行的间隔时间


5.5，额外的美化配置

有些时候ADB获取到的设备名并不是我们想要的，比如我使用的是iQOO10但ADB获取到的是设备型号V2217A，为了解决这种情况我在脚本开头写了个修正设备名称的字典


![image](https://github.com/user-attachments/assets/157fc7bf-e80d-4894-a913-c425566f80e3)


默认包含我的iQOO10设备，当然，你可以进行自定义添加，语法为
```
"ADB获取到的设备名": "你想要显示的设备名",
```
我认为我写的还是很简单易懂的，如果实在拿不准如何添加可以直接修改已经有的iQOO10字典，前面为ADB获取的名称，后面为修正后的名称，修正名称可以随便你来取


## 吐槽

这个脚本简陋的没边了，除了能运行我很难编一个优点出来

但毕竟主要是个人用，能跑就行了...

![da8792278cba53c8baa82e449916c361](https://github.com/user-attachments/assets/005efaf9-5185-462c-8d03-a767f43b4e9c)

