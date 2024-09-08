Amazon Dynamo DB Token Bucket Algorithm and Bursting

---
![](8.jpg)  
  
Use for ratelimiting clients based on their provisioned capacity  
Tables are provisioned with ReadCapacityUnit as a metric.   
1 RCU = 4kb per sec.  
Throttles clients if no tokens are available.  
![](22.jpg)  
Bursting  
  
![](26.jpg)  
  
![](15.jpg)