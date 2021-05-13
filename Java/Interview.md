# 面试经历的问题  
  
## MySQL  

1.当一张表上有学号成绩,另一张表上有学号姓名,怎么样连接两张表查询出不及格的同学  

首先了解主键和外键  :  
主键(primary key):主键是唯一的，用于标识一张表。
外键(foreign key):存在与外面的主键就是外键,外键可以有多个，用于建立表和表的关系。    


连接语句:  
LEFT JOIN（左连接）：返回包括左表中的所有记录和右表中连接字段相等的记录   

左连接语句:SELECT tb_student.name,tb_class.name FROM tb_student LEFT OUTER JOIN tb_class ON tb_student.classID=tb_class.id;  

RIGHT JOIN（右连接）：返回包括右表中所有记录和左表中连接字段相等的记录  

查询语句:SELECT * FROM tb_score WHERE grade> ANY(SELECT grade FROM tb_score WHERE sID=1);  

## Linux  

1.怎么运用Linux查询多线程在哪个cpu上面运行  
   ps -eo ruser,pid,ppid,lwp,psr,args -L | grep qemu  
   依次在用户ID，进程ID，父进程ID，线程ID，运行该线程的CPU的序号，命令行参数（包括命令本身）  

2.怎么运用Linux查询多线程  
   ps -ef | grep  
   ps -ef:显示所有进程的消息  
   grep是查找输出包含想要的字符串的行
