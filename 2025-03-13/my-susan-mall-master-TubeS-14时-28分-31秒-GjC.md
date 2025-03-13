根据提供的Git diff记录，以下是对代码更改的评审：

### 1. 新增邮件发送和Freemarker依赖
在`pom.xml`中新增了`spring-boot-starter-mail`和`spring-boot-starter-freemarker`依赖，表明项目将支持邮件发送和HTML邮件模板的生成。这是一个良好的功能扩展，但需要确保邮件服务配置正确，且测试邮件发送功能是否正常。

### 2. 添加ApplicationConfig类
新增了`ApplicationConfig`类，但没有具体内容。这是一个好习惯，因为它有助于集中管理应用程序的配置信息。应确保在此类中配置所有必要的属性和Bean。

### 3. 依赖包版本和作用域
确保所有依赖包的版本都是兼容的，且作用域正确。例如，`easyexcel`的版本为3.3.3，这是一个较新的版本，可能需要检查与现有代码的兼容性。

### 4. 代码重命名
将多个实体类从`excel`包重命名为`common`包，这是一个合理的变更，因为它可能意味着这些实体类不再仅用于Excel处理。需要确保重命名后的类在所有相关代码中被正确引用。

### 5. 新增RemoteLoginEmailEntity和EmailTypeEnum
新增了`RemoteLoginEmailEntity`类和`EmailTypeEnum`枚举，这表明项目将处理异地登录的邮件发送。需要确保邮件发送逻辑正确实现，并且邮件模板内容与实体类字段一致。

### 6. 修改CommonTaskEntity类
在`CommonTaskEntity`类中，将任务类型注释从"通用excel导出"修改为"通用excel导出 2：发邮件"，表明现在这个实体类可以用于Excel导出和邮件发送。需要确保相关的业务逻辑也进行了相应的更新。

### 7. GeoIpHelper类变更
在`GeoIpHelper`类中，增加了`getNotFoundCity`方法来处理IP地理位置查询失败的情况。这是一个良好的异常处理措施。

### 8. CommonTaskAspect类变更
在`CommonTaskAspect`类中，将任务类型从`TaskTypeEnum.MENU`修改为`TaskTypeEnum.EXPORT_EXCEL`。这需要确保`ExcelBizTypeEnum`枚举和相关的业务逻辑也进行了相应的更新。

### 9. mapper文件重命名
将多个mapper文件从`excel`包重命名为`common`包，这与实体类的重命名策略一致。需要确保重命名后的文件在MyBatis配置中被正确引用。

### 10. 新增EmailService和IEmailService接口
新增了`EmailService`类和`IEmailService`接口，这表明项目将实现邮件发送服务的抽象和实现。需要确保邮件发送逻辑正确实现，并且接口文档更新。

### 11. 新增RemoteLoginEmailService类
新增了`RemoteLoginEmailService`类，用于发送异地登录的邮件。需要确保邮件发送逻辑正确实现，并且邮件模板内容与实体类字段一致。

### 12. UserService类变更
在`UserService`类中，增加了记录异地登录数据的逻辑，并创建了相应的任务。需要确保这个逻辑能够正确触发邮件发送，并且测试邮件发送功能。

### 13. 其他变更
- `mall-job`模块的`JobApplication`类扫描的包从`{"cn.net.susan"}`更改为`{"cn.net.susan.mapper"}`。
- 新增了`mall-job`模块的`TestController`类，用于测试邮件发送功能。

### 总结
这次代码更改引入了新的功能，包括邮件发送和异地登录检测。代码结构得到了一些优化，但需要确保所有更改都经过充分的测试，以确保功能的正确性和系统的稳定性。