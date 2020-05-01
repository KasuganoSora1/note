# 如何提升数据库性能

## 1.对数据的删除和更新使用批量模式

## 2.使用SQL服务器的自动分类功能

使用Switch 来代替 delete 和 insert。相对于delete 和 insert 大量的数据，你只更改了元数据
数据库中并没有switch函数，文中所说的很有可能是select * case where then when then语句

## 3.将标量函数转换为表值
|聚合函数|时间函数|标量值函数|表值函数|
|--------|--------|-----------|-------|
|AVG|DATEADD|式1|式2|
|COUNT|DATEDIFF|||
|MAX|DATENAME|||
|MIN|DATEPART|||
|SUM|DAY|||
||GETDATE|||
||GETUTCDATE|||
||MONTH|||

**式1**<br>
CREATE FUNTION function_name<br>([{@parameter_name parameter_data_type [=default]}[,...n]])<br>RETURNS TABLE<br>[WITHENCRYPTION]<br>[AS]<br>RETURN(select_statement)<br>
**式2**<br>
CREATE FUNTION function_name<br>([{@parameter_name parameter_data_type [=default]}[,...n]])<br>RETURNS TABLE<br>AS<br>RETURN(select_statement)<br>

## 4.使用case替代 UPdate

## 5.减少嵌套视图以减少延迟

## 6.数据预分级

## 7.使用临时表

## 8.避免直接使用他人代码

## 9.避免使用否定搜索

## 10.避免使用cursor(游标)

避免使用游标，必要时可以使用临时表替代

## 11.总是select你所需要的数据，对不需要的数据不要select

## 12.使用系统表中rows来计数

## 13.避免让数据库遍历整个数据表

比如 判断一个数据是否存在。<br>
```set @ct=select * from T1; if @ct>0 begin<Dosomething>END ```<br>
这种方法就没又另外一种方法好<br>
``` if Exists(select 1 from T1) BEGIN<Dosomething>END ```<br>
因为第一种方法数据库会将数据库中的数据进行遍历

### 14.尽量避免使用GUID（全局唯一同意标识）

### 15.避免使用触发器

### 16.避免double dip

什么是double dip。先将查询的数据放在临时表上，然后将大型表与临时表连接在一起。这个过程被称为double dip。

### 17.尽可能的使用存储过程

### 18.避免ORM

### 19.Go Slow 

### 20.尽量少用curlsor

### 21.使用AWR 和 ADDM

### 22.避免使用关键字 DISTINCT
