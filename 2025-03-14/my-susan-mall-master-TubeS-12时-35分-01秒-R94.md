根据提供的Git diff记录，以下是对代码变更的评审：

**pom.xml变更：**

1. **新增依赖：**
   - 添加了`spring-boot-starter-amqp`依赖，这表明项目中新增了对RabbitMQ的支持。
   - 添加了`jackson-dataformat-xml`依赖，可能是为了支持XML格式的消息序列化。

**评审：**
- 新增RabbitMQ依赖是合理的，如果项目中使用了RabbitMQ作为消息队列，这个变更是有意义的。
- 添加`jackson-dataformat-xml`可能是为了处理特定的XML消息格式，需要确认是否所有XML消息都使用这个转换器。

**RabbitConfig.java变更：**

1. **新增配置类：**
   - 新增了`RabbitConfig`类，用于配置RabbitMQ的相关参数和创建队列、交换机等。

**评审：**
- 新增配置类是合理的，这样可以集中管理RabbitMQ的配置，提高代码的可读性和可维护性。
- 配置类中定义了多个常量，这些常量应该有清晰的文档说明，以便其他开发者理解其用途。

**JwtUserEntity.java变更：**

1. **新增字段：**
   - 在`JwtUserEntity`类中新增了`roles`字段。

**评审：**
- 添加`roles`字段是合理的，如果项目中需要使用角色信息，这个变更是有意义的。
- 需要确保`roles`字段与权限系统相匹配，以便正确地处理用户权限。

**MqHelper.java变更：**

1. **新增工具类：**
   - 新增了`MqHelper`类，用于发送消息到RabbitMQ。

**评审：**
- 新增工具类是合理的，这样可以简化消息发送的操作，提高代码的可读性和可维护性。
- 需要确保`MqHelper`类中的方法能够正确地处理异常情况。

**RepeatSubmitAspect.java变更：**

1. **修改常量：**
   - 将`REPEAT_SUBMIT_PREFIX`常量的值从`"repeatSubmit:"`改为`"repeatSubmit:"`。

**评审：**
- 修改常量值似乎没有实际意义，可能是代码中的笔误。

**UserDetailsServiceImpl.java变更：**

1. **修改方法：**
   - 修改了`UserDetailsServiceImpl`类的构造方法，将`roles`字段添加到`JwtUserEntity`对象中。

**评审：**
- 这个变更看起来是合理的，因为`roles`字段现在在`JwtUserEntity`中被使用。

**ExcelExportTask.java变更：**

1. **修改方法：**
   - 修改了`ExcelExportTask`类的`doExportExcel`方法，增加了对`ExcelBizTypeEnum`的处理。
   - 新增了`getRoutingKey`和`saveNotifyMessage`方法。

**评审：**
- 对`ExcelExportTask`类的修改增加了对业务类型的处理，这是合理的，因为不同的业务类型可能需要不同的处理逻辑。
- 新增的`getRoutingKey`和`saveNotifyMessage`方法看起来是合理的，但需要确保这些方法能够正确地生成路由键和保存通知消息。

**CommonNotifyMapper.xml变更：**

1. **修改XML文件：**
   - 在`CommonNotifyMapper.xml`文件中，将`insert`标签的`useGeneratedKeys`和`keyProperty`属性设置为`true`。

**评审：**
- 这个变更使得`insert`操作能够自动获取主键值，这是合理的，可以提高代码的简洁性。

**application.yml变更：**

1. **添加配置：**
   - 在`application.yml`文件中添加了RabbitMQ的配置。

**评审：**
- 添加RabbitMQ配置是合理的，如果项目中使用了RabbitMQ，这个变更是有意义的。

**总结：**

总体来说，这次代码变更看起来是有意义的，增加了对RabbitMQ的支持，并改进了代码的可读性和可维护性。但是，需要确保所有新增的配置和功能都得到了正确的测试和验证。