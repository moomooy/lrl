# MySQL数据库软件  

1、安装：  
2、卸载：  
3、配置  
*  MySQL服务启动   
   1、手动  
   2、cmd-->services.msc 打开服务的窗口  
   3、使用管理员打开cmd  
        * net start mysql：启动mysql的服务   
        * net stop mysql:关闭mysql服务  

* MySQL登陆  
1、mysql -uroot -p密码  
2、mysql -hip -uroot -p连接目标  

先创建两张表  

```
CREATE TABLE score (

id int(10) NOT NULL AUTO_INCREMENT,

subject_id int(10) DEFAULT NULL,

student_id int(10) DEFAULT NULL,

score float DEFAULT NULL,

PRIMARY KEY (id)

) ENGINE=InnoDB AUTO_INCREMENT=19 DEFAULT CHARSET=utf8;
```

这其中:NOT NULL 规定该字段不允许为空  
       AUTO_INCREMENT = 100;（ID列从100开始自增）
       UNSIGNED是无符号的意思，代表该字段没有正负  
       default 规定该字段的默认值  
       ENGINE=InnoDB:默认就是这个引擎  
       utf8:这个虽然在my.ini设置过了，但设置的是mysql的的语言编码，而这里创建的时候不设置，就会出现乱码问题，二者的作用域是不一样的，在创建表单的时候，这个charset会作用到这个表上，他代表mysql建立数据库数据表时设定字符集为utf-8  
