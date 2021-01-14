# 0 建表

- 建表工具：PowerDesigner

![image-20210111114455637](https://i.loli.net/2021/01/11/w6CfLFNIrDKtQTH.png)

- 建表，用powerdesigner画图，就可以自动生成schema，然后调整语句

![image-20210111231616249](https://i.loli.net/2021/01/11/T8KZr4Y32EfDotz.png)

- 修改文件的字符编码，比如下图，把sql文件从ANSI改成utf-8

![image-20210111231854244](https://i.loli.net/2021/01/11/2BLYFbon9UNzhSe.png)

# 1 使用mysql

- 首先登陆

![image-20210111232016579](https://i.loli.net/2021/01/11/CJYXO5maMHUtI28.png)

- 查看数据库
- ![image-20210111232040509](https://i.loli.net/2021/01/11/cN2xrw5QuzD3Fyq.png)

- 删掉旧的t_user表，然后用source插入新表

![image-20210111232134355](https://i.loli.net/2021/01/11/AObLVvo4UWFYHBy.png)

![image-20210111232220668](https://i.loli.net/2021/01/11/YBRvifzGVMkgD1s.png)

# 2 开发

## 2.1 初始化用户界面

![image-20210111233232259](https://i.loli.net/2021/01/11/Ysb9NmipXLQJ28E.png)

## 2.2 连接数据库检查用户信息是否正确

![image-20210111233545498](https://i.loli.net/2021/01/11/VDuHA7y63mIiWxG.png)

![image-20210111234248737](https://i.loli.net/2021/01/11/dD1QN4HjUnpP6Vc.png)

## 2.3 终结形态

![image-20210111234634915](https://i.loli.net/2021/01/11/FCkBQcftmGbVsYT.png)

![image-20210111234624933](https://i.loli.net/2021/01/11/evOLfjQ3IgzZsob.png)

![image-20210111234556337](https://i.loli.net/2021/01/11/EBS7YzVmPfWlG4n.png)

# 3 安全

## 3.1 SQL注入

![image-20210111235359446](https://i.loli.net/2021/01/11/1ouHMaIqBiNKFmt.png)

- 原因在于SQL语句的漏洞

![image-20210111235951192](https://i.loli.net/2021/01/11/H4uS7NBRD8dhrnm.png)

## 3.2 解决SQL注入问题的方法 - PreparedStatement（开发中真正使用的是这个）

![image-20210113100813192](https://i.loli.net/2021/01/13/EWoMcHr1l7bTdIm.png)

- 修改内容为以下
- 把所有stmt改成ps

![image-20210113100907620](https://i.loli.net/2021/01/13/328u6RbZHf9rUMi.png)

![image-20210113100928532](https://i.loli.net/2021/01/13/zwUs2H4NQcAjLRI.png)

![image-20210113102028442](https://i.loli.net/2021/01/13/Yj1LebTWmdxKUCJ.png)

## 3.3 升序降序 - 必须使用Statement而不是PreparedStatement

- 看来statement和preparedStatement是各有各的用途

![image-20210113182012827](https://i.loli.net/2021/01/13/XHgcfBeS9YphJZV.png)

![image-20210113233718861](https://i.loli.net/2021/01/13/fFKHZBnxjiMYUrI.png)

![image-20210113233704155](https://i.loli.net/2021/01/13/yOZw4GAQMtjqgKm.png)

# 4 事务锁

