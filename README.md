##项目简介：

-这是一个SpringBoot后端餐厅评价项目，支持用户上传图片，搜索餐厅，提交评论。

-这个项目用到了keycloak，ElasticSearch，kibana。

-系统用Keycloak发放JWT然后通过Spring security实现无状态鉴权，实现了用户访问限制以及点评限制。

-数据通过ElastiSearch储存数据与索引，支持模糊字搜索，评分过滤以及地理位置搜索。


用户功能：

-上传餐厅图片

-创建,编辑，删除餐厅

-搜索餐厅通过餐厅名字，菜品，模糊搜索

-根据地理位置搜索餐厅

-根据评分筛选餐厅

-发布，编辑，删除评论

-仅允许48小时内编辑评论


-限制发送多条评论
![4921768497458_ pic](https://github.com/user-attachments/assets/30a5b789-fe48-4ff3-a597-92905be23dae)
