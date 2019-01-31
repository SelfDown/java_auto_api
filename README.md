# java_auto_api
项目背景

公司做了很多项目之后，发现基本上大部分都是基于表的增删改查。

    1）之前接触东华的接口，发现他们的查询sql是写在界面上的。然后映射出接口。确实很方便。我这里模仿他们在界面上写sql。然后进行查询、筛选、验证等等

    2）对接itask 过程单点登录和esb 接口。只要接上itask的esb。 人员、组织、组织关系、账号、密码。总共9个接口。都通过一个接口推送过来，通过接口里一个唯一标志符号，来区分业务操作。我模仿它，将新增、修改、删除、查询接口，统一成一个接口，也就操作通过 接口里service 标志符号来区分。

项目特点

    1）这里统一所有的业务接口。意思是所有的增删改查只有一个接口（除文件上传、下载）。及/insight/service/result.接口里有标志符号（service），确定来做哪些业务

    2）在线自动接口文档。应用接口统一，而且都是配置出来的，所以接口文档能自动生成

    3）自带测试工具。

    4） 配置文件支持在线改。包括数据库的配置可以在tomcat 启动之后再改。基本上是0 配置。所有的配置信息保存在database.db 里。
     只要配置一个api.database.path 是 database.db 的路径和debugger 是否为调试模式

    5）大部分的增删改查都是页面上直接配置，不需要任何开发。以后界面基本也能配置出来像金蝶一样，保存为数据库记录动态加载


项目集成。maven 方式建立项目。我用的是idea

     1）File>New>Project from Existing sources...
     
     2)选中解压后的sqlapi>Import project from external model>Maven
     
     3) 默认3步。然后选中jdk 1.8。最后到默认直到finish
     
     4）找到application.properties 。配置api.database.path 为database.db 实际路径
     
     5）maven 下载所需包后，点击Appliction.java 右键 Run 'Appliction.main()' 运行成功
     
     6) 浏览器访问http://localhost:8080/insight-api.html 控制台 
     


将sql 转化为http api 工具

java maven 项目。基于spring boot .在界面上填写sql 查询语句，直接转化为 http api。能够处理简单增删改查
