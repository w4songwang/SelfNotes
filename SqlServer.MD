### 用SQL SERVER取分组数据第一条

``` sql

--1、创建测试表及插入数据：
create table test
(id int,
name varchar(10),
score int,
classname varchar(20));
 
insert into test values (1,'张三',100,'一班');
insert into test values (2,'李四',89,'一班');
insert into test values (3,'王五',97,'一班');
insert into test values (4,'赵六',87,'二班');
insert into test values (5,'孙七',94,'二班');
insert into test values (6,'杨八',76,'二班');
--2、查出每个班级的成绩第一名，执行以下语句：
select t.* from
(select test.*,row_number() over (partition by classname order by score desc) rn 
from test) t
where rn=1;

```
### Sql Server合并多行询数据到一行：使用自连接、FOR XML PATH('')、STUFF或REPLACE函数(https://www.cnblogs.com/xiaotao726/p/6694645.html)
