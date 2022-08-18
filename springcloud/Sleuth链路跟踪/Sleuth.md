 #Sleuth：分布式请求链路跟踪   
 这个东西是和zipkin搭配使用    

其实就是zipkin，SpringCloud拿来用了然后叫Sleuth

这个技术就是用来监控这个服务走过了多少个微服务模块，这样出问题也能找到  
常用来弄日志系统模块             


![img_19.png](Sleuth_img/img_19.png)     

![img_20.png](Sleuth_img/img_20.png)    

Sleuth监控，zipkin展示控制台     

zipkin 9411端口访问    
下载jar包就行，然后java -jar   ******.jar    
![img_23.png](Sleuth_img/img_23.png)    





链路图   

![img_21.png](Sleuth_img/img_21.png)       
 
![img_22.png](Sleuth_img/img_22.png)





搭建   
引入依赖   
![img_24.png](Sleuth_img/img_24.png)    



改yaml文件 
![img_25.png](Sleuth_img/img_25.png)      


用order调用payment
![img_26.png](Sleuth_img/img_26.png)      
![img_27.png](Sleuth_img/img_27.png)    