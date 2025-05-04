根据提供的 `git diff` 记录，以下是对代码变更的评审：

### 1. `Limit.java` 注解变更

- **变更点**：将 `permitsPerSecond` 的类型从 `double` 改为 `int`。
- **理由**：通常限流次数是整数，使用 `int` 类型可以避免浮点数的不精确问题，并提高性能。
- **建议**：此变更合理，可以接受。

### 2. 新增 `LimitDistributedConfig.java`

- **变更点**：新增配置类用于分布式限流功能。
- **内容**：包含 `LimitDistributedAspect` 和 `limitScript` 的配置。
- **理由**：分布式限流需要额外的配置和脚本支持，此变更合理。
- **建议**：确保 `limitScript` 脚本正确无误，并且配置的 `StringRedisTemplate` 和 `DefaultRedisScript` 正确初始化。

### 3. 新增 `SimpleLimitConfig.java`

- **变更点**：新增配置类用于简单限流功能。
- **内容**：包含 `SimpleLimitAspect` 的配置。
- **理由**：简单限流功能也需要配置支持，此变更合理。
- **建议**：确保 `SimpleLimitAspect` 正确初始化。

### 4. 新增 `EnableDistributedLimit.java` 和 `EnableSimpleLimit.java`

- **变更点**：新增启用分布式限流和简单限流的注解。
- **理由**：使用注解可以简化配置，提高代码可读性。
- **建议**：确保这两个注解正确导入对应的配置类。

### 5. `LimitTypeEnum.java`

- **变更点**：新增枚举类用于定义限流类型。
- **内容**：包含 `ALL`, `IP`, `USER_ID` 三个类型。
- **理由**：限流类型枚举化可以提高代码的可维护性和可读性。
- **建议**：确保枚举值和描述准确无误。

### 6. `LimitDistributedAspect.java`

- **变更点**：新增基于Redis的限流切面。
- **内容**：包含限流逻辑和Lua脚本执行。
- **理由**：分布式限流需要考虑多个实例的同步，使用Redis是常见的解决方案。
- **建议**：确保Lua脚本正确执行，并且异常处理逻辑完善。

### 7. `SimpleLimitAspect.java`（原 `LimitAspect.java`）

- **变更点**：重命名类为 `SimpleLimitAspect`。
- **理由**：可能是因为功能从通用限流变为简单限流。
- **建议**：确保重命名后的类和原有功能一致。

### 8. `ApiApplication.java`

- **变更点**：在启动类上添加 `@EnableDistributedLimit` 注解。
- **理由**：启用分布式限流功能。
- **建议**：确保此变更不会影响到其他功能。

### 9. `GeoIpController.java`

- **变更点**：注释掉原有的限流注解，并添加新的限流注解。
- **理由**：可能是因为限流策略变更。
- **建议**：确保新的限流策略符合业务需求。

总的来说，这些变更都是为了提高代码的可维护性和功能完善，建议在部署前进行充分的测试以确保功能的正确性和稳定性。