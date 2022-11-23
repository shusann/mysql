# mysql常用命令
* mysql启动和关闭
   + net start mysql80
   + net stop mtsql80
* mysql客户端连接
   + mysql [-h 127.0.0.1] [-p 3306] -u root -p

## SQL
### DDL-数据库操作
> * 查询所有数据库
>   + show databases;
> * 查询当前数据库
>   + select database();
> * 创建数据库
>   + create database [if not exists] 数据库名 [default charset 字符集] [collate 排序规则];
> * 删除数据库
>   + drop database [if exists] 数据库名;
> * 使用
>   + use 数据库名;
---
### DDL-表操作
#### DDL-表操作-查询
> * 查询当前数据库所有表
>   + show tables;
> * 查询表结构
>   + desc 表名;
> * 查询指定表的建表语句
>   + show create table 表名;

#### DDL-表操作-创建
> create table 表名(
>     字段1 字段1类型[comment 字段1注释],
>     字段2 字段2类型[comment 字段2注释],
>     字段3 字段3类型[comment 字段3注释],
>     ......
>     字段n 字段n类型[comment 字段n注释]
> )[comment 表注释];

#### DDL-表操作-数据类型
##### 数值类型
| 类型 | 大小 | 有符号(SIGNED)范围 | 无符号(UNSIGNED)范围 | 描述 |
|----|----|----|----|----|
|TINYINT|1 byte|(-128, 127)|(0, 255)|小整数值|
|SMALLINT|2 bytes|(-32768, 32767)|(0，65535)|大整数值|
|MEDIUMINT|3 bytes|(-8388608, 8388607)|(0，16777215)|大整数值|
|INT或INTEGER|4 bytes|(-2147483648，2147483647)|(0，4 294 967 295)|大整数值|
|BIGINT|8 bytes|(-9223372036854775808，9223372036854775807)|(0，18 446 744 073 709 551 615)|极大整数值|
|FLOAT|4 bytes|(-3.402 823 466 E+38，-1.175 494 351 E-38)，0，(1.175 494 351 E-38，3.402 823 466 351 E+38)|0，(1.175 494 351 E-38，3.402 823 466 E+38)|单精度浮点数值|
|DOUBLE|8 bytes|(-1.797 693 134 862 315 7 E+308，-2.225 073 858 507 201 4 E-308)，0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308)|0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308)|双精度浮点数值|
|DECIMAL|对DECIMAL(M,D) ，如果M>D，为M+2否则为D+2|依赖于M和D的值|依赖于M和D的值|小数值|

##### 字符串类型
| 类型 | 大小 | 描述 |
|----|----|----|
|CHAR	    |0-255 bytes	|定长字符串|
|VARCHAR	|0-65535 bytes	|变长字符串|
|TINYBLOB	|0-255 bytes	|不超过 255 个字符的二进制字符串|
|TINYTEXT	|0-255 bytes	|短文本字符串|
|BLOB	    |0-65 535 bytes	|二进制形式的长文本数据|
|TEXT	    |0-65 535 bytes	|长文本数据|
|MEDIUMBLOB	|0-16 777 215 bytes	|二进制形式的中等长度文本数据|
|MEDIUMTEXT	|0-16 777 215 bytes	|中等长度文本数据|
|LONGBLOB	|0-4 294 967 295 bytes	|二进制形式的极大文本数据|
|LONGTEXT	|0-4 294 967 295 bytes	|极大文本数据|

##### 日期和时间类型
|类型|大小( bytes)|范围|格式|用途|
|----|----|----|----|----|
|DATE	    |3	|1000-01-01/9999-12-31|	YYYY-MM-DD|	日期值|
|TIME	    |3	|'-838:59:59'/'838:59:59'|	HH:MM:SS|	时间值或持续时间|
|YEAR	    |1	|1901/2155|	YYYY|	年份值|
|DATETIME	|8	|'1000-01-01 00:00:00' 到 '9999-12-31 23:59:59'|	YYYY-MM-DD hh:mm:ss|	混合日期和时间值|
|TIMESTAMP	|4	|'1970-01-01 00:00:01' UTC 到 '2038-01-19 03:14:07' UTC| YYYY-MM-DD hh:mm:ss|	混合日期和时间值，时间戳|

#### DDL-表操作-修改
> * 添加
>   + alter table 表名 add 字段名 类型(长度) [comment 注释] [约束];
> * 修改数据类型
>   + alter table 表名 modify 字段名 新数据类型(长度);
> * 修改字段名和字段类型
>   + alter table 表名 change 旧字段名 新字段名 类型(长度) [comment 注释] [约束];
> * 删除字段
>   + alter table 表名 drop 字段名;
> * 修改表名
>   + alter table 表名 remame to 新表名;
