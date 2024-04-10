#数据库复习

##基础知识总结
#
关系(Relation): 一个关系通常是一张表
元组(Tuple): 表中的每行(Row)
码(Key): 码就是能唯一标识实体的属性，对应表中的列
候选码(Candidate key)：若关系中的某一属性或属性组的值能唯一的标识一个元组，而其任何、子集都不能再标识，则称该属性组为候选码。例如：在学生实体中，“学号”是能唯一的区分学生实体的，
同时又假设“姓名”、“班级”的属性组合足以区分学生实体，那么{学号}和{姓名，班级}都是候选码
主码(Primary Key): 主码也叫主键。主码是从候选码中选出来的。 一个实体集中只能有一个主码，但可以有多个候选码
外码(Foreign key): 外码也叫外键。如果一个关系中的一个属性是另外一个关系中的主码则这个属性为外码
主属性(Prime attribute)：候选码中出现过的属性称为主属性。比如关系 工人（工号，身份证号，姓名，性别，部门）. 显然工号和身份证号都能够唯一标示这个关系，
所以都是候选码。工号、身份证号这两个属性就是主属性。如果主码是一个属性组，那么属性组中的属性都是主属性
非主属性(Nonprime attribute): 不包含在任何一个候选码中的属性称为非主属性。比如在关系——学生（学号，姓名，年龄，性别，班级）中，主码是“学号”，
那么其他的“姓名”、“年龄”、“性别”、“班级”就都可以称为非主属性

#ER 图 [Entity Relationship Diagram]
实体(Entity): [Row]通常是现实世界的业务对象，当然使用一些逻辑对象也可以。比如对于一个校园管理系统，会涉及学生、教师、课程、班级等等实体。在 ER 图中，实体使用矩形框表示
属性(Attribute): 即某个实体拥有的属性，属性用来描述组成实体的要素，对于产品设计来说可以理解为字段。在 ER 图中，属性使用椭圆形表示
联系(Relation):即实体与实体之间的关系，在 ER 图中用菱形表示，这个关系不仅有业务关联关系，还能通过数字表示实体之间的数量对照关系。例如，一个班级会有多个学生就是一种实体间的联系

同一门课程也可以被若干人选择，所以它们之间的关系是多对多（M: N）。另外，还有其他两种实体之间的关系是：1 对 1（1:1）、1 对多（1: N）

#数据库规范
1NF 属性不可再分
-no table column can have tables as values
-属性不可再分 无重复列(column)
-不能再被分割，也就是这个字段只能是一个值，不能再分为多个其他的字段了。1NF 是所有关系型数据库的最基本要求 ，
也就是说关系型数据库中创建的表一定满足第一范式

2NF 1NF 的基础之上，消除了非主属性对于码的部分函数依赖
-is a fundamental concept of database normalization that helps
remove partial dependencies in your relational database

3NF
-It deals with transitive dependencies and improves data integrity through effective information organization

#主键和外键区别是什么
主键(Primary Key)：主键用于唯一标识一个元组，不能有重复，不允许为空。一个表只能有一个主键
外键(Foreign Key): 外键用来和其他表建立联系用，外键是另一表的主键，外键是可以有重复的，可以是空值。一个表可以有多个外键[一般会被ban掉]

#储存过程(Stored Procedure)
-不咋用
我们可以把存储过程看成是一些 SQL 语句的集合，中间加了点逻辑控制语句。存储过程在业务比较复杂的时候是非常实用的，比如很多时候我们完成一个操作可能需要写一大串 SQL 语句，这时候我们就可以写有一个存储过程，这样也方便了我们下一次的调用。
存储过程一旦调试完成通过后就能稳定运行，另外，使用存储过程比单纯 SQL 语句执行要快，因为存储过程是预编译过的

drop, delete and truncate
-drop(丢弃数据): drop table 表名 ，直接将表都删除掉，在删除表的时候使用[Remove table]
-truncate (清空数据) : truncate table 表名 ，只删除表中的数据，
再插入数据的时候自增长 id 又从 1 开始，在清空表中数据的时候使用[Empty table]
delete（删除数据） : delete from 表名 where 列名=值，删除某一行的数据，如果不加 where 子句和truncate table 表名作用类似

注:truncate 和 drop 属于 DDL(数据定义语言)语句，操作立即生效，原数据不放到 rollback segment 中，不能回滚，操作不触发 trigger。
而 delete 语句是 DML (数据库操作语言)语句，这个操作会放到 rollback segment 中，事务提交之后才生效

DML 语句和 DDL 语句区别
-DML 是数据库操作语言（Data Manipulation Language）的缩写，是指对数据库中表记录的操作，主要包括表记录的插入、更新、删除和查询，是开发人员日常使用最频繁的操作
DDL （Data Definition Language）是数据定义语言的缩写，简单来说，就是对数据库内部的对象进行创建、删除、修改的操作语言。它和 DML 语言的最大区别是 DML 只是对表内部数据的操作，而不涉及到表的定义、结构的修改，
更不会涉及到其他对象。DDL 语句更多的被数据库管理员（DBA）所使用，一般的开发人员很少使用

数据库的设计:
需求分析 : 分析用户的需求，包括数据、功能和性能需求
概念结构设计 : 主要采用 E-R 模型进行设计，包括画 E-R 图
逻辑结构设计 : 通过将 E-R 图转换成表，实现从 E-R 模型到关系模型的转换
物理结构设计 : 主要是为所设计的数据库选择合适的存储结构和存取路径
数据库实施 : 包括编程、测试和试运行
数据库的运行和维护 : 系统的运行与数据库的日常维护

##字符集(coded character set)详解
注: MySQL
SHOW CHARSET 来查看


##SQL语法基础知识总结

#基本概念
-数据库术语
数据库（database） - 保存有组织的数据的容器（通常是一个文件或一组文件）。
数据表（table） - 某种特定类型数据的结构化清单。
模式（schema） - 关于数据库和表的布局及特性的信息。模式定义了数据在表中如何存储，包含存储什么样的数据，数据如何分解，各部分信息如何命名等信息。数据库和表都有模式。
列（column） - 表中的一个字段。所有表都是由一个或多个列组成的。
行（row） - 表中的一个记录。
主键（primary key） - 一列（或一组列），其值能够唯一标识表中每一行。

-SQL语法

子句 - 是语句和查询的组成成分。（在某些情况下，这些都是可选的。）
表达式(expression) - 可以产生任何标量值，或由列和行的数据库表
谓词 - 给需要评估的 SQL 三值逻辑（3VL）（true/false/unknown）或布尔真值指定条件，并限制语句和查询的效果，或改变程序流程。
查询(select) - 基于特定条件检索数据。这是 SQL 的一个重要组成部分。
语句 - 可以持久地影响纲要和数据，也可以控制数据库事务、程序流程、连接、会话或诊断。

SQL 语法要点
SQL 语句不区分大小写，但是数据库表名、列名和值是否区分，依赖于具体的 DBMS 以及配置。
例如：SELECT 与 select、Select 是相同的
多条 SQL 语句必须以分号（;）分隔
处理 SQL 语句时，所有空格都被忽略

//一行
UPDATE user SET username = 'robot', password = 'robot' WHERE username = 'root';
//多行
UPDATE user
SET username='robot', password='robot'
WHERE username = 'root';

SQL 支持三种注释
## 注释1
-- 注释2
/* 注释3 */

#SQL 分类
数据定义语言(DDL)
-数据定义语言（Data Definition Language，DDL）是 SQL 语言集中负责数据结构定义与数据库对象定义的语言。
-DDL 的主要功能是定义数据库对象。
-DDL 的核心指令是 CREATE、ALTER、DROP

数据操纵语言(DML)
-数据操纵语言（Data Manipulation Language, DML）是用于数据库操作，对数据库其中的对象和数据运行访问工作的编程语句。
-DML 的主要功能是 访问数据，因此其语法都是以读写数据库为主。
-DML 的核心指令是 INSERT、UPDATE、DELETE、SELECT。这四个指令合称 CRUD(Create, Read, Update, Delete)，即增删改查

事务控制语言(TCL)
-事务控制语言(Transaction Control Language, TCL) 用于管理数据库中的事务。这些用于管理由 DML 语句所做的更改。它还允许将语句分组为逻辑事务。
-TCL 的核心指令是 COMMIT、ROLLBACK

数据控制语言(DCL)
-DCL 以控制用户的访问权限为主，因此其指令作法并不复杂，可利用 DCL 控制的权限有：CONNECT、SELECT、INSERT、UPDATE、DELETE、EXECUTE、USAGE、REFERENCES。


增删改查(DML) CRUD

INSERT INTO
ex.

插入数据
//insert complete row
INSERT INTO user
VALUES(10, 'root', 'root'),
(12, 'root1', 'root2');

//insert some info
INSERT INTO user(username)
VALUES('root');

INSERT INTO user(username)
SELECT name
FROM account;

更新数据
UPDATE
ex.
UPDATE user
SET username = 'root2', password = 'root'
WHERE username = 'root';

删除数据
DELETE 语句用于删除表中的记录
TRUNCATE TABLE 可以清空表，也就是删除所有行

DELETE FROM user
WHERE username = 'root';

//empty the whole table
TRUNCATE TABLE user;

查询数据
SELECT
DISTINCT 用于返回唯一不同的值。它作用于所有列，也就是说所有列的值都相同才算相同
LIMIT 限制返回行数
ASC 升序(默认)
DESC 降序

//单列查询
SELECT prod_name
FROM products;

//多列查询
SELECT prod_id, prod_name, prod_price
FROM products;

//查询所有列
SELECT * 
FROM products;

//查询不同值
SELECT DISTINCT vend_id
FROM products;

//限制查询结果
前五
SELECT * FROM mytable LIMIT 5;
//从第零条开始返回五个
SELECT * FROM mytable LIMIT 0, 5;
3-5行
//从第二行开始返回3个
SELECT * FROM mytable LIMIT 2, 3;

排序
ORDER BY
SELECT * FROM products
ORDER BY prod_price desc, prod_name ASC;

分组
GROUP BY
group by：

group by 子句将记录分组到汇总行中。
group by 为每个组返回一个记录。
group by 通常还涉及聚合count，max，sum，avg 等。
group by 可以按一列或多列进行分组。
group by 按分组字段进行排序后，order by 可以以汇总字段来进行排序。

//分组
SELECT cust_name, COUNT(cust_address) AS addr_num
FROM Customers GROUP BY cust_name;

//分组后排序
SELECT cust_name, COUNT(cust_address) AS addr_num
FROM CUstomers GROUP BY cust_name
ORDER BY cust_name DESC;

having:
-having 用于对汇总的 group by 结果进行过滤
-having 一般都是和 group by 连用
-where 和 having 可以在相同的查询中

SELECT cust_name, COUNT(*) AS num
FROM Customers
WHERE cust_email IS NOT NULL
GROUP BY cust_name
HAVING COUNT(*) >= 1

having vs where：
where 前, having 后
where：过滤过滤指定的行，后面不能加聚合函数（分组函数）。where 在group by 前。
having：过滤分组，一般都是和 group by 连用，不能单独使用。having 在 group by 之后。

子查询
用于 FROM 的子查询返回的结果相当于一张临时表，所以需要使用 AS 关键字为该临时表起一个名字

SELECT cust_name, cust_contact
FROM customers
WHERE cust_id IN (SELECT cust_id
                    FROM orders
                    WHERE order_num IN (SELECT order_num
                                        FROM orderitems
                                        WHERE prod_id = 'RGAN01'));

WHERE
WHERE 子句用于过滤记录，即缩小访问数据的范围。
WHERE 后跟一个返回 true 或 false 的条件。
WHERE 可以与 SELECT，UPDATE 和 DELETE 一起使用。
可以在 WHERE 子句中使用的操作符。

ex
SELECT * FROM Customers
WHERE cust_name = 'Kids Place';

UPDATE Customers
SET cust_name = 'Jack Jones'
WHERE cust_name = 'Kids Place';

DELETE FROM Customers
WHERE cust_name = 'Kids Place';

IN & BETWEEN
IN 操作符在 WHERE 子句中使用，作用是在指定的几个特定值中任选一个值
BETWEEN 操作符在 WHERE 子句中使用，作用是选取介于某个范围内的值

SELECT *
FROM products
WHERE vend_id IN ('DLL01', 'BRS01');

SELECT *
FROM products
WHERE prod_price BETWEEN 3 AND 5;

AND,OR,NOT
AND、OR、NOT 是用于对过滤条件的逻辑处理指令。
AND 优先级高于 OR，为了明确处理顺序，可以使用 ()。
AND 操作符表示左右条件都要满足。
OR 操作符表示左右条件满足任意一个即可。
NOT 操作符用于否定一个条件。

ex.
SELECT prod_id, prod_name, prod_price
FROM products
WHERE vend_id = 'DLL01' AND prod_price <= 4;

SELECT prod_id, prod_name, prod_price
FROM products
WHERE vend_id = 'DLL01' OR prod_price <= 4;

SELECT *
FROM products
WHERE prod_price NOT BETWEEN 3 AND 5;

LIKE
LIKE 操作符在 WHERE 子句中使用，作用是确定字符串是否匹配模式。
只有字段是文本值时才使用 LIKE。
LIKE 支持两个通配符匹配选项：% 和 _。
不要滥用通配符，通配符位于开头处匹配会非常慢。
% 表示任何字符出现任意次数。
_ 表示任何字符出现一次。

ex.
SELECT prod_id, prod_name, prod_price
FROM products
WHERE prod_name LIKE '%bean bag%'

SELECT prod_id, prod_name, prod_price
FROM products
WHERE prod_name LIKE '__ inch teddy bear';

连接(重点JOIN)
JOIN 是“连接”的意思，顾名思义，SQL JOIN 子句用于将两个或者多个表联合起来进行查询

//基本语法
select table1.column1, table2.column2...
from table1
join table2
on table1.common_column1 = table2.common_column2;

# join....on
select c.cust_name, o.order_num
from Customers c
inner join Orders o
on c.cust_id = o.cust_id
order by c.cust_name;

# 如果两张表的关联字段名相同，也可以使用USING子句：join....using()
select c.cust_name, o.order_num
from Customers c
inner join Orders o
using(cust_id)
order by c.cust_name;

我还是喜欢on
ON 和 WHERE 的区别：

连接表时，SQL 会根据连接条件生成一张新的临时表。ON 就是连接条件，它决定临时表的生成。
WHERE 是在临时表生成以后，再对临时表中的数据进行过滤，生成最终的结果集，这个时候已经没有 JOIN-ON 了。

!!!SQL 先根据 ON 生成一张临时表，然后再根据 WHERE 对临时表进行筛选。


# 隐式内连接
select c.cust_name, o.order_num
from Customers c, Orders o
where c.cust_id = o.cust_id
order by c.cust_name;

# 显式内连接
select c.cust_name, o.order_num
from Customers c inner join Orders o
using(cust_id)
order by c.cust_name;

组合(UNION)
UNION 运算符将两个或更多查询的结果组合起来，并生成一个结果集，其中包含来自 UNION 中参与查询的提取行
UNION 基本规则：

所有查询的列数和列顺序必须相同。
每个查询中涉及表的列的数据类型必须相同或兼容。
通常返回的列名取自第一个查询。

SELECT column_name(s) FROM table1
UNION ALL
SELECT column_name(s) FROM table2;

JOIN vs UNION：

JOIN 中连接表的列可能不同，但在 UNION 中，所有查询的列数和列顺序必须相同。
UNION 将查询之后的行放在一起（垂直放置），但 JOIN 将查询之后的列放在一起（水平放置），即它构成一个笛卡尔积。

函数
不同数据库的函数往往各不相同，因此不可移植。本节主要以 MySQL 的函数为例

LEFT()、RIGHT()	左边或者右边的字符
LOWER()、UPPER()	转换为小写或者大写
LTRIM()、RTRIM()	去除左边或者右边的空格
LENGTH()	长度，以字节为单位
SOUNDEX()	转换为语音值

日期&格式
日期格式：YYYY-MM-DD
时间格式：HH:MM:SS

AddDate()	增加一个日期（天、周等）
AddTime()	增加一个时间（时、分等）
CurDate()	返回当前日期
CurTime()	返回当前时间
Date()	返回日期时间的日期部分
DateDiff()	计算两个日期之差
Date_Add()	高度灵活的日期运算函数
Date_Format()	返回一个格式化的日期或时间串
Day()	返回一个日期的天数部分
DayOfWeek()	对于一个日期，返回对应的星期几
Hour()	返回一个时间的小时部分
Minute()	返回一个时间的分钟部分
Month()	返回一个日期的月份部分
Now()	返回当前日期和时间
Second()	返回一个时间的秒部分
Time()	返回一个日期时间的时间部分
Year()	返回一个日期的年份部分

数值处理
SIN()	正弦
COS()	余弦
TAN()	正切
ABS()	绝对值
SQRT()	平方根
MOD()	余数
EXP()	指数
PI()	圆周率
RAND()	随机数

汇总
AVG()	返回某列的平均值
COUNT()	返回某列的行数
MAX()	返回某列的最大值
MIN()	返回某列的最小值
SUM()	返回某列值之和
注: AVG() 会忽略NULL


DDL 语法
数据库
CREATE DATABASE test;
DROP DATABASE test;
USE test;

数据表（TABLE）
CREATE TABLE user (
id int(10) unsigned NOT NULL COMMENT 'Id',
username varchar(64) NOT NULL DEFAULT 'default' COMMENT '用户名',
password varchar(64) NOT NULL DEFAULT 'default' COMMENT '密码',
email varchar(64) NOT NULL DEFAULT 'default' COMMENT '邮箱'
) COMMENT='用户表';


索引(INDEX)

优点：

使用索引可以大大加快数据的检索速度（大大减少检索的数据量）, 减少 IO 次数，这也是创建索引的最主要的原因。
通过创建唯一性索引，可以保证数据库表中每一行数据的唯一性。

缺点：

创建索引和维护索引需要耗费许多时间。当对表中的数据进行增删改的时候，如果数据有索引，那么索引也需要动态的修改，会降低 SQL 执行效率。
索引需要使用物理文件存储，也会耗费一定空间。

BTree索引最常见 

按照使用维度划分索引
主键索引：加速查询 + 列值唯一（不可以有 NULL）+ 表中只有一个。
普通索引：仅加速查询。
唯一索引：加速查询 + 列值唯一（可以有 NULL）。

主键索引(Primary Key):
一张数据表有只能有一个主键，并且主键不能为 null，不能重复。

二级索引(Secondary Index):
通过二级索引可以定位主键的位置，二级索引又称为辅助索引/非主键索引
唯一索引(Unique Key):
唯一索引也是一种约束。唯一索引的属性列不能出现重复的数据，但是允许数据为 NULL，一张表允许创建多个唯一索引。 
建立唯一索引的目的大部分时候都是为了该属性列的数据的唯一性，而不是为了查询效率
普通索引(Index):普通索引的唯一作用就是为了快速查询数据，一张表允许创建多个普通索引，并允许数据重复和 NULL
前缀索引(Prefix):前缀索引只适用于字符串类型的数据。前缀索引是对文本的前几个字符创建索引，相比普通索引建立的数据更小，因为只取前几个字符
全文索引(Full Text):全文索引主要是为了检索大文本数据中的关键字的信息，是目前搜索引擎数据库使用的一种技术。Mysql5.6 之前只有 MYISAM 引擎支持全文索引，5.6 之后 InnoDB 也支持了全文索引

聚簇索引（Clustered Index）
索引结构和数据一起存放的索引，并不是一种单独的索引类型。InnoDB 中的主键索引就属于聚簇索引
pro
查询速度非常快
对排序查找和范围查找优化
con
依赖于有序的数据
更新代价大

非聚簇索引(Non-Clustered Index)

pro
更新代价比聚簇索引要小 。非聚簇索引的更新代价就没有聚簇索引那么大了，非聚簇索引的叶子节点是不存放数据的

con
跟聚簇索引一样，非聚簇索引也依赖于有序的数据
这应该是非聚簇索引最大的缺点了。 当查到索引对应的指针或主键后，可能还需要根据指针或主键再到数据文件或表中查询

覆盖索引（Covering Index)

覆盖索引即需要查询的字段正好是索引的字段，那么直接根据该索引，就可以查到数据了，而无需回表查询

联合索引(Compound Index)

CREATE TABLE `student` (
  `id` int NOT NULL,
  `name` varchar(100) DEFAULT NULL,
  `class` varchar(100) DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `name_class_idx` (`name`,`class`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;


索引下推（Index Condition Pushdown)


索引使用指南(!!!)

合适:

不为 NULL 的字段：索引字段的数据应该尽量不为 NULL，因为对于数据为 NULL 的字段，数据库较难优化。如果字段频繁被查询，但又避免不了为 NULL，建议使用 0,1,true,false 这样语义较为清晰的短值或短字符作为替代。
被频繁查询的字段：我们创建索引的字段应该是查询操作非常频繁的字段。被作为条件查询的字段：
被作为 WHERE 条件查询的字段，应该被考虑建立索引。频繁需要排序的字段：
索引已经排序，这样查询可以利用索引的排序，加快排序查询时间。
被经常频繁用于连接的字段：经常用于连接的字段可能是一些外键列，对于外键列并不一定要建立外键，只是说该列涉及到表与表的关系。对于频繁被连接查询的字段，可以考虑建立索引，提高多表连接查询的效率

不合适:
被频繁更新的字段


索引并不是越多越好，建议单张表索引不超过 5 个！索引可以提高效率同样可以降低效率。
索引可以增加查询效率，但同样也会降低插入和更新的效率，甚至有些情况下会降低查询效率。

尽可能的考虑建立联合索引而不是单列索引
注意避免冗余索引
字符串类型的字段使用前缀索引代替普通索引
删除长期未使用的索引，不用的索引的存在会造成不必要的性能损耗。

知道如何分析语句是否走索引查询
我们可以使用 EXPLAIN 命令来分析 SQL 的 执行计划 


索引例子:
ex
CREATE INDEX user_index
ON user (id);

ALTER table user ADD INDEX user_index(id);

CREATE UNIQUE INDEX user_index
ON user (id);

ALTER TABLE user
DROP INDEX user_index;


约束(Constraints)

事务处理

不能回退 SELECT 语句，回退 SELECT 语句也没意义；也不能回退 CREATE 和 DROP 语句。
MySQL 默认是隐式提交，每执行一条语句就把这条语句当成一个事务然后进行提交

START TRANSACTION;

INSERT INTO 'user'
VALUES (1, 'root', 'root@xxx.com');

SAVEPOINT updateA;

INSERT INTO 'user'
VALUES (2, 'root2', 'root2@gmail.com');

ROLLBACK TO updateA;
 提交事务，只有操作 A 生效
COMMIT;


权限控制