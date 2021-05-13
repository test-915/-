# SQL

> 语句类型：
>
> 库表构建
>
> 数据增删改
>
> 数据查询



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



### 所有库

```sql
show databases
```



### 当前库

```sql
select database()
```



## 表操作

### 创建表

```sql
create table 表名(
    字段1 类型1(宽度)[约束条件] ,
    字段2...
)
```

[约束条件]:可选unsigned(无符号)，zerofill(零填充，同时无符号);
[宽度]:可选;



### 表结构

```sql
desc 表名
describe 表名
show create table 表名
```



### 修改表

```sql
alter 表名
```



### 复制表

```sql
create 表名
```



### 删除表

```sql
drop 表名
```



### 选择表

```sql
select * from `表名`
```

[*]:可指定字段名；
[表名]:可指定绝对路径；



### 修改引擎

```sql
alter table 表名 engine=引擎
```

[引擎]:innodb、memory(内存引擎)等



## 数操作

### 插入数据

```sql
insert into 表名(
    字段1...
)values(值1...),(值2...)...
```

[字段]:可选，指定字段，不指定则顺序插入；
[值]:可输入多个对象值；



### 更新数据

```sql
update 表名 
set 设置字段='设置值' 
where 条件字段='条件值'
```



### 删除数据

```sql
delete from 表名
where 条件字段=‘条件值’
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
tinyint 	/* 极短 */
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
char		/* 定长，删除尾部空格 */
varchar		/* 变长，保留尾部空格 */
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
enum		/* 枚举 */	enum("参数1","参数2"...)
set			/* 集合 */	/* 与enum同理 */
```



### 日期

```sql
date
time
datetime
timestamp	/* 时间戳 */
year
```



#### 返回当前时间

```sql
now()
```



## 约束条件

> 作用：数据完整性与一致性；

> key包括：主键、外键、索引（index、unique）



### 键

#### 主键

```sql
primary key 	/* pk */
pk = unique + not null
```

> 唯一标识；
>
> 非空；
>
> 一表一主键；



##### 单主键

```sql
create table 表名(
	字段 类型 primary key,
    ...
)
```



##### 复合主键

```sql
create table 表名(
	字段 类型,
	...
	primary key(字段,字...)
)
```



#### 外键

```
foreign key		/* fk */
```

> 表与表之间的关联；
>
> 父表主键 -> 子表外键；



```sql
create table 表名(
	字段 类型,
	...
	foreign key(字段)
	references 外表名(外表字段) 
	/* 
    on update cascade
    on delete cascade
    */
)
/* engine = innodb */
```

[on update cascade]:可选，同步更新；
[on delete cascade]: 可选，同步删除；
[engine]: 默认为innodb;



#### 唯一键

```sql
unique key		/* uk */
```

```sql
/* 示例 */
create table 表名(
	字段1 类型1,
	unique(字段1)
)
```

```sql
/* 自定义键名 */
constraint 键名 unique(字段)
```

> 唯一；
>
> 可空；
>
> 一表多个唯一键；



### 属性

#### 非空

```sql
not null
```

> 设置后不能为空，必须赋值；
>
> 不设置则默认为可空；



#### 自增

```sql
auto_increment
```

> 整型；
>
> 主键；



#### 默认值

```sql
default
```

```sql
/* 示例 */
字段1 enum("值1"...)not null default "值1"
/* 解释：字段1非空，且默认为值1 */
```



#### 无符号

```sql
unsigned
```



#### 零填充

```sql
zerofill
```

