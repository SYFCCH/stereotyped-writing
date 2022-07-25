

### 什么是stream     
![img.png](img.png)    
![img_2.png](img_2.png)    
inputs就是消费者，outputs就是生产者   

### 编码常用注解   
![img_1.png](img_1.png)   

Binder:绑定器，方便连接中间件，屏蔽差异，rabbitmq中的交换机      
channel: 类似中间件中的队列,通过channel对队列进行配置      
Source和Sink  
![img_3.png](img_3.png)     




然后是要用到的注解   
![img_4.png](img_4.png)      


# 实战   

pom文件  
![img_6.png](img_6.png)   
如果要切换成kafka只要pom文件最后rabbit改成kafka就行了   

yml文件   
![img_5.png](img_5.png)     



## 生产者模块

#### 业务

##### 发送消息接口  
![img_7.png](img_7.png)   

##### 发送消息接口实现类   
开发套路：   ![img_11.png](img_11.png)    


流程1： Source      
![img_9.png](img_9.png)       
加上注解，知道理论知识然后进行实操   
生产者这边得有Source，然后要用信道  和 绑定器连接消息中间件   

于是我们就用到了@EnableBinding将channel和Exchange绑定在一起    

这个@EnableBinding就是框架图中的Outputs   

流程2：配置信道 channel  
![img_12.png](img_12.png)   

![img_13.png](img_13.png)    



##### Controller  

就调用下之前写的类的方法就好了   
![img_14.png](img_14.png)   



## 消费者模块   
yml文件要把output改为input   
![img_15.png](img_15.png)    

#### 业务  


![img_16.png](img_16.png)      

发送消息的时候，是String类型的message，消费的时候，也要是String，所以Message<String>   



