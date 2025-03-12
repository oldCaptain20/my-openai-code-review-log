根据提供的Git diff记录，以下是对代码变更的评审：

### mall-business/pom.xml
- **添加依赖**: 添加了`spring-boot-starter-websocket`依赖，这表明项目可能新增了WebSocket功能。需要确认WebSocket的具体用途和实现细节。

### mall-business/src/main/java/cn/net/susan/entity/excel/CommonNotifyConditionEntity.java 和 CommonNotifyEntity.java
- **新增实体类**: 新增了`CommonNotifyConditionEntity`和`CommonNotifyEntity`类，用于通知信息的存储和查询。这表明项目可能新增了通知功能。
- **字段定义**: 字段定义清晰，包含了通知的基本信息，如标题、内容、类型、阅读状态等。需要确认这些字段的用途和逻辑。

### mall-business/src/main/java/cn/net/susan/mapper/excel/CommonNotifyMapper.java
- **新增Mapper接口**: 新增了`CommonNotifyMapper`接口，定义了通知的CRUD操作。这表明项目可能新增了通知的持久化层。

### mall-business/src/main/java/cn/net/susan/service/base/BaseService.java
- **修改方法**: `export`方法从无返回值修改为返回`String`，并添加了`doExport`方法的实现。这表明导出功能可能进行了修改或新增。

### mall-business/src/main/java/cn/net/susan/service/excel/CommonNotifyService.java
- **新增服务层**: 新增了`CommonNotifyService`服务层，实现了通知的查询、添加、修改、删除等操作。这表明项目可能新增了通知的Service层。

### mall-business/src/main/resources/cn/net/susan/mapper/excel/CommonNotifyMapper.xml
- **新增Mapper XML**: 新增了`CommonNotifyMapper.xml`，定义了通知的数据库操作。这表明项目可能新增了通知的数据库操作。

### mall-job/src/main/java/cn/net/susan/config/WebSocketConfig.java
- **新增配置类**: 新增了`WebSocketConfig`配置类，用于配置WebSocket。这表明项目可能新增了WebSocket服务端。

### mall-job/src/main/java/cn/net/susan/job/CommonNotifyJob.java
- **新增Job**: 新增了`CommonNotifyJob`定时任务，用于推送通知。这表明项目可能新增了定时推送通知的功能。

### mall-job/src/main/java/cn/net/susan/job/CommonTaskJob.java
- **类名修改**: 将`CommonTaskHandler`类重命名为`CommonTaskJob`。这可能是为了更准确地描述类的功能。

### mall-job/src/main/java/cn/net/susan/websocket/WebSocketServer.java
- **新增WebSocket服务端**: 新增了`WebSocketServer`类，用于处理WebSocket连接和消息。这表明项目可能新增了WebSocket服务端。

### mall-job/src/main/resources/application.yml
- **修改日志级别**: 将`cn.net.susan.mapper`的日志级别修改为`debug`。这可能是为了调试数据库操作。

### mall-mgt/src/main/java/cn/net/susan/controller/excel/CommonNotifyController.java
- **新增Controller**: 新增了`CommonNotifyController`控制器，定义了通知的接口。这表明项目可能新增了通知的接口。

### 总结
- 项目新增了通知功能，包括实体类、Mapper、Service、Controller、Mapper XML、Job、WebSocket服务端等。
- 需要确认WebSocket的具体用途和实现细节，以及通知功能的详细逻辑和流程。

## 建议
- 在新增功能时，建议进行充分的测试，确保功能的正确性和稳定性。
- 建议对代码进行适当的注释，提高代码的可读性和可维护性。
- 建议对项目进行版本控制，方便跟踪代码变更和回滚。