根据提供的Git diff记录，以下是对代码变更的评审：

### JwtUserEntity.java
- **新增文件**：JwtUserEntity类被新增，实现了UserDetails接口，用于Spring Security的用户认证。
- **优点**：类的设计符合Spring Security的认证流程，提供了基本的用户信息字段和认证方法。
- **缺点**：未提供密码加密的逻辑，直接存储明文密码，存在安全风险。建议使用PasswordEncoder进行密码加密。

### UserDetailsServiceImpl.java
- **新增文件**：UserDetailsServiceImpl类被新增，实现了UserDetailsService接口，用于加载用户详情。
- **优点**：类的设计符合Spring Security的认证流程，提供了用户认证的基本逻辑。
- **缺点**：示例中直接使用固定的密码“123456”进行认证，实际应用中应使用数据库中的加密密码进行认证。

### UserService.java
- **变更**：UserService类中新增了用户登录和登出的方法。
- **优点**：实现了用户登录和登出的功能，使用了Spring Security的认证和授权机制。
- **缺点**：示例中使用了TokenHelper进行token生成和删除，但TokenHelper类已被删除，需要使用TokenUtil类。

### PasswordUtil.java
- **新增文件**：PasswordUtil类被新增，用于密码加密。
- **优点**：实现了密码加密的功能，增加了系统的安全性。
- **缺点**：示例中使用了固定的私钥，实际应用中应从配置文件中读取。

### TokenUtil.java
- **重命名**：TokenHelper类被重命名为TokenUtil类。
- **优点**：类名更符合Java命名规范。
- **缺点**：TokenUtil类中缺少一些TokenHelper类的方法，需要补充。

### TokenUtil.java (mall-common)
- **删除文件**：TokenUtil类被删除。
- **优点**：避免了重复的类定义。
- **缺点**：如果其他模块还在使用TokenUtil类，需要迁移到TokenUtil.java。

### SpringSecurityConfig.java
- **变更**：新增了PasswordEncoder和GrantedAuthorityDefaults的Bean定义。
- **优点**：配置了密码加密方式和权限默认前缀。
- **缺点**：示例中未配置具体的权限控制规则。

### UserController.java
- **变更**：@PreAuthorize注解中的角色权限前缀从"ROLE_"改为"USER"。
- **优点**：更符合Spring Security的权限控制规则。
- **缺点**：示例中未配置具体的权限控制规则。

### JwtTokenFilter.java
- **变更**：TokenHelper类被重命名为TokenUtil类。
- **优点**：类名更符合Java命名规范。
- **缺点**：示例中使用了TokenHelper类的方法，需要迁移到TokenUtil类。

### application.yml
- **变更**：修改了用户密码和角色的配置。
- **优点**：配置了用户密码和角色信息。
- **缺点**：示例中未配置其他必要的配置项。