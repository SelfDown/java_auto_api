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


项目搭建。maven 方式建立项目。我用的是idea

     1）File>New>Project from Existing sources...
     
     2)选中解压后的sqlapi>Import project from external model>Maven
     
     3) 默认3步。然后选中jdk 1.8。最后到默认直到finish
     
     4）找到application.properties 。配置api.database.path 为database.db 实际路径
     
     5）maven 下载所需包后，点击Appliction.java 右键 Run 'Appliction.main()' 运行成功
     
     6) 浏览器访问 http://localhost:8080/insight-api.html 控制台 
     


恭喜项目已经搭建完成！接下来就是配置，不会有开发（除非自定义模块）。首先大致介绍一下这里已经实现的模块。以后的工作都是基于这些模块来配置

     1）platform_query  查询模块。界面上填写一个基本查询sql，基于它来进行筛选查询。建议先把sql 在navicat写好.直接复制粘贴到这里
     
     2）platform_create 创建数据模块。基于表，用户可以上传一些数据字段，也可以后台根据现有的规则生成字段。最后达到数据库记录生成
     
     3)platform_update 修改数据模块。同创建一样。可以上传，也可以后台生成。达到数据库记录修改。如果是假删除，也是修改模块，只是将delete_flag改为1 
     
     4)platform_login 登录模块
     
     5）version_iteration 模型版本迭代。这是个自定义业务模块，对于新项目基本用不上。以后集成工作流后能直接替代它
     
     6）database_table 数据库创建更新模块。可以在线建表，添加字段、修改字段长度等等。注意如果是树形结构，添加默认记录id=0,delete_flag=0的记录
     
     7）file_upload_save 文件上传模块。可以配置文件保存路径，生成文件夹规则，比如一个文件夹不能超过1000个文件。注意如果自定义模块。这里预留service_file 开头是文件操作。其他的service 不能使用
     
     8）database_connection_config 数据库连接配置。配置数据库host、用户名、密码、数据库、初始连接数量等等。这里使用druid 连接池，填写druid属性可以生效。注意这里service_read_source 和service_write_source 不能删除。项目启动的时候会默认连接它们
     
然后对界面大致介绍一下
     
     1）顶部的大文本框是控制台，显示接口调用信息，传递的参数信息
     
     2）admin和e10adc3949ba59abbe56e057f20f883e 文本框是之前项目登录接口。基本不用
     
     3）insight/service/result 后面的文件框是接口测试框。请求json 数据放在这个里面。请求地址是insight/service/result，点击提交按钮，以ajax json方式提交
     
     4）下面的表格，是具体接口信息包括service 和备注信息，以后接口调用就是调用具体的service
     
     5）点击新增或者修改，右侧显示模块配置参数信息
     
     6）查看json 按钮，可以查看请求的必传参数
     
     7）查看文档，以页面的显示描述接口的信息，包含了一个js 调用示例。可以将此页面右键打印pdf,存档、或者给第三方接口人员使用
     
     8）测试按钮 是发了一个 insight/service/result 请求。和填写json再点击提交效果一致。如果想更改参数提交。查看json ，修改字段后。复制到接口测试框中，点击提交

 
项目配置文档，请查看 https://github.com/SelfDown/java_auto_api/wiki
