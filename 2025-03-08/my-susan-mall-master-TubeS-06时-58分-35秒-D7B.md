### 代码评审

#### mall-business/pom.xml
- **添加了新的依赖**: `jjwt`, `spring-security-core`, `spring-security-web`, `spring-security-config`, `mall-common`. 这些依赖似乎用于用户认证和授权，以及JWT令牌处理。
- **移除了Spring Boot Actuator依赖**: 可能是因为不再需要监控和管理功能。
- **新增的mall-common依赖**: 表明可能存在代码共享或模块化设计。

#### mall-business/src/main/java/cn/net/susan/entity/auth/AuthUserEntity.java
- **新增实体类**: 用于存储用户认证信息，包括用户名、密码、验证码和手机号。
- **数据校验**: 通过`@NotBlank`注解确保密码和验证码不为空。

#### mall-business/src/main/java/cn/net/susan/entity/auth/TokenEntity.java
- **新增实体类**: 用于存储JWT令牌和用户名。

#### mall-business/src/main/java/cn/net/susan/helper/TokenHelper.java
- **新增工具类**: 用于生成、解析和删除JWT令牌，以及与Redis交互。
- **依赖注入**: 依赖于`RedisUtil`和`UserDetails`。
- **安全性**: 使用`HS512`算法生成JWT令牌，并设置了过期时间。

#### mall-business/src/main/java/cn/net/susan/service/sys/UserService.java
- **新增方法**: `login`用于用户登录，返回JWT令牌。
- **新增方法**: `logout`用于用户退出登录。

#### mall-business/src/main/java/cn/net/susan/util/RedisUtil.java
- **新增工具类**: 用于与Redis进行交互，包括设置、获取和删除键值对。

#### mall-business/src/main/java/cn/net/susan/util/SpringBeanUtil.java
- **新增工具类**: 用于获取Spring容器中的Bean实例。

#### mall-common/src/main/java/cn/net/susan/constant/NumberConstant.java
- **新增常量类**: 定义了一些常用的数字常量。

#### mall-common/src/main/java/cn/net/susan/util/TokenUtil.java
- **新增工具类**: 用于从HTTP请求中获取JWT令牌。

#### mall-mgt/pom.xml
- **移除了Spring Security依赖**: 可能是因为在mall-mgt模块中不再需要Spring Security。

#### mall-mgt/src/main/java/cn/net/susan/ApiApplication.java
- **添加了`scanBasePackages`**: 显式指定了Spring Boot应用的扫描包路径。

#### mall-mgt/src/main/java/cn/net/susan/annoation/NoLogin.java
- **新增注解**: 用于标记无需登录即可访问的方法。

#### mall-mgt/src/main/java/cn/net/susan/config/JwtTokenConfigurer.java
- **新增配置类**: 用于配置JWT令牌过滤器。

#### mall-mgt/src/main/java/cn/net/susan/config/RedisConfig.java
- **新增配置类**: 用于配置Redis模板，并使用FastJson序列化器。

#### mall-mgt/src/main/java/cn/net/susan/config/SpringSecurityConfig.java
- **新增配置类**: 用于配置Spring Security，包括HTTP安全、会话管理和权限控制。
- **使用JWT令牌过滤器**: 通过`JwtTokenConfigurer`类添加JWT令牌过滤器。

#### mall-mgt/src/main/java/cn/net/susan/config/SwaggerConfig.java
- **配置Swagger**: 用于生成API文档。

#### mall-mgt/src/main/java/cn/net/susan/controller/web/WebUserController.java
- **新增控制器**: 用于处理用户登录和退出登录请求。

#### mall-mgt/src/main/java/cn/net/susan/filter/JwtTokenFilter.java
- **新增过滤器**: 用于验证JWT令牌，并设置Spring Security的认证上下文。

### 总结
- 这次代码更新主要集中在用户认证和授权方面，包括JWT令牌处理、Redis缓存和Spring Security配置。
- 添加了多个工具类和配置类，以简化代码和增强功能。
- 建议对代码进行单元测试，以确保功能的正确性和稳定性。