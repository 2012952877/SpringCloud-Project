

# 0 准备

- Mybaits是用于替代JDBC中大量的冗余代码所出现的框架
- JDBC是用于Java连接SQL的工具（Java Database Connectivity）
- ![image-20201231124028911](https://i.loli.net/2020/12/31/b8GWpQmhzvPcekK.png)
  - 不要Dog d，因为这样的方法不能feed Cat了，基于面向抽象编程的思想，应该写成Animal a
  - 这也是“面向父类编程”=“面向抽象编程”=“面向接口编程”
  - 在java.sql.*; 下面，是一个interface
- ![image-20201231125413366](https://i.loli.net/2020/12/31/kwvhE3VSIlLWGnm.png)
  - 有JDBC就不需要再写多套连接的Java程序
- ![image-20210101144530488](https://i.loli.net/2021/01/01/CMJP5AFQH9N3gwz.png)

## 0.1 JDBC的步骤

![image-20210109133408747](https://i.loli.net/2021/01/09/dDFO73BnRV1c2Gk.png)

### 0.1.1 注册驱动

- 这一步我们告诉java要连接的是com.mysql.jdbc.Driver();数据库

![image-20210109140039565](https://i.loli.net/2021/01/09/mQzlWMFyiIxZUo5.png)

- 8.0版本以后是    **new com.mysql.cj.jdbc.Driver();**

#### 0.1.1.1 注册驱动的不同方式

![image-20210109190310002](https://i.loli.net/2021/01/09/6isurjNZJXLBQIp.png)

- 这样写的目的是利用配置文件

### 0.1.2 获取连接

![image-20210109140728841](https://i.loli.net/2021/01/09/4QDpYF6GjPTeZSd.png)

![image-20210109141452469](https://i.loli.net/2021/01/09/mqeRvDdVIa2F57f.png)

- user是计算机的账号
- password是计算机的密码

![image-20210109141856787](https://i.loli.net/2021/01/09/miUWYpErvjed1KV.png)

![image-20210109143835626](https://i.loli.net/2021/01/09/jousTvBO8wRCA4G.png)

### 0.1.3 获取数据库操作对象（Statement 专门执行sql语句的）

![image-20210109154946705](https://i.loli.net/2021/01/09/citZT3vWVHS96Ij.png)

![image-20210109155041449](https://i.loli.net/2021/01/09/btV4usQRUGnwaHf.png)

### 0.1.4 执行sql

![image-20210109155441083](https://i.loli.net/2021/01/09/RONHqUd6YujAtIL.png)

### 0.1.5 处理查询结果集 ，executeQuery方法(select，DQL,和executeUpadate不同)

- 用executeQuery拿到ResultSet以后，需要拿到结果集中的所有数据，编程思路是这样的
- ![image-20210110120703354](D:%5CPicgo%5CEQvWKs1mlBytFu2.png)

![image-20210110121346006](https://i.loli.net/2021/01/10/ys3u2jRDUdnzgIA.png)

![image-20210110121446019](https://i.loli.net/2021/01/10/xLXVA19jyk75Tb6.png)

#### 0.1.5.1 使用while来实现对ResultSet的遍历，注意这里有两种写法

![image-20210110124335311](https://i.loli.net/2021/01/10/ywRGZ3CWNiOhkg4.png)

![image-20210110131118652](https://i.loli.net/2021/01/10/ZfscEpVT13zJyNS.png)

### 0.1.6 释放资源

![image-20210109182036940](https://i.loli.net/2021/01/09/k2psq6iZnRtXLCO.png)

![image-20210109182136096](https://i.loli.net/2021/01/09/z9nsMhCTEfJVxRe.png)

#### 0.1.6.1 释放资源的顺序是固定的

![image-20210110115506070](https://i.loli.net/2021/01/10/dJAUk3csj1NpOT9.png)

- rs是ResultSet，是executeQuery返回的结果集；如果用的是executeUpdate，则返回的是int，代表这个操作影响的数据库记录数量
- stmt是createStatement，数据库的操作对象
- conn是getConnection，获取到的连接
- 以上三条都要按照从小到大依次关闭

### 0.1.7 连接jdbc和属性资源文件

- 首先创建jdbc.properties

![image-20210109190808226](https://i.loli.net/2021/01/09/rpEau3C4PW1dYbN.png)

![image-20210109190847099](https://i.loli.net/2021/01/09/zdOTReu4rfsi1I9.png)

- 修改代码

![image-20210109191037063](https://i.loli.net/2021/01/09/JfHvdth48jG9TiY.png)

## 0.2 DQL、DML、DDL、DCL的概念与区别

- **DML（Data Manipulation Language）**

  - 数据操纵语言DML主要有三种形式：
    1) 插入：INSERT
    2) 更新：UPDATE
    3) 删除：DELETE

- **DDL(数据定义语言，Data Definition Language)**

  - 数据定义语言DDL用来创建数据库中的各种对象-----表、视图、
    索引、同义词、聚簇等如：
    CREATE TABLE/VIEW/INDEX/SYN/CLUSTER
    | | | | |
    表 视图 索引 同义词 簇

    DDL操作是隐性提交的！不能rollback

- **数据查询语言DQL**

  - 数据查询语言DQL基本结构是由SELECT子句，FROM子句，WHERE
    子句组成的查询块：
    SELECT <字段名表>
    FROM <表或视图名>
    WHERE <查询条件>

- **数据控制语言DCL**

  - 数据控制语言DCL用来授予或回收访问数据库的某种特权，并控制
    数据库操纵事务发生的时间及效果，对数据库实行监视等。如：
    1) GRANT：授权。
    2) ROLLBACK [WORK] TO [SAVEPOINT]：回退到某一点。
    回滚---ROLLBACK
    回滚命令使数据库状态回到上次最后提交的状态。其格式为：
    SQL>ROLLBACK;

    3) COMMIT [WORK]：提交。  在数据库的插入、删除和修改操作时，只有当事务在提交到数据
    库时才算完成。在事务提交前，只有操作数据库的这个人才能有权看
    到所做的事情，别人只有在最后提交完成后才可以看到。
    提交数据有三种类型：显式提交、隐式提交及自动提交。下面分
    别说明这三种类型。
    (1) 显式提交
    用COMMIT命令直接完成的提交为显式提交。其格式为：
    SQL>COMMIT；
    (2) 隐式提交
    用SQL命令间接完成的提交为隐式提交。这些命令是：
    ALTER，AUDIT，COMMENT，CONNECT，CREATE，DISCONNECT，DROP，
    EXIT，GRANT，NOAUDIT，QUIT，REVOKE，RENAME。

    (3) 自动提交
    若把AUTOCOMMIT设置为ON，则在插入、修改、删除语句执行后，
    系统将自动进行提交，这就是自动提交。其格式为：
    SQL>SET AUTOCOMMIT ON；

## 0.3 在IDEA中配置jdbc

![image-20210110183503748](https://i.loli.net/2021/01/10/tfijreIDaokw1JU.png)

![image-20210110183528249](https://i.loli.net/2021/01/10/TXu7Zz1ESLhQYfy.png)

![image-20210110183539834](https://i.loli.net/2021/01/10/AtsD3qznvfVmLhR.png)

![image-20210110183601282](https://i.loli.net/2021/01/10/niZoq3edYwL8tSj.png)

![image-20210110183609996](https://i.loli.net/2021/01/10/NinT97LZCKshpQF.png)

![image-20210110183647601](https://i.loli.net/2021/01/10/B3vCyWJl6KczMmF.png)

# 1 关于Mybaits

![image-20201231120733701](https://i.loli.net/2020/12/31/XST1MkIa2ChlZ37.png)