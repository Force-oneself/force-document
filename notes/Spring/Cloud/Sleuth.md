| Name                                                         | Default                                                      | Description                                                  |
| :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| spring.sleuth.async.configurer.enabled                       | `true`                                                       | 启用默认的AsyncConfigurer.                                   |
| spring.sleuth.async.enabled                                  | `true`                                                       | 启用检测与异步相关的组件，以便在线程之间传递跟踪信息.        |
| spring.sleuth.async.ignored-beans                            |                                                              | {@link java.util.concurrent.Executor} Bean名称列表，应忽略这些名称，而不应将它们包装在跟踪表示中. |
| spring.sleuth.baggage.correlation-enabled                    | `true`                                                       | 使行李环境与日志环境相关联.                                  |
| spring.sleuth.baggage.correlation-fields                     |                                                              |                                                              |
| spring.sleuth.baggage.local-fields                           |                                                              |                                                              |
| spring.sleuth.baggage.remote-fields                          |                                                              | 与在线中引用的过程中相同的字段的列表。 例如，字段“ x-vcap-request-id”将按原样设置，包括前缀. |
| spring.sleuth.baggage.tag-fields                             |                                                              |                                                              |
| spring.sleuth.circuitbreaker.enabled                         | `true`                                                       | 启用Spring Cloud CircuitBreaker工具.                         |
| spring.sleuth.enabled                                        | `true`                                                       |                                                              |
| spring.sleuth.feign.enabled                                  | `true`                                                       | 在使用Feign时启用跨度信息传播.                               |
| spring.sleuth.feign.processor.enabled                        | `true`                                                       | 启用将Feign Context包装在其跟踪表示中的后处理器.             |
| spring.sleuth.function.enabled                               | `true`                                                       | 启用对Spring Cloud Function和基于Spring Cloud Function的项目的检测（例如Spring Cloud Stream）. |
| spring.sleuth.grpc.enabled                                   | `true`                                                       | 使用GRPC时启用跨度信息传播.                                  |
| spring.sleuth.http.enabled                                   | `true`                                                       | 启用HTTP支持.                                                |
| spring.sleuth.integration.enabled                            | `true`                                                       | 启用Spring Integration侦探检测.                              |
| spring.sleuth.integration.patterns                           | `[!hystrixStreamOutput*, **, !channel**]`                    | 通道名称将与之匹配的模式数组。 @see org.springframework.integration.config.GlobalChannelInterceptor＃patterns（）默认为与Hystrix Stream和功能Stream通道名称不匹配的任何通道名称. |
| spring.sleuth.integration.websockets.enabled                 | `true`                                                       | 启用对WebSocket的跟踪.                                       |
| spring.sleuth.messaging.enabled                              | `false`                                                      | 是否应该打开消息传递.                                        |
| spring.sleuth.messaging.jms.enabled                          | `true`                                                       | 启用JMS跟踪.                                                 |
| spring.sleuth.messaging.jms.remote-service-name              | `jms`                                                        | JMS远程服务名称.                                             |
| spring.sleuth.messaging.kafka.enabled                        | `true`                                                       | 启用Kafka跟踪.                                               |
| spring.sleuth.messaging.kafka.mapper.enabled                 | `true`                                                       | 为Kafka启用DefaultKafkaHeaderMapper跟踪.                     |
| spring.sleuth.messaging.kafka.remote-service-name            | `kafka`                                                      | Kafka远程服务名称.                                           |
| spring.sleuth.messaging.kafka.streams.enabled                | `false`                                                      | 是否应打开Kafka流.                                           |
| spring.sleuth.messaging.rabbit.enabled                       | `true`                                                       | 启用RabbitMQ跟踪.                                            |
| spring.sleuth.messaging.rabbit.remote-service-name           | `rabbitmq`                                                   | Rabbit远程服务名称.                                          |
| spring.sleuth.mongodb.enabled                                | `true`                                                       | 启用MongoDb的跟踪.                                           |
| spring.sleuth.opentracing.enabled                            | `true`                                                       | 启用OpenTracing支持.                                         |
| spring.sleuth.propagation.type                               |                                                              | 跟踪上下文传播类型.                                          |
| spring.sleuth.quartz.enabled                                 | `true`                                                       | 启用Quartz跟踪.                                              |
| spring.sleuth.reactor.decorate-on-each                       | `true`                                                       | 当在每个运算符上使用true装饰时，性能会下降，但是日志记录将始终包含每个运算符中的跟踪条目。 如果在最后一个运算符上使用false修饰符，则会有更好的表现，但日志记录可能并不总是包含跟踪条目。 通过{@link SleuthReactorProperties＃instrumentationType} @不推荐使用显式值 |
| spring.sleuth.reactor.enabled                                | `true`                                                       | 如果为true，则启用对反应堆的检测.                            |
| spring.sleuth.reactor.instrumentation-type                   |                                                              |                                                              |
| spring.sleuth.redis.enabled                                  | `true`                                                       | 使用Redis时启用跨度信息传播.                                 |
| spring.sleuth.redis.remote-service-name                      | `redis`                                                      | 远程Redis端点的服务名称.                                     |
| spring.sleuth.rpc.enabled                                    | `true`                                                       | 启用RPC跟踪.                                                 |
| spring.sleuth.rxjava.schedulers.hook.enabled                 | `true`                                                       | 通过RxJavaSchedulersHook启用对RxJava的支持.                  |
| spring.sleuth.rxjava.schedulers.ignoredthreads               | `[HystrixMetricPoller, ^RxComputation.*$]`                   | 不会采样其跨度的线程名称.                                    |
| spring.sleuth.sampler.probability                            |                                                              | 应该采样的请求的概率。 例如。 1.0-应抽样100％的请求。 精度仅是整数（即不支持0.1％的迹线）. |
| spring.sleuth.sampler.rate                                   | `10`                                                         | 对于低流量的端点，每秒速率可能是一个不错的选择，因为它可以为您提供浪涌保护。 例如，您可能永远不会期望端点每秒收到50个以上的请求。 如果流量突然激增到每秒5000个请求，那么每秒仍然会有50条痕迹。 相反，如果您有一个百分比（例如10％），则同一浪涌最终将导致每秒500条痕迹，这可能会使您的存储设备超负荷。 为此，Amazon X-Ray包括一个限速采样器（名为Reservoir）。 勇敢者通过{@link brave.sampler.RateLimitingSampler}采用了相同的方法. |
| spring.sleuth.sampler.refresh.enabled                        | `true`                                                       | 启用采样器的刷新范围.                                        |
| spring.sleuth.scheduled.enabled                              | `true`                                                       | 为{@link org.springframework.scheduling.annotation.Scheduled}启用跟踪. |
| spring.sleuth.scheduled.skip-pattern                         |                                                              | 应该跳过的类的完全限定名称的模式.                            |
| spring.sleuth.span-filter.additional-span-name-patterns-to-ignore |                                                              | 要忽略的跨度名称的其他列表。 将附加到{@link #spanNamePatternsToSkip}. |
| spring.sleuth.span-filter.enabled                            | `false`                                                      | 将打开默认的Sleuth处理程序机制。 可能会忽略某些跨度的导出;   |
| spring.sleuth.span-filter.span-name-patterns-to-skip         | `^catalogWatchTaskScheduler$`                                | 要忽略的范围名称列表。 它们不会被发送到外部系统.             |
| spring.sleuth.supports-join                                  | `true`                                                       | True表示跟踪系统支持在客户端和服务器之间共享跨度ID.          |
| spring.sleuth.trace-id128                                    | `false`                                                      | 为true时，生成128位跟踪ID，而不是64位跟踪ID.                 |
| spring.sleuth.tracer.mode                                    |                                                              | 设置应该选择哪个跟踪器实现.                                  |
| spring.sleuth.web.additional-skip-pattern                    |                                                              | 跟踪中应跳过的URL的其他模式。 这将附加到{@link SleuthWebProperties＃skipPattern}. |
| spring.sleuth.web.client.enabled                             | `true`                                                       | 启用拦截器注入{@link org.springframework.web.client.RestTemplate}. |
| spring.sleuth.web.client.skip-pattern                        |                                                              | 在客户端跟踪中应跳过的URL的模式.                             |
| spring.sleuth.web.enabled                                    | `true`                                                       | 如果为true，则启用对Web应用程序的检测.                       |
| spring.sleuth.web.filter-order                               | `0`                                                          | 跟踪过滤器应注册的顺序.                                      |
| spring.sleuth.web.ignore-auto-configured-skip-patterns       | `false`                                                      | 如果设置为true，将忽略自动配置的跳过模式.                    |
| spring.sleuth.web.servlet.enabled                            | `true`                                                       | 启用Servlet检测.                                             |
| spring.sleuth.web.skip-pattern                               | `/api-docs.**  |/swagger.** |.**\.png  |.**\.css |.**\.js |.**\.html |/favicon.ico |/hystrix.stream` | 跟踪中应跳过的URL的模式.                                     |
| spring.sleuth.web.webclient.enabled                          | `true`                                                       | 为WebClient启用跟踪检测.                                     |
| spring.zipkin.activemq.message-max-bytes                     | `100000`                                                     | 通过ActiveMQ发送给Zipkin的跨度给定消息的最大字节数.          |
| spring.zipkin.activemq.queue                                 | `zipkin`                                                     | ActiveMQ队列的名称，应将跨度发送到Zipkin.                    |
| spring.zipkin.base-url                                       | `localhost:9411/`                                            | zipkin查询服务器实例的URL。 如果在服务发现中注册了Zipkin，您还可以提供Zipkin服务器的服务ID（例如[zipkinserver /]（https：// zipkinserver /））. |
| spring.zipkin.compression.enabled                            | `false`                                                      |                                                              |
| spring.zipkin.discovery-client-enabled                       |                                                              | 如果设置为{@code false}，则始终将{@link ZipkinProperties＃baseUrl}视为URL. |
| spring.zipkin.enabled                                        | `true`                                                       | 允许发送跨度到Zipkin.                                        |
| spring.zipkin.encoder                                        |                                                              | 发送到Zipkin的跨度的编码类型。 如果您的服务器不是最新服务器，请设置为{@link SpanBytesEncoder＃JSON_V1}. |
| spring.zipkin.kafka.topic                                    | `zipkin`                                                     | Kafka主题的名称，应将跨度发送到Zipkin.                       |
| spring.zipkin.locator.discovery.enabled                      | `false`                                                      | 通过服务发现启用主机名定位.                                  |
| spring.zipkin.message-timeout                                | `1`                                                          | 将待处理的跨度批量发送到Zipkin之前的超时时间（以秒为单位）.  |
| spring.zipkin.rabbitmq.addresses                             |                                                              | 用于发送跨度到Zipkin的RabbitMQ经纪人的地址                   |
| spring.zipkin.rabbitmq.queue                                 | `zipkin`                                                     | 应该将跨度发送到Zipkin的RabbitMQ队列的名称.                  |
| spring.zipkin.sender.type                                    |                                                              | 将跨度发送到Zipkin的方法.                                    |
| spring.zipkin.service.name                                   |                                                              | 通过HTTP从中发送跨度的服务名称，该名称应显示在Zipkin中.      |