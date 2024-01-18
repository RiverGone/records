**target**:https://gitee.com/heyewei/JFinalcms

version: v5.0.0

 A SQL injection vulnerability exists in the /admin/admin interface.  
A SQL injection vulnerability exists in JFinalcms via  /admin/admin name parameter, which can be directly concatenated into an SQL statement from the frontend.

![image-20240118224724189](img/image-20240118224724189.png)

The AdminControl module passes to the findPage function without any string filtering after receiving the name parameter, which leads to the generation of sql injection:

![image-20240118225026863](img/image-20240118225026863.png)



Payload: ` name=' AND (SELECT 2522 FROM (SELECT(SLEEP(5)))qFTY) AND 'wguW'='wguW`

![sqlmap-1](img/sqlmap-1.png)

As shown in the figure below, sensitive user information stored in the database can be obtained by using sql injection attacks:

![image-20240118230936057](img/image-20240118230936057.png)





