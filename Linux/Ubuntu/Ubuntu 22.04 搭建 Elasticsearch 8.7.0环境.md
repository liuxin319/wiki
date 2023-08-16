# 下载安装包 

- 下载地址：[https://www.elastic.co/cn/downloads/past-releases/elasticsearch-8-7-0](https://www.elastic.co/cn/downloads/past-releases/elasticsearch-8-7-0)
- 选择符合的版本下载
![1684744735950.png](..%2F..%2Fimages%2Flinux%2Fubuntu%2F1684744735950.png)

# 解压压缩包
```
tar -zxvf elasticsearch-8.7.0-linux-x86_64.tar.gz
```
![1684744735951.png](..%2F..%2Fimages%2Flinux%2Fubuntu%2F1684744735951.png)

# 修改elasticsearch.yml配置
## 进入config文件夹
```
cd elasticsearch-8.7.0/config/
```
## 编辑elasticsearch.yml
```
vim elasticsearch.yml
```
## 去掉network.host和http.port 注释
![1684744735952.png](..%2F..%2Fimages%2Flinux%2Fubuntu%2F1684744735952.png)
## 启动服务
```
./bin/elasticsearch
```
![1684744735953.png](..%2F..%2Fimages%2Flinux%2Fubuntu%2F1684744735953.png)
## 访问服务 http://ip:port 响应数据启动成功
![1684744735954.png](..%2F..%2Fimages%2Flinux%2Fubuntu%2F1684744735954.png)
### 启动报错
#### 虚拟内存过低
```
node validation exception                                                                                                                                                              
[1] bootstrap checks failed. You must address the points described in the following [1] lines before starting Elasticsearch.                                                                                                                                
bootstrap check failure [1] of [1]: max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]                                                                                                                             
ERROR: Elasticsearch did not exit normally - check the logs at /opt/elasticsearch-8.7.0/logs/elasticsearch.log
```
![1684744735955.png](..%2F..%2Fimages%2Flinux%2Fubuntu%2F1684744735955.png)

- 编辑 /etc/sysctl.conf 
```
sudo vim /etc/sysctl.conf 
```

- 添加配置
```
vm.max_map_count=655360
```

- 保存修改
```
sudo sysctl -p
```
#### 安全验证访问 http://ip:9200 无反应
![1684744735956.png](..%2F..%2Fimages%2Flinux%2Fubuntu%2F1684744735956.png)

- 编辑elasticsearch.yml
```
vim config/elasticsearch.yml
```

- 将安全验证改为flase
![1684744735957.png](..%2F..%2Fimages%2Flinux%2Fubuntu%2F1684744735957.png)

