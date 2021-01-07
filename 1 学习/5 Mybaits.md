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

# 1 关于Mybaits

![image-20201231120733701](https://i.loli.net/2020/12/31/XST1MkIa2ChlZ37.png)