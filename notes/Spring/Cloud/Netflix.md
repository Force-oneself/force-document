| Name                                                         | Default | Description                                                  |
| :----------------------------------------------------------- | :------ | :----------------------------------------------------------- |
| eureka.client.eureka-connection-idle-timeout-seconds         | 30      | 指示与eureka服务器的HTTP连接在关闭之前可以保持空闲状态的时间（以秒为单位）。 在AWS环境中，建议将该值设置为30秒或更短，因为防火墙会在几分钟后清除连接信息，使连接处于悬吊状态. |
| eureka.client.eureka-server-connect-timeout-seconds          | 5       | 指示与eureka服务器的连接需要超时之前要等待的时间（以秒为单位）。 请注意，客户端中的连接由org.apache.http.client.HttpClient池化，此设置影响实际的连接创建以及从池中获取连接的等待时间. |
| eureka.client.eureka-server-d-n-s-name                       |         | 获取要查询以获取eureka服务器列表的DNS名称。如果合同通过实现serviceUrls返回服务URL，则不需要此信息。 当useDnsForFetchingServiceUrls设置为true且eureka客户端期望DNS以某种方式配置时，将使用DNS机制，以便它可以动态获取更改的eureka服务器。 这些更改在运行时有效. |
| eureka.client.eureka-server-port                             |         | 当eureka服务器列表来自DNS时，获取用于构造服务URL以便与eureka服务器联系的端口。如果合同返回服务URL eurekaServerServiceUrls（String），则不需要此信息。 当useDnsForFetchingServiceUrls设置为true且eureka客户端期望DNS以某种方式配置时，将使用DNS机制，以便它可以动态获取更改的eureka服务器。 这些更改在运行时有效. |
| eureka.client.eureka-server-read-timeout-seconds             | 8       | 指示从eureka服务器读取超时需要等待多长时间（以秒为单位）.    |
| eureka.client.eureka-server-total-connections                | 200     | 获取从eureka客户端到所有eureka服务器的允许的连接总数.        |
| eureka.client.eureka-server-total-connections-per-host       | 50      | 获取从eureka客户端到eureka服务器主机的允许的连接总数.        |
| eureka.client.eureka-server-u-r-l-context                    |         | 当eureka服务器列表来自DNS时，获取用于构造服务URL以便与eureka服务器联系的URL上下文。 如果合同从eurekaServerServiceUrls返回服务URL，则不需要此信息。 当useDnsForFetchingServiceUrls设置为true且eureka客户端期望DNS以某种方式配置时，将使用DNS机制，以便它可以动态获取更改的eureka服务器。 这些更改在运行时有效. |
| eureka.client.eureka-service-url-poll-interval-seconds       | 0       | 指示轮询尤里卡服务器信息更改的频率（以秒为单位）。 可以添加或删除Eureka服务器，并且此设置控制Eureka客户端应该多久知道一次. |
| eureka.client.prefer-same-zone-eureka                        | true    | 指示此实例是否应出于延迟和/或其他原因尝试在同一区域中使用eureka服务器。 理想情况下，将eureka客户端配置为与同一区域中的服务器进行通信，这些更改在运行时在下一个注册表获取周期生效（如registryFetchIntervalSeconds所指定） |
| eureka.client.register-with-eureka                           | true    | 指示此实例是否应在eureka服务器上注册其信息以供他人发现。 在某些情况下，您不希望发现实例，而只希望发现其他实例. |
| eureka.server.peer-eureka-nodes-update-interval-ms           | 0       |                                                              |
| eureka.server.peer-eureka-status-refresh-time-interval-ms    | 0       |                                                              |
| management.endpoint.hystrix.config                           |         | Hystrix设置。 传统上，这些是使用servlet参数设置的。 有关更多详细信息，请参考Hystrix的文档。. |
| management.endpoint.hystrix.stream.enabled                   | true    | 是否启用hystrix.stream端点.                                  |
| management.metrics.binders.hystrix.enabled                   | true    | 启用OK Http Client工厂bean的创建.                            |
| ribbon.eureka.enabled                                        | true    | 允许将Eureka与Ribbon一起使用.                                |
| spring.cloud.circuitbreaker.hystrix.enabled                  | true    | 启用Hystrix Spring Cloud CircuitBreaker API实现的自动配置.   |
| spring.cloud.loadbalancer.eureka.approximate-zone-from-hostname | false   | 用于确定我们是否应尝试从主机名获取`zone`值.                  |
| spring.cloud.loadbalancer.ribbon.enabled                     | true    | 导致默认情况下使用“ RibbonLoadBalancerClient”.               |
| zuul.ribbon-isolation-strategy                               |         |                                                              |
| zuul.ribbon.eager-load.enabled                               | false   | 启动时可立即加载功能区客户端.                                |