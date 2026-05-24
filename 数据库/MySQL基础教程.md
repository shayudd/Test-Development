# MySQL数据库安装、连接

## Windows

✅安装

https://dev.mysql.com/downloads/mysql/

可在MySQL文件夹先创建两个文件夹 install 和 data

打开MySQL Configurator，其中：

   Data Directory可选刚创建的文件夹data

   记住端口是3306

   填MySQL Root Passward: 例如fwk123

   …其余默认

此时MySQL服务已启动



✅卸载

任务管理器——服务——MYSQL84  停止

控制面板——程序——程序和功能，右击卸载，按提示操作即可





## Linux

✅安装

```shell
sudo apt update
```

https://dev.mysql.com/downloads/repo/apt/

```shell
wget https://dev.mysql.com/get/mysql-apt-config_0.8.39-1_all.deb
sudo dpkg -i mysql-apt-config_0.8.39-1_all.deb
```

按提示选择 mysql-8.4-lts

```shell
sudo apt update
sudo apt install mysql-server -y
```

设置root密码：fwk123

启动服务

```shell
sudo systemctl start mysql
```

开机自启

```shell
sudo systemctl enable mysql
```

查看运行状态

```shell
sudo systemctl status mysql
```

看到active (running)表示正在运行

停止服务

```shell
sudo systemctl stop mysql
```





## 连接数据库

用户名是你登录的用户，主机名或者IP地址为可选项，如果是本地连接则不需要，远程连接需要填写，密码是对应用户的密码

```shell
mysql –u 用户名 [–h 主机名或者IP地址, -P 端口号] –p 密码
```

- 输入-p后可以直接跟上密码，也可以按回车，会提示你输入密码，二者都是相同的效果
- `-h 127.0.0.1` 其中“-h”是参数，“127.0.0.1” 是 IP 地址，默认本地参数可忽略
- `-P 3306` 其中“-P”是参数，“3306” 是端口号，默认本地参数可忽略

```shell
mysql -u root -p
```

```shell
mysql -h 127.0.0.1 -P 3306 -u root -p rootpassword

...
mysql>
```

只需要在`mysql>`命令中输入 SQL 语句，同时并以分号“;”结束。最后摁`Enter`键即可：

- 命令输入在`mysql>` 之后
- 用`q\`、`quit`、`exit`三种命令可以退出命令行实用程序
- 帮助命令，输入`help`或`\h`获得帮助，可以获得其它特定的命令的帮助(如，输入help select获得使用SELECT语句的帮助)



⭐使用管理工具远程连接

先创建远程用户

远程用户：fwkRemote，密码：remote

```sql
CREATE USER 'fwkRemote'@'%' IDENTIFIED BY 'remote';
```

这里是授权全部数据库的所有权限，也可以是某一个数据库或某一个数据库的某一个表，也可以是部分权限，等等

```sql
GRANT ALL PRIVILEGES ON *.* TO 'fwkRemote'@'%' WITH GRANT OPTION;
```

刷新权限，立即生效

```sql
FLUSH PRIVILEGES;
```

重启数据库

```shell
sudo systemctl restart mysql
```

开放 Ubuntu 防火墙端口，开放 3306

```shell
sudo ufw allow 3306/tcp
```



**DataGrip**

新建工程

![image-20260524183542503](./MySQL基础教程.assets/image-20260524183542503.png)

![image-20260524183558300](./MySQL基础教程.assets/image-20260524183558300.png)

选择schema或新建schema即可

右击新建console即可输入SQL命令了





**Navicat**

点击连接

略

点击【新建查询】编写SQL语句







# 数据库管理

## 创建数据库 

创建test数据库

```sql
CREATE DATABASE test;
```

若此数据库存在则报错，可加上IF NOT EXISTS

```sql
CREATE DATABASE IF NOT EXISTS test;
```





## 查看数据库

数据库连接成功之后，可查看当前所有存在的数据库：

```sql
SHOW DATABASES;
```



## 删除数据库

```sql
DROP DATABASE test;
```

类似的，加上IF EXISTS

```sql
DROP DATABASE IF EXISTS test;
```



## 选择数据库

选择使用test数据库，之后一系列操作即针对此数据库

```sql
USE test;
```







## 数据库存储引擎

MySQL 提供了多个存储引擎，包括处理事务安全表的引擎和处理非事务安全表的引擎。在 MySQL 中，不需要在整个服务器中使用同一种存储引擎，针对具体的要求，可以对每一个表使用不同的存储引擎。

MySQL中的数据用各种不同的技术存储在文件(或者内存)中。这些技术中的每一种技术都使用不同的存储机制、索引技巧、锁定水平并且最终提供广泛的不同的功能和能力。通过选择不同的技术，你能够获得额外的速度或者功能，从而改善你的应用的整体功能。 存储引擎就是如何存储数据、如何为存储的数据建立索引和如何更新、查询数据等技术的实现方法。

例如，如果你在研究大量的临时数据，你也许需要使用内存存储引擎。内存存储引擎能够在内存中存储所有的表格数据。又或者，你也许需要一个支持事务处理的数据库(以确保事务处理不成功时数据的回退能力)。

### InnoDB

默认





# MySQL数据类型与运算符

MySQL 常用的数据类型大致可分为：

- 数值类型：例如 `TINYINT`、`INT`、`BIGINT`、`FLOAT`、`DOUBLE`、`DECIMAL`
- 日期时间类型：例如 `YEAR`、`DATE`、`TIME`、`DATETIME`、`TIMESTAMP`
- 字符串类型：例如 `CHAR`、`VARCHAR`、`TEXT`、`ENUM`、`SET`
- 二进制类型：例如 `BIT`、`BINARY`、`VARBINARY`、`BLOB`

不同类型决定了数据的存储方式、取值范围、比较规则以及空间占用



✨选择字段类型时，通常遵循以下原则：

1. 满足业务需求即可，不要盲目选择更大的类型。
2. 能用数值类型就不要用字符串类型。
3. 定长数据优先考虑 `CHAR`，变长数据优先考虑 `VARCHAR`。
4. 金额、精确计算等场景优先使用 `DECIMAL`，避免浮点误差。
5. 日期时间信息应使用专门的时间类型，不要自行用字符串保存。
6. 文本内容较长时使用 `TEXT`，二进制大对象使用 `BLOB`。

字段类型选得合适，不仅有助于节省存储空间，也会直接影响查询效率、索引效果和后续维护成本。



## 整数类型

### TINYINT

`TINYINT` 占用 1 个字节，适合保存范围较小的整数。

常见场景：

- 性别
- 布尔状态
- 很小范围的枚举值

示例：

```sql
CREATE TABLE user_status (
  id int NOT NULL AUTO_INCREMENT,
  status tinyint NOT NULL DEFAULT 0 COMMENT '0禁用，1启用',
  PRIMARY KEY (id)
);
```

✅如果字段永远不会出现负数，可以配合 `UNSIGNED` 使用，获得更大的正数范围。



### SMALLINT

`SMALLINT` 占用 2 个字节，适合保存范围中等偏小的整数。

常见场景：

- 年份编号
- 库存数量较小的商品
- 区域编号、分类编号

示例：

```sql
CREATE TABLE course (
  id int NOT NULL AUTO_INCREMENT,
  course_no smallint unsigned NOT NULL,
  PRIMARY KEY (id)
);
```



### MEDIUMINT

`MEDIUMINT` 占用 3 个字节，介于 `SMALLINT` 和 `INT` 之间。

它在很多业务里不如 `INT` 常见，但在一些对存储空间敏感、同时数据量又超过 `SMALLINT` 范围的场景里仍然有价值。

示例：

```sql
CREATE TABLE city_stat (
  id int NOT NULL AUTO_INCREMENT,
  population mediumint unsigned NOT NULL DEFAULT 0,
  PRIMARY KEY (id)
);
```



### INT

`INT` 是**最常用**的整数类型，占用 4 个字节，适合绝大多数业务编号和计数字段。

常见场景：

- 用户 ID
- 订单 ID
- 浏览次数
- 商品数量

示例：

```sql
CREATE TABLE article (
  id int unsigned NOT NULL AUTO_INCREMENT,
  title varchar(100) NOT NULL,
  view_count int unsigned NOT NULL DEFAULT 0,
  PRIMARY KEY (id)
);
```

如果不确定用哪种整数类型，`INT` 通常是最稳妥的默认选择。



### BIGINT

`BIGINT` 占用 8 个字节，适合非常大的整数范围。

常见场景：

- 超大规模主键 ID
- 雪花算法 ID
- 金额分单位后的超大整数存储
- 高并发日志流水号

示例：

```sql
CREATE TABLE order_log (
  id bigint unsigned NOT NULL AUTO_INCREMENT,
  order_no bigint unsigned NOT NULL,
  PRIMARY KEY (id)
);
```

当数据量可能达到数十亿级时，主键通常会优先考虑 `BIGINT`。



### 小结

整数类型的核心差别在于“范围”和“空间”。范围够用即可，过大只会浪费存储；过小则可能溢出。业务里最常见的是 `TINYINT`、`INT` 和 `BIGINT`。





## 浮点数类型和定点数类型

### FLOAT

`FLOAT` 是单精度浮点数，适合对精度要求不高、但更关注存储空间和速度的场景。

常见场景：

- 温度
- 身高体重
- 近似统计值

示例：

```sql
CREATE TABLE weather (
  id int NOT NULL AUTO_INCREMENT,
  temperature float DEFAULT NULL,
  PRIMARY KEY (id)
);
```

需要注意，`FLOAT` 在计算和存储时可能出现精度误差，因此不适合保存金额等精确数据。



### DOUBLE

`DOUBLE` 是双精度浮点数，精度和范围都比 `FLOAT` 更高。

常见场景：

- 科学计算
- 更大范围的近似数值
- 对误差容忍度稍低但仍不要求绝对精确的业务

示例：

```sql
CREATE TABLE position_log (
  id int NOT NULL AUTO_INCREMENT,
  longitude double NOT NULL,
  latitude double NOT NULL,
  PRIMARY KEY (id)
);
```

`DOUBLE` 比 `FLOAT` 更精确，但本质上仍然是浮点数，也可能存在精度问题。



### DECIMAL

`DECIMAL` 是定点数类型，适合要求精确计算的场景。

最典型的场景就是：

- 金额
- 账务数据
- 税率
- 结算数据

语法通常写为：

```sql
DECIMAL(M, D)
```

其中：

- `M` 表示总位数
- `D` 表示小数位数

例如：

```sql
CREATE TABLE account (
  id int NOT NULL AUTO_INCREMENT,
  balance decimal(10,2) NOT NULL DEFAULT 0.00,
  PRIMARY KEY (id)
);
```

这里的 `decimal(10,2)` 表示总共 10 位，其中 2 位是小数位，也就是最多能表示 8 位整数加 2 位小数。



### 小结

`FLOAT` 和 `DOUBLE` 是近似值，`DECIMAL` 是精确值。只要涉及金额、结算、财务、积分等不能容忍误差的业务，应该优先使用 `DECIMAL`。







## 日期时间类型

### YEAR

`YEAR` 用于保存年份信息，格式通常为

示例：

```sql
CREATE TABLE student_profile (
  id int NOT NULL AUTO_INCREMENT,
  enroll_year year DEFAULT NULL,
  PRIMARY KEY (id)
);
```

如果字段只需要表达“年份”，使用 `YEAR` 会比字符串更清晰。



### DATE

`DATE` 用于保存日期，不包含时分秒，格式通常为 `YYYY-MM-DD`。

示例：

```sql
CREATE TABLE holiday (
  id int NOT NULL AUTO_INCREMENT,
  holiday_date date NOT NULL,
  PRIMARY KEY (id)
);
```



### TIME

`TIME` 用于保存时间值，可以表示一天中的某个时间点，也可以表示一个时间间隔，格式为

示例：

```sql
CREATE TABLE work_time (
  id int NOT NULL AUTO_INCREMENT,
  start_time time NOT NULL,
  PRIMARY KEY (id)
);
```



### DATETIME类型

`DATETIME` 用于保存完整日期和时间，格式通常为 `YYYY-MM-DD HH:MM:SS`。

示例：

```sql
CREATE TABLE article (
  id int NOT NULL AUTO_INCREMENT,
  publish_time datetime NOT NULL,
  PRIMARY KEY (id)
);
```



### TIMESTAMP类型

`TIMESTAMP` 同样可以保存日期和时间，但更常用于记录系统时间，例如创建时间、更新时间。

示例：

```sql
CREATE TABLE user_log (
  id int NOT NULL AUTO_INCREMENT,
  created_at timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  updated_at timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP
    ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (id)
);
```

这个例子里：

- `created_at` 在插入时自动写入当前时间
- `updated_at` 在更新记录时自动刷新

因此 `TIMESTAMP` 很适合审计字段。



### DATETIME和TIMESTAMP的区别

可以这样理解：

- `DATETIME` 更适合业务层面的“真实时间点”
- `TIMESTAMP` 更适合系统自动维护的时间字段

常见实践：

- 订单创建时间、日志时间：常用 `TIMESTAMP`
- 活动开始时间、预约时间：常用 `DATETIME`



### 小结

如果只需要年份，用 `YEAR`；只需要日期，用 `DATE`；只需要时间，用 `TIME`；需要完整日期时间，则常在 `DATETIME` 和 `TIMESTAMP` 之间选择。选型的关键不只是格式，还要考虑字段的业务语义。













# 数据表的基本操作









# ⭐查询数据







# ⭐插入、更新与删除数据









# ⭐索引





# MySQL函数







# 存储过程和函数









# 视图









# 触发器









# MySQL用户管理











# 数据备份与还原









# MySQL日志









