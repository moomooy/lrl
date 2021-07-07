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

* Mysql退出  
1、exit  
2、quit  

* Mysql目录结构  
 1、MySQL的安装目录  
   * 配置文件 my.ini  
2、MySQL数据目录  
 * 几个概念  
     * 数据库：文件夹 
     * 表：文件  
     * 数据：  

# SQL  

1、什么是SQL  
   Structured Query Language：结构化查询语言   
   其实就是定义了操作所有关系型数据库的规则，每一种数据库操作的方式存在不太一样的地方就是，称为“方言”   


2、SQL通用语法  
&emsp; 1、SQL语法可以单行或者多行书写，以分号结尾   
&emsp; 2、可使用空格和缩进来增强语句的可读性  
&emsp; 3、MySQL数据库的SQL语句不分大小写，关键字建议用大写  
&emsp; 4、三种注释  
        * 单行注释：-- 注释内容或者 # 注释内容  
        * 多行注释：/*  注释  */

3、SQL的分类  

1）DDL(Date definition language)数据定义语言  
&emsp; 可以用来定义数据库对象：数据库，表，列等，关键字：create，drop，alter等   
2）DML(Date definition language)数据操作语言  
&emsp; 用来对数据库中表的数据进行增添删改，关键字：insert，delete，update等   
3）DQL(Date Query Language)数据查询语言  
&emsp; 用来查询数据中表的记录(数据)。关键字：select，where  
4）DCL(Date COntrol Language)数据控制语言(了解)  
&emsp; 用来定义数据库的访问权限和安全级别，及创建用户。关键字：GRANT，REVOKE等  

## DDL操作数据库、表   

#### 操作数据库：CRUD   

&emsp; 1、C（creat）：创建  
*  创建数据库：  
create datebase 数据库名臣； 

*  创建数据库，判断不存在，再创建   
creat datebase if not exists 数据库名称；  
*  创建数据库并指定字符集  
creat datebase 数据库名称 character set 字符集名；  
*  创建db4数据库，判断是否存在，并制定字符集为gbk  
creat datebase if not exists db4  character set gbk；  

2、R(Retrieve):查询  
* 查询所有数据库的名称：  
show datebases；
* 查询某个数据库的字符集：查新某个数据库的创建语句  
show create datebase 数据库名称；  

3、U(Update):修改  
* 修改数据库的字符集  
alter datebase 数据库名称 character set 字符集名称；  

4、D(Delete)：删除  
* 删除数据库  
Drop datebase 数据库名称；  
* 判断数据库存在，存在再删除  
drop datebase if exists 数据库名称；  

5、使用数据库  
* 查询当前正在使用的数据库名称  
select datebase();
* 使用数据库  
use 数据库名称   

#### DDL操作表  

1、C（creat）：创建  
语法：  
  create table 表名(
          列名1 数据类型1，
          列名2 数据类型2，
          ...
          列名n 数据类型n
  );   


数据库类型：  
int ： 数据类型  
* age int,  
double : 小数类型  
* score double(5,2)  
date:日期，只包含年月日，yyyy-MM-dd  
datetime：日期，包含年月日时分秒 yyyy-MM-dd HH-mm-ss  
timestamp：时间错类型，包含年月日时分秒 yyyy-MM-dd HH-mm-ss  
* 如果将来不给这个字符段赋值，或者赋值为null，则默认使用当前的系统时间，来自动赋值  
varchar：字符串  
* name varchar(20);姓名最大20个字符   
* zhangsan  8个字符，张三 2个字符  

* 创建表  
create table student(
        id int,  
        name varchar(32),
        age int,
        score double(4,1),
        birthday date,  
        insert_time timestamp
);
* 复制表： creat table 表名 like 被复制表名；

2、R（Retrieve）：查询  
* 查询某个数据库中所有的表名称：show tables；  
* 查询表结构：desc 表名；  

3、U(Update):修改   
&emsp; 1、修改表名：alter table  表名  rename to 新的表名；  
&emsp; 2、修改表的字符集：alter table 表名 character set 字符集名称； 
&emsp; 3、添加一列 ：alter table 表名 add 列名 数据类型；  
&emsp; 4、修改列名称 类型： alter table 表名 change 列名 新列名 新数据类型；  
                          alter table 表名 modify 列名 新数据类型；  

4、；删除列  
alter table 表名 drop 列名；



4、D(Delete)：删除  
* drop table 表名；  
* drop table if exists 表名；

## DML_增删改表  

1、添加数据：  
* 语法：  
&emsp; insert into 表名(列名，列名2，...列名n) value (值1，值2，...值n);  

注意：  
&emsp; 1、列名和值要一一对应。  
&emsp; 2、如果表名后，不定义列名，则默认给所有列添加值  
&emsp; &emsp;insert into 表名 value(值1，值2，...值n);  
&emsp; 3、出了数字类型，其他类型需要使用引号（单双都可以）引起来  


2、删除数据  
* 语法  
&emsp; delete from 表名 [where 条件]  
* 注意：  
&emsp; 1、如果不加条件，则删除表中所有记录。  
&emsp; 2、如果要删除所有记录   
&emsp; &emsp;1、delete from 表名;--不推荐使用，有多少条记录就会执行多少条记录，效率很慢。  
&emsp; &emsp;2、TRUNCATE TABLE 表名；--推荐使用，效率高，先删除表，然后再创建一张一模一样的表  

3、修改数据  
* 语法：  
&emsp; update 表名 set 列名1 = 值1 ，列名2 = 值2，...[where 条件];  
* 注意：如果不加任何条件，则会将表中所有记录全部修改    

## DQL_查*询表中的记录  
* select * from 表名;  
 
1、语法 ：  
select 字段列表  
from 表名列表  
where 条件列表  
group by  分组字段  
having 分组之后的条件  
order by 排序  
limit 分页限定  
