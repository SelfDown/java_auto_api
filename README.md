# java_auto_api
公司做了很多项目之后，发现基本上大部分都是基于表的增删改查。

之前接触东华的接口，发现他们的查询sql是写在界面上的。然后映射出接口。确实很方便。我这里模仿他们在界面上写sql。然后进行查询、筛选、验证等等

对接itask 过程单点登录和esb 接口。只要接上itask的esb。 人员、组织、组织关系、账号、密码。总共9个接口。都通过一个接口推送过来。

然后我这里统一所有的业务接口。意思是所有的增删改查只有一个接口。及/insight/service/result.接口里有标志符号，确定来做哪些业务


将sql 转化为http api 工具

java maven 项目。基于spring boot .在界面上填写sql 查询语句，直接转化为 http api。能够处理简单增删改查
