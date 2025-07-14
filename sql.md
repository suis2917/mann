Sql针对Null有is NULL和is not NULL两种判断方法

MySQL 使用三值逻辑 —— TRUE, FALSE 和 UNKNOWN。任何与 NULL 值进行的比较都会与第三种值 UNKNOWN 做比较。这个“任何值”包括 NULL 本身！这就是为什么 MySQL 提供 IS NULL 和 IS NOT NULL 两种操作来对 NULL 特殊判断。

任何与 NULL 的比较都返回 UNKNOWN



[黑马MySQL基础篇笔记整理——超详细_黑马mysql笔记-CSDN博客](https://blog.csdn.net/wohuishidalao/article/details/133971522)

### *DDL表数据定义*

![image-20250424134129336](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250424134129336.png)

![image-20250424134143600](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250424134143600.png)



### *DML数据操作*

![image-20250424153841307](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250424153841307.png)

![image-20250424153603940](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250424153603940.png)

![image-20250424134212319](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250424134212319.png)

![image-20250424153527360](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250424153527360.png)



### *DQL表数据查询*

select决定列数，groupby决定行数

![image-20250424134333551](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250424134333551.png)



![image-20250424153719873](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250424153719873.png)

![image-20250424153807422](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250424153807422.png)

![image-20250424153121464](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250424153121464.png)

### *DCL*

​    用来管理数据库用户、控制数据库的访问权限。

![image-20250428181948700](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250428181948700.png)

![image-20250428182026338](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250428182026338.png)

### 函数

​    一段可以直接被另一段程序调用的程序或代码。

![image-20250428182054222](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250428182054222.png)

![image-20250428182122484](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250428182122484.png)

![image-20250428182131404](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250428182131404.png)

### 约束

![image-20250428182158412](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250428182158412.png)

![image-20250428182446531](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250428182446531.png)

#### 外键约束

​    用来让两张表的数据之间建立连接，从而保证数据的一致性和完整性

![image-20250428182459326](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250428182459326.png)

![image-20250428182514564](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250428182514564.png)

```sql
-- 删除更新行为
alter table 表_name add constraint  fk_表_name_status foreign key (status) references user(id) on update cascade on delete cascade ;
alter table 表_name add constraint  fk_表_name_status foreign key (status) references user(id) on update set null on delete set null ;
```

### 多表查询

要消除笛卡尔积，只需要在查询语句的后面加一个where条件即可

![image-20250429134726049](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250429134726049.png)

```sql
# 注意，一定得是连接的另一个表的主键才可以
alter table emp add constraint  fk foreign key (dep_id) references dep(id) on update cascade on delete cascade ;
 
-- 内连接
-- 1、查询每一个员工的姓名，及关联的部门的名称（隐式内连接实现）
-- 表结构：emp, dep
-- 连接条件：emp.dep_id = dep.id
select emp.name, dep.dep from emp, dep  where  emp.dep_id = dep.id;
 
# 一旦对表起了别名，就不能再通过表明来限定字段
select e.name,d.dep from emp e, dep d where e.id = d.id ;
 
-- 2、查询每一个员工的姓名，及关联的部门的名称（显示内连接实现）  ---INNER JOIN ... ON ...
-- 表结构：emp, dep
-- 连接条件：emp.dep_id = dep.id
select e.name, d.dep from emp e inner join dep d on e.dep_id = d.id;
 
select e.name, d.dep from emp e  join dep d on e.dep_id = d.id;
```

![image-20250429135233256](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250429135233256.png)

```sql
-- 外连接
-- 1、查询emp表所有的数据，和对应的部门信息（左外连接）
-- 表结构：emp, dep
-- 连接条件：emp.dep_id = dep.id
select e.*, d.dep from emp e left join dep d on d.id = e.dep_id;
 
-- 2、 查询dep表所有的数据，和对应的员工信息（右外连接）
select e.*, d.* from emp e right join dep d on d.id = e.dep_id;
```



#### 联合查询- union， union all

​    对于 union 查询，就是把多次查询的结果合并起来，形成一个新的查询结果集。

```sql
-- union all ,union
-- 1、将地址在北京的， 和年龄大于 20 岁的员工全部查询
select * from emp where workaddress = '北京'
# union all # 查询结果直接合并
union #查询结果合并并去重
select * from emp where age > 20;
 
# 对于联合查询的多张表的列数必须保持一致，字段类型也需要保持一致
```



#### 嵌套查询

![image-20250502164714816](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250502164714816.png)

![image-20250502164800649](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250502164800649.png)

```sql
-- 列子查询
-- 1、 查询“销售部” 和“研发部” 的所有员工信息
select * from emp where dep_id in (select id from dep where dep = '销售部' or dep = '研发部');
 
-- 2、 查询比销售部所有人工资都高的员工信息
select * from emp where salary > all((select salary from emp where dep_id = (select id from dep where dep = '销售部')));
# all 返回回来的结构都需要满足
 
-- 3、查询比研发部其中任意一人工资高的员工信息
select * from emp where salary > any (select salary from emp where dep_id = (select id from dep where dep = '研发部'));
# any = some
```

```sql
-- 案例
-- 1、查询员工姓名、年龄、部门信息（隐式内连接）
-- 表：emp , dept
-- 连接条件 ： emp.dep_id = dep.id
select e.name,e.age, d.dep from emp e,dep d where e.dep_id = d.id;
 
-- 2、查询年龄大于20的员工姓名、年龄、部门信息 （显示内连接）
-- 表：emp , dept
-- 连接条件 ： emp.dep_id = dep.id
select e.name,e.age,d.dep from emp e join dep d on d.id = e.dep_id where e.age > 20;
 
-- 3、查询拥有员工的部门ID、部门名称 (部门表和员工表交集的部分)
-- 表：emp , dept
-- 连接条件 ： emp.dep_id = dep.id
-- distinct 去重
select distinct d.id, d.dep from emp e,dep d where e.dep_id = d.id;
 
-- 4、查询所有年龄大于25的员工及其归属的部门名称，如果没有分配部门，也要展示出来
-- 表：emp , dept
-- 连接条件 ： emp.dep_id = dep.id
-- 外连接
select e.name,d.dep from emp e left join dep d on d.id = e.dep_id where e.age > 25;
 
-- 5、查询所有员工工资等级
-- 表：emp , salgrade
-- 连接条件 ： emp.salary >= salgrade.losal &&  emp.salary <= salgrade.hisal
select * from emp e ,salgrade s where e.salary >= s.losal &&  e.salary <= s.hisal;
select * from emp e ,salgrade s where e.salary between s.losal and s.hisal;
 
-- 6、查询"研发部"所有员工信息及工资等级
-- 表：emp , salgrade， dep
-- 连接条件 ：e.salary between s.losal and s.hisal; emp.dep_id = dep.id
-- 查询条件：dep.dep = '研发部'
select e.*, s.grade
from emp e,
     dep d,
     salgrade s
where (e.salary between s.losal and s.hisal)
  and e.dep_id = d.id
  and d.dep = '研发部';
 
-- 7、查询"研发部"员工的平均工资
-- 表：emp ,  dep
-- 连接条件 ： emp.dep_id = dep.id
select avg(e.salary)
from emp e,
     dep d
where e.dep_id = d.id
  and d.dep = '研发部';
 
-- 8、查询工资比李四高的员工信息
-- 表：emp
select *
from emp e
where salary > (select e.salary from emp e where e.name = '李四');
 
-- 9、查询比平均工资高的员工信息
-- 表：emp
select *
from emp e
where salary > (select avg(salary) from emp);
 
-- 10、查询低于本部门平均工资的员工
-- 表：emp , dept
-- 连接条件 ： emp.dep_id = dep.id
select *
from emp e2
where e2.salary < (select avg(e1.salary) from emp e1 where e1.dep_id = e2.dep_id);
 
-- 11、查询所有部门的信息，并统计部门的员工人数
select d.id,d.dep ,(select count(*) from emp e where e.dep_id = d.id) '人数' from dep d;   
```

![image-20250502165031583](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250502165031583.png)

### 事务

​    一组操作的集合，它是不可分割的工作单位，事务会把所有的操作作为一个整体一起向系统提交或撤销操作请求，即这些操作要么同时成功，要么同时失败。默认MySQL的事务是自动提交的，也就是说，当执行一条DML语句，MySQL会立即隐式的提交事务。

![image-20250507152034281](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250507152034281.png)

手动：

![image-20250507152048952](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250507152048952.png)

#### 并发事务问题

![image-20250507152113006](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250507152113006.png)

#### 事务隔离级别

​    为解决并发事务问题，设置来了事务隔离级别，下表中从上到下隔离级别越来越高，但是性能越来越差，实际开发中，二者加以权衡使用。

![image-20250507152123682](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250507152123682.png)
