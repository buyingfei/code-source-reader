#### 事务源码分析

##### 注解 **EnableTransactionManagement** 为事务分析入口,注意这里的AdviceMode，默认为JDK 代理

![Snipaste_2021-03-31_09-55-42](.\img\Snipaste_2021-03-31_09-55-42.png)

##### 进入 TransactionManagementConfigurationSelector 配置选择器中
![Snipaste_2021-03-31_11-00-17](.\img\Snipaste_2021-03-31_10-06-39.png)

##### 分析**ProxyTransactionManagementConfiguration** 配置类

![Snipaste_2021-03-31_11-00-17](.\img\tranaction003.png)

##### 根据advisor 能找到pointcut

![Snipaste_2021-03-31_11-00-17](.\img\Snipaste_2021-03-31_10-37-25.png)
##### **TransactionAttributeSourcePointcut pointcut ** 根据名字可知为事务属性切入点，其需要一个 TransactionAttributeSource 接口，查看TransactionAttributeSource 接口的一个实现类，有一个

![Snipaste_2021-03-31_11-00-17](.\img\Snipaste_2021-03-31_11-00-17.png)

##### 走入 AnnotationTransactionAttributeSource 类，并注意一下代码
![Snipaste_2021-03-31_11-00-17](.\img\Snipaste_2021-03-31_11-18-10.png)


##### 走入 SpringTransactionAnnotationParser 类中
![Snipaste_2021-03-31_11-00-17](.\img\Snipaste_2021-03-31_11-12-26.png)

##### AOP  增强 类：TransactionInterceptor，主要观察invoke 方法

![Snipaste_2021-03-31_11-00-17](.\img\Snipaste_2021-03-31_11-30-03.png)

#### 事务执行
![Snipaste_2021-03-31_11-00-17](.\img\trans004.png)
