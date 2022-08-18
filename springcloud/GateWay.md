# GateWay   
### 简介   
![img_62.png](img_62.png)     

底层引入了Netty
![img_63.png](img_63.png)      



### 能做什么？   

挡在前面   
![img_64.png](img_64.png)    

负载均衡是nginx    
然后下面是网关     
![img_65.png](img_65.png)    


反向代理
鉴权
流量控制
熔断 
日志监控   


### Gateway是非阻塞io，Zuul是阻塞的  

![img_66.png](img_66.png)    

![img_67.png](img_67.png)       

![img_68.png](img_68.png)    


![img_69.png](img_69.png)      





### 三大核心概念    ：Route路由，Predicate断言，Filter过滤    和RabbitMq很像   
![img_71.png](img_71.png)   
![img_72.png](img_72.png)   

###### GateWay流程   
![img_73.png](img_73.png)   
![img_74.png](img_74.png)    

核心逻辑就是  路由转发和执行过滤链   



