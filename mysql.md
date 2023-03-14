# mysql

` net start mysql80 `   启动mysql  
` net stop mysql80 `   停止mysql  

`  mysql -u root -p `   进入mysql的root账户 wt  


## DDL
> Data Definition Language

#### 查询
`show databases;` 查询所有数据库 
` select database(); `  查询当前数据库  
`show tables;`  查询当前数据库所有表  
` desc tableName_; ` 查询表结构  
`show create table tableName_; `查询指定表的建表语句  


#### 创建
`create database [if not exists] databaseName_ [default charset] [collate] ;`创建数据库  

```
create table tableName_(
    fieldName1_ fieldType1_ [constraint1_ constraint2_ ...] [comment 'comment_'],
    fieldName2_ fieldType2_ [constraint1_ constraint2_ ...] [comment 'comment_'],
    fieldName3_ fieldType3_ [constraint1_ constraint2_ ...] [comment 'comment_'],
    ...
    fieldNamen_ fieldTypen_ [constraint1_ constraint2_ ...] [comment 'comment_']
)[comment 'comment_'];
```
创建表  

##### 数据类型
||||
|--|--|--|
|tinyint    |1 byte|tinyint unsigned
|smallint   |2 bytes|smallint unsigned
|mediumint  |3 bytes|mediumint unsigned
|int/integer|4 bytes|int unsigned
|bigint     |8 bytes|bigint unsigned
|float      |4 bytes|float(m,d)
|double     |8 bytes|double(m,d)
|decimal||

![](/mysqlNotePicture/mysqlNote1.png)  


![](/mysqlNotePicture/mysqlNote2.png)  

#### 修改
`alter table tableName_ add fieldName_ fieldType_ field [comment 'comment_'] [constraint_];` 添加字段
;`alter table tableName_ modify fieldName_ newFieldType_` 修改数据类型  
`alter table tableName_ change oldFieldName_ newFieldName_ fieldType_ [comment 'comment_'] [constraint_];`  修改字段名与类型  
`alter table tableName_ rename to newTableName_; ` 修改表名  


#### 删除
` drop database [if exists] databaseName_; `    删除数据库  
` drop table [if exists] tableName_; `  删除表  
` alter table tableName_ drop fieldName_;` 删除字段  
`truncate table tableName_; `   重置表,清空表数据,表结构不变  

#### 使用
` use databaseName_; `




## DML
> Data Manipulation Language

#### 添加

`insert into tableName_ (fieldName1_,fieldName2,...) values (data1_,data2_,...); `    给指定字段添加数据  
`insert into tableName_ (fieldName1_,fieldName2,...) values (data11_,data12_,...),(data21_,data22_,...),...; `    给指定字段批量添加数据  

`insert into tableName_ values (data1_,data2_,...); `    给全部字段添加数据  
`insert into tableName_ values (data1_,data2_,...),(data21_,data22_,...),...; `    给全部字段批量添加数据  

#### 修改

` update tableName_ set fieldName1_=data1,fieldName2_=data2,... [where condition_]; `   修改符合条件的数据  


#### 删除

`delete from tableName_ [where condition_];`




## DQL
> Data Query Language

```
select [distinct] fileName1_ [AS nickName1_],fileName2_ [AS nickName2_],...
from tableName_ [where condition_]  
[group by fileName_] 
[having condition_] 
[order by fieldName1_ asc,fieldName2_ desc,...] 
[limit number1_,number2_];      -- (number1_,number1_+number2_) number1_>=0  

```

>![](/mysqlNotePicture/mysqlNote3.png/)
[where regex .*]  

![](/mysqlNotePicture/mysqlNote4.png)  

## 多表查询  

- 多表关系  
1-n     1<-n  
1-1     1->1  
n-n     n<-m->n  

- 多表查询  
`select...from tableName1_ nickName1_,tableName2_ nickName2_... where ...;  `
`select...from tableName1_ nickName1_ [inner] join tableName2_ nickName2_ on condition_ ...;`  
`select...from tableName1_ nickName1_ left join tableName2_ nickName2_ on condition_ ...;`  
`select...from tableName1_ nickName1_ right join tableName2_ nickName2_ on condition_ ...;`  

- 联合查询 
```
select ...
union [all]  
select ...;
```



## DCL
> Data Control Language

`use mysql;` + `select * from user; `  查询用户  
`create user 'username_'@'hostname_' identified by 'passworld'; `   创建新用户  
`alter user 'username_'@'hostname_' identified with mysql_native_passworld by 'newPassworld'; `   修改用户密码   
`drop user 'username_'@'hostname_'; `   删除用户  
`grant permissions_ on databaseName_.tableName_ to 'username_'@'hostname_';`    授予权限  
`revoke permissions_ on databaseName_.tableName_ to 'username_'@'hostname_';`    删除权限  

![](/mysqlNotePicture/mysqlNote5.png)  


## 函数
>![](/mysqlNotePicture/mysqlNote6.png)  
rtrim   去除右边空格  
ltrim   去除左边空格  

![](/mysqlNotePicture/mysqlNote7.png)  
![](/mysqlNotePicture/mysqlNote8.png)  
![](/mysqlNotePicture/mysqlNote9.png)  

## 约束
>![](/mysqlNotePicture/mysqlNote10.png)  
auto_increment  自增  

`alter table tableName_ add constraint foreignKeyName_ foreign key (childFileName_) references parentTableName_(parentFileName_);`  添加外键  

## 事务

`select @@autocommit;`  查看事务提交方式  
`set @@autocommit=0;`   设置是否(1/0)自动提交  

`begin;`    `start transaction;`    开启事务  

`commit;` 提交事务  
`rollback;`   回滚事务  

`select @@transaction_isolation;`   查看事务提交等级  
`set [session|global] transaction isolation level {read uncommitted | read committed | repeatable read | serializable };`   设置事务提交等级  
![](/mysqlNotePicture/mysqlNote11.png) 

