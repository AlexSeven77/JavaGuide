DDD 后端开发介绍

![image.png](https://ucc.alicdn.com/pic/developer-ecology/d92764a7963f43068273133f9a1ac6f9.png)

https://developer.aliyun.com/article/719251

![image.png](https://ucc.alicdn.com/pic/developer-ecology/9e6ceb0223134da09e4832c1fcac9a82.png)

*3.1.1 - Types 模块*

Types模块是保存可以对外暴露的Domain Primitives的地方。Domain Primitives因为是无状态的逻辑，可以对外暴露，所以经常被包含在对外的API接口中，需要单独成为模块。Types模块不依赖任何类库，纯 POJO 。

![image.png](https://ucc.alicdn.com/pic/developer-ecology/e6be74513715472da882a44710cd68e1.png)

*3.1.2 - Domain 模块*

Domain 模块是核心业务逻辑的集中地，包含有状态的Entity、领域服务Domain Service、以及各种外部依赖的接口类（如Repository、ACL、中间件等。Domain模块仅依赖Types模块，也是纯 POJO 。

![image.png](https://ucc.alicdn.com/pic/developer-ecology/6d624f59dd6c45998bc5b52cfa27a790.png)

*3.1.3 - Application模块*

Application模块主要包含Application Service和一些相关的类。Application模块依赖Domain模块。还是不依赖任何框架，纯POJO。

![image.png](https://ucc.alicdn.com/pic/developer-ecology/cbf5da9300914845a9bdfb2297353f66.png)

*3.1.4 - Infrastructure模块*

Infrastructure模块包含了Persistence、Messaging、External等模块。比如：Persistence模块包含数据库DAO的实现，包含Data Object、ORM Mapper、Entity到DO的转化类等。Persistence模块要依赖具体的ORM类库，比如MyBatis。如果需要用Spring-Mybatis提供的注解方案，则需要依赖Spring。

![image.png](https://ucc.alicdn.com/pic/developer-ecology/7b9447118e454545a11ca1824150fa29.png)

*3.1.5 - Web模块*

Web模块包含Controller等相关代码。如果用SpringMVC则需要依赖Spring。

![image.png](https://ucc.alicdn.com/pic/developer-ecology/0684cb24145f4b1386fa7009ac9174d9.png)

*3.1.6 - Start模块*

Start模块是SpringBoot的启动类。