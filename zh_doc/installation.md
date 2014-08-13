FHIRBASE
很多年前 RIM 出现的时候 试图以one fit all的架势席卷全球 实现宇宙healthcare大一统的梦想 
那时候ORACLE以JAVASIG中RIM 存储模型为原型开发了ORACLE HTB产品 买的很差吧.
在那之后,有一个叫[MGRID](http://www.mgrid.net/)公司 以RIM模型为基础 结合在PG数据库基础上开发了一个产品
当时有一篇论文就是在讲[ISO Healthcare Datatype/HL7 DATA TYPE R2里的数据类型在PG中的实现](http://www.mgrid.net/sites/default/files/1003.3370v1.pdf).
现在产品线好像很强大[产品说明](http://www.mgrid.net/sites/default/files/mgrid-productbrief-201303.pdf)
*  Healthcare DatatypeLibrary (HDL)医疗数据类型库 
*  Healthcare Data Model(HDM)医疗数据模型
*  数据导入导出(队列选择和分析)
多年过去了 FHIR火了后 又有人沿着前人的脚步开始了类似的探索          
你可以选择vagrant+virtualbox的方式 可以选择docker image的方式 亦可在本机安装        
##本机安装          

fhirbase数据库本机安装
1.安装所必须的软件为
Requirements:

    PostgreSQL 9.4 (http://www.postgresql.org/about/news/1522/)
    pgcrypto
    pg_trgm

可以通过如下命令完成上述三个的安装
You can build Postgresql from source on debian/ubuntu and create local user cluster with:

source local_cfg.sh && ./install-postgres

NOTE: you can tune configuration in local_cfg.sh.

2.软件安装完成之后,只需要将数据库脚本写到pg里面即可 如下
You can install FHIRBase:

source local_cfg.sh
echo 'CREATE DATABASE mydb' | psql postgres
psql mydb < fhirbase--1.0.sql

数据库的使用          
找到fhirbase源码路径
1.首先运行 source local_cfg.sh
2.pg_ctl start 启动数据库
里面是对pg端口 地址的配置参数
3.链接数据库
psql mydb
或者 
psql -U fhirbase -d mydb -h localhost -p 5777
4.或者使用pgadmin客户端登录


