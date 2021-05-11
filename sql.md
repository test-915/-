# SQL

## 库操作

### 创建库

```sql
create database [IF NOT EXISTS] 库名
```

[IF NOT EXISTS]:可选，如果不存在，则创建；



### 删除库

```sql
drop database [IF EXISTS] 库名
```

[database]: 也可以是table等等;
[IF EXISTS]: 可选，如果存在，则删除;



### 显示所有库

```sql
show databases
```



### 当前所在库

```sql
select database()
```



## 表操作

### 创建表

```sql
create table 表名(字段1 类型1(宽度)[约束条件] ,字段2...)
```

[约束条件]:可选unsigned(无符号)，zerofill(零填充，同时无符号);
[宽度]:可选;



### 查看结构

```sql
desc 表名
```



### 插入数据

```sql
insert into 表名(字段1...) values(值1...)
```

[字段]:可选，指定字段；



### 选择表

```sql
select * from `表名`
```



### 计算值长度

```sql
length()
select length(字段1)... from 表名
```



### 拼接值

```sql
concat()
select concat(字段1)... from 表名
```



## 数据类型

### 数值

#### 整数

```sql
int
tinyint 	/*极短*/
smallint
mediumint
bigint
```

[约束条件]:unsigned限定只能存正值(无符号，储值翻倍)；
[宽度]:仅为显示宽度；



#### 浮点

```sql
float
double
```

[参数1]:总位数；
[参数2]:小数位；
[宽度]:限制宽度；



#### 定点

```sql
dec
```



#### 位类型

```sql
bit
```



### 字符串

#### 短文本

```sql
char		/*定长，删除尾部空格*/
varchar		/*变长，保留尾部空格*/
```



#### 长文本

```sql
text
tinytext
mediumtext
longtext
```



#### blob

```sql
blob
tinyblob
mediumblob
longblob
```



#### binary

```sql
binary
varbinary
```



#### 选择项

```sql
enum		/*枚举*/
set			/*集合*/
```

​		

### 日期

```sql
date
time
datetime
timestamp	/*时间戳*/
year
```



#### 返回当前时间

```sql
now()
```

