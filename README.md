## 项目简介：

- 这是一个SpringBoot后端餐厅评价项目，支持用户上传图片，搜索餐厅，提交评论

- 这个项目用到了keycloak，ElasticSearch，kibana

- 系统用Keycloak发放JWT然后通过Spring security实现无状态鉴权，实现了用户访问限制以及点评限制

- 数据通过ElastiSearch储存与索引，支持模糊字搜索，评分过滤以及地理位置搜索



## 用户功能：

- 上传餐厅图片

- 创建,编辑，删除餐厅

- 搜索餐厅通过餐厅名字，菜品，模糊搜索

- 根据地理位置搜索餐厅

- 根据评分筛选餐厅

- 发布，编辑，删除评论

- 仅允许48小时内编辑评论

- 限制发送多条评论



## 系统特性：

- Keycloak和JWT提供用户验证功能

- JWT通过SpringSecurity鉴权

- ElasticSearch储存数据和索引

- Kibana提供了可视化

- 使用了docker来启动KeyCloak，ElasticSearch， Kibana

- 上传的图片储存到本地


## 系统构架图：
![4921768497458_ pic](https://github.com/user-attachments/assets/30a5b789-fe48-4ff3-a597-92905be23dae)


## 技术栈
- java21
- SpringBoot
- ElasticSearch(搜索 + 储存)
- Kibana(可视化工具)
- KeyCloak(提供认证)
- Docker(启动服务)

## 项目结构
- config(Security + keyCloak)

- controllers(请求入口)

- domains(entities, dtos)

- mappers(dtos <=> entities)
  
- repository(ElasticSearch repository)

- services(处理业务逻辑)

- exceptions(自定义异常)


## 项目亮点
- 使用KeyCloak登陆，退出，注册账号然后使用SpringSecurity相结合进行Token的验证(避免了手动实现登陆逻辑)
- Lombok和MapStruct相结合，使用了Lombok减少entity以及dto的样板代码，使用MapStruct来进行entity和dto之前的映射提供代码的可读性以及可维护性
- 使用了ElasticSearch替代了传统的关系型数据库对餐厅以及评论数据进行了储存，提供了模糊关键字搜索，Geo搜索，评分过滤的功能
- 对展示的餐厅进行了分页避免了一次加载大量数据
- 创建了自定义异常并通过ErrorController去进行全局异常处理同一封装业务与Http响应
- 实现了图片的上传，上传的图片会储存到本地
- 使用SpringSecurity对非登陆用户进行限制，限制未登陆的用户无法进行评论
- 在service增添逻辑让用户只能对同一家餐馆评论一条并且只能在评论后48小时内进行编辑，超过时间或者已经评论过再次评论的话就会抛出自定义的异常
- 使用了SpringbootTest进行测试，验证了核心业务流程的正常运行

## 启动方式

1.启动依赖服务

项目根目录执行：docker-compose up
