# AIDL 简介
aidl 一般用来进程通讯。一般来说，主要有两种角色，客户端 （Client）和服务端（Server）。

### 服务端
* 一般用来处理客户端的请求，把与客户端通讯的方式抽象成接口，并编写成 AIDL 文件
* 通常服务端需要实现一个 Service，来处理客户端的请求

### 客户端
* 通常我们需要将服务端 的 AIDL 文件 copy 过来，并通过 Intent 的方式来启动服务端的 Service。  
  
## Ex : 通过 app（Clilent） 唤起另外一个 APP （Server），并进行两者之间的通讯。
### 服务端的实现：
* 将请求抽象成接口，并编写 aidl 文件
* 编写一个 Service，实现接口，处理客户端的请求，并将 binder 返回回去；
* 在 AndroidManifet 配置 Service，将我们的 Service 暴露出去。

### 客户端的实现
* 将服务端的 aidl 文件 copy 过来，放在同一个包下。
* 通过服务端 Service 的 Action 启动， 当启动 Service 成功的时候，将服务端返回的 Binder 保存下来并转化成相应的实例。
* 之后如果想与服务端通讯，通过保存下来的 Binder，即可调用服务端的方法。
