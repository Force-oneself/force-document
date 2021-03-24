| Name                                                         | Default                                                      | Description                                                  |
| :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| spring.cloud.gateway.default-filters                         |                                                              | 适用于每条路线的过滤器定义列表.                              |
| spring.cloud.gateway.discovery.locator.enabled               | `false`                                                      | 启用DiscoveryClient网关集成的标志.                           |
| spring.cloud.gateway.discovery.locator.filters               |                                                              |                                                              |
| spring.cloud.gateway.discovery.locator.include-expression    | `true`                                                       | 将评估是否在网关集成中包括服务的SpEL表达式，默认为：true.    |
| spring.cloud.gateway.discovery.locator.lower-case-service-id | `false`                                                      | predicates和filters中的小写serviceId选项，默认为false。 当eureka自动将serviceId大写时，对eureka很有用。 因此MYSERIVCE将与/ myservice / **匹配 |
| spring.cloud.gateway.discovery.locator.predicates            |                                                              |                                                              |
| spring.cloud.gateway.discovery.locator.route-id-prefix       |                                                              | routeId的前缀，默认为DiscoveryClient.getClass（）。getSimpleName（）+“ _”。 将添加服务ID以创建routeId. |
| spring.cloud.gateway.discovery.locator.url-expression        | `'lb://'+serviceId`                                          | 为每条路线创建uri的SpEL表达式，默认为：'lb：//'+ serviceId.  |
| spring.cloud.gateway.enabled                                 | `true`                                                       | 启用网关功能.                                                |
| spring.cloud.gateway.fail-on-route-definition-error          | `true`                                                       | 在路由定义错误时失败的选项，默认为true。 否则，将记录警告.   |
| spring.cloud.gateway.filter.add-request-header.enabled       | `true`                                                       | 启用add-request-header.                                      |
| spring.cloud.gateway.filter.add-request-parameter.enabled    | `true`                                                       | 启用add-request-parameter filter.                            |
| spring.cloud.gateway.filter.add-response-header.enabled      | `true`                                                       | 启用 add-response-header filter.                             |
| spring.cloud.gateway.filter.circuit-breaker.enabled          | `true`                                                       | 启用 circuit-breaker filter.                                 |
| spring.cloud.gateway.filter.dedupe-response-header.enabled   | `true`                                                       | 启用 dedupe-response-header filter.                          |
| spring.cloud.gateway.filter.fallback-headers.enabled         | `true`                                                       | 启用 fallback-headers filter.                                |
| spring.cloud.gateway.filter.hystrix.enabled                  | `true`                                                       | 启用 hystrix filter.                                         |
| spring.cloud.gateway.filter.map-request-header.enabled       | `true`                                                       | 启用 map-request-header filter.                              |
| spring.cloud.gateway.filter.modify-request-body.enabled      | `true`                                                       | 启用 modify-request-body filter.                             |
| spring.cloud.gateway.filter.modify-response-body.enabled     | `true`                                                       | 启用 modify-response-body filter.                            |
| spring.cloud.gateway.filter.prefix-path.enabled              | `true`                                                       | 启用 prefix-path filter.                                     |
| spring.cloud.gateway.filter.preserve-host-header.enabled     | `true`                                                       | 启用 preserve-host-header filter.                            |
| spring.cloud.gateway.filter.redirect-to.enabled              | `true`                                                       | 启用 redirect-to filter.                                     |
| spring.cloud.gateway.filter.remove-hop-by-hop.headers        |                                                              |                                                              |
| spring.cloud.gateway.filter.remove-hop-by-hop.order          |                                                              |                                                              |
| spring.cloud.gateway.filter.remove-request-header.enabled    | `true`                                                       | 启用 remove-request-header filter.                           |
| spring.cloud.gateway.filter.remove-request-parameter.enabled | `true`                                                       | 启用 remove-request-parameter filter.                        |
| spring.cloud.gateway.filter.remove-response-header.enabled   | `true`                                                       | 启用 remove-response-header filter.                          |
| spring.cloud.gateway.filter.request-header-size.enabled      | `true`                                                       | 启用 request-header-size filter.                             |
| spring.cloud.gateway.filter.request-header-to-request-uri.enabled | `true`                                                       | 启用 request-header-to-request-uri filter.                   |
| spring.cloud.gateway.filter.request-rate-limiter.deny-empty-key | `true`                                                       | 如果键解析器返回空键，则切换为拒绝请求，默认为true.          |
| spring.cloud.gateway.filter.request-rate-limiter.empty-key-status-code |                                                              | denyEmptyKey为true时返回的HttpStatus，默认为FORBIDDEN.       |
| spring.cloud.gateway.filter.request-rate-limiter.enabled     | `true`                                                       | 启用 request-rate-limiter filter.                            |
| spring.cloud.gateway.filter.request-size.enabled             | `true`                                                       | 启用 request-size filter.                                    |
| spring.cloud.gateway.filter.retry.enabled                    | `true`                                                       | 启用retry filter.                                            |
| spring.cloud.gateway.filter.rewrite-location-response-header.enabled | `true`                                                       | 启用 rewrite-location-response-header filter.                |
| spring.cloud.gateway.filter.rewrite-location.enabled         | `true`                                                       | 启用 rewrite-location filter.                                |
| spring.cloud.gateway.filter.rewrite-path.enabled             | `true`                                                       | 启用 rewrite-path filter.                                    |
| spring.cloud.gateway.filter.rewrite-response-header.enabled  | `true`                                                       | 启用 rewrite-response-header filter.                         |
| spring.cloud.gateway.filter.save-session.enabled             | `true`                                                       | 启用 save-session filter.                                    |
| spring.cloud.gateway.filter.secure-headers.content-security-policy | `default-src 'self' https:; font-src 'self' https: data:; img-src 'self' https: data:; object-src 'none'; script-src https:; style-src 'self' https: 'unsafe-inline'` |                                                              |
| spring.cloud.gateway.filter.secure-headers.content-type-options | `nosniff`                                                    |                                                              |
| spring.cloud.gateway.filter.secure-headers.disable           |                                                              |                                                              |
| spring.cloud.gateway.filter.secure-headers.download-options  | `noopen`                                                     |                                                              |
| spring.cloud.gateway.filter.secure-headers.enabled           | `true`                                                       | 启用 secure-headers filter.                                  |
| spring.cloud.gateway.filter.secure-headers.frame-options     | `DENY`                                                       |                                                              |
| spring.cloud.gateway.filter.secure-headers.permitted-cross-domain-policies | `none`                                                       |                                                              |
| spring.cloud.gateway.filter.secure-headers.referrer-policy   | `no-referrer`                                                |                                                              |
| spring.cloud.gateway.filter.secure-headers.strict-transport-security | `max-age=631138519`                                          |                                                              |
| spring.cloud.gateway.filter.secure-headers.xss-protection-header | `1 ; mode=block`                                             |                                                              |
| spring.cloud.gateway.filter.set-path.enabled                 | `true`                                                       | 启用 set-path filter.                                        |
| spring.cloud.gateway.filter.set-request-header.enabled       | `true`                                                       | 启用 set-request-header filter.                              |
| spring.cloud.gateway.filter.set-request-host-header.enabled  | `true`                                                       | 启用 set-request-host-header filter.                         |
| spring.cloud.gateway.filter.set-response-header.enabled      | `true`                                                       | 启用 set-response-header filter.                             |
| spring.cloud.gateway.filter.set-status.enabled               | `true`                                                       | 启用 set-status filter.                                      |
| spring.cloud.gateway.filter.strip-prefix.enabled             | `true`                                                       | 启用 strip-prefix filter.                                    |
| spring.cloud.gateway.forwarded.enabled                       | `true`                                                       | 启用 ForwardedHeadersFilter.                                 |
| spring.cloud.gateway.global-filter.adapt-cached-body.enabled | `true`                                                       | 启用 adapt-cached-body global filter.                        |
| spring.cloud.gateway.global-filter.forward-path.enabled      | `true`                                                       | 启用 forward-path global filter.                             |
| spring.cloud.gateway.global-filter.forward-routing.enabled   | `true`                                                       | 启用 forward-routing global filter.                          |
| spring.cloud.gateway.global-filter.load-balancer-client.enabled | `true`                                                       | 启用 load-balancer-client global filter.                     |
| spring.cloud.gateway.global-filter.netty-routing.enabled     | `true`                                                       | 启用 netty-routing global filter.                            |
| spring.cloud.gateway.global-filter.netty-write-response.enabled | `true`                                                       | 启用 netty-write-response global filter.                     |
| spring.cloud.gateway.global-filter.reactive-load-balancer-client.enabled | `true`                                                       | 启用 reactive-load-balancer-client global filter.            |
| spring.cloud.gateway.global-filter.remove-cached-body.enabled | `true`                                                       | 启用 remove-cached-body global filter.                       |
| spring.cloud.gateway.global-filter.route-to-request-url.enabled | `true`                                                       | 启用 route-to-request-url global filter.                     |
| spring.cloud.gateway.global-filter.websocket-routing.enabled | `true`                                                       | 启用 websocket-routing global filter.                        |
| spring.cloud.gateway.globalcors.add-to-simple-url-handler-mapping | `false`                                                      | 如果应将全局CORS配置添加到URL处理程序.                       |
| spring.cloud.gateway.globalcors.cors-configurations          |                                                              |                                                              |
| spring.cloud.gateway.httpclient.compression                  | `false`                                                      | 为Netty HttpClient启用压缩.                                  |
| spring.cloud.gateway.httpclient.connect-timeout              |                                                              | 连接超时（以毫秒为单位），默认值为45s.                       |
| spring.cloud.gateway.httpclient.max-header-size              |                                                              | 最大响应标头大小.                                            |
| spring.cloud.gateway.httpclient.max-initial-line-length      |                                                              | 最大初始行长.                                                |
| spring.cloud.gateway.httpclient.pool.acquire-timeout         |                                                              | 仅对于FIXED类型，等待获取的最长时间（以毫秒为单位）.         |
| spring.cloud.gateway.httpclient.pool.max-connections         |                                                              | 仅对于FIXED类型，在现有连接上开始等待挂起之前的最大连接数.   |
| spring.cloud.gateway.httpclient.pool.max-idle-time           |                                                              | 以毫秒为单位的时间，之后通道将被关闭。 如果为NULL，则没有最大空闲时间. |
| spring.cloud.gateway.httpclient.pool.max-life-time           |                                                              | 通道将关闭的持续时间。 如果为NULL，则没有最大使用寿命.       |
| spring.cloud.gateway.httpclient.pool.name                    | `proxy`                                                      | 通道池映射名称，默认为代理.                                  |
| spring.cloud.gateway.httpclient.pool.type                    |                                                              | 供HttpClient使用的池类型，默认为ELASTIC.                     |
| spring.cloud.gateway.httpclient.proxy.host                   |                                                              | Netty HttpClient代理配置的主机名.                            |
| spring.cloud.gateway.httpclient.proxy.non-proxy-hosts-pattern |                                                              | 配置的主机列表的正则表达式（Java）。 应该直接到达，绕过代理  |
| spring.cloud.gateway.httpclient.proxy.password               |                                                              | Netty HttpClient代理配置的密码.                              |
| spring.cloud.gateway.httpclient.proxy.port                   |                                                              | Netty HttpClient代理配置的端口.                              |
| spring.cloud.gateway.httpclient.proxy.type                   |                                                              | 用于Netty HttpClient代理配置的proxyType.                     |
| spring.cloud.gateway.httpclient.proxy.username               |                                                              | Netty HttpClient代理配置的用户名.                            |
| spring.cloud.gateway.httpclient.response-timeout             |                                                              | 响应超时.                                                    |
| spring.cloud.gateway.httpclient.ssl.close-notify-flush-timeout | `3000ms`                                                     | SSL close_notify刷新超时。 默认为3000毫秒.                   |
| spring.cloud.gateway.httpclient.ssl.close-notify-read-timeout | `0`                                                          | SSL close_notify读取超时。 默认为0毫秒.                      |
| spring.cloud.gateway.httpclient.ssl.default-configuration-type |                                                              | 默认的ssl配置类型。 默认为TCP.                               |
| spring.cloud.gateway.httpclient.ssl.handshake-timeout        | `10000ms`                                                    | SSL握手超时。 默认为10000毫秒                                |
| spring.cloud.gateway.httpclient.ssl.key-password             |                                                              | 密钥密码，默认与keyStorePassword相同.                        |
| spring.cloud.gateway.httpclient.ssl.key-store                |                                                              | Netty HttpClient的密钥库路径.                                |
| spring.cloud.gateway.httpclient.ssl.key-store-password       |                                                              | 密钥库密码.                                                  |
| spring.cloud.gateway.httpclient.ssl.key-store-provider       |                                                              | Netty HttpClient的密钥库提供程序，可选字段.                  |
| spring.cloud.gateway.httpclient.ssl.key-store-type           | `JKS`                                                        | Netty HttpClient的密钥库类型，默认为JKS.                     |
| spring.cloud.gateway.httpclient.ssl.trusted-x509-certificates |                                                              | 用于验证远程端点的证书的受信任证书.                          |
| spring.cloud.gateway.httpclient.ssl.use-insecure-trust-manager | `false`                                                      | 安装netty InsecureTrustManagerFactory。 这是不安全的，不适合生产. |
| spring.cloud.gateway.httpclient.websocket.max-frame-payload-length |                                                              | 最大帧有效载荷长度.                                          |
| spring.cloud.gateway.httpclient.websocket.proxy-ping         | `true`                                                       | 对下游服务的代理ping帧，默认为true.                          |
| spring.cloud.gateway.httpclient.wiretap                      | `false`                                                      | 为Netty HttpClient启用窃听调试.                              |
| spring.cloud.gateway.httpserver.wiretap                      | `false`                                                      | 为Netty HttpServer启用窃听调试.                              |
| spring.cloud.gateway.loadbalancer.use404                     | `false`                                                      |                                                              |
| spring.cloud.gateway.metrics.enabled                         | `false`                                                      | 启用指标数据收集.                                            |
| spring.cloud.gateway.metrics.prefix                          | `spring.cloud.gateway`                                       | 网关发出的所有指标的前缀.                                    |
| spring.cloud.gateway.metrics.tags                            |                                                              | 标签映射已添加到指标.                                        |
| spring.cloud.gateway.predicate.after.enabled                 | `true`                                                       | 开启 after predicate.                                        |
| spring.cloud.gateway.predicate.before.enabled                | `true`                                                       | 开启 before predicate.                                       |
| spring.cloud.gateway.predicate.between.enabled               | `true`                                                       | 开启 between predicate.                                      |
| spring.cloud.gateway.predicate.cloud-foundry-route-service.enabled | `true`                                                       | 开启 cloud-foundry-route-service predicate.                  |
| spring.cloud.gateway.predicate.cookie.enabled                | `true`                                                       | 开启 cookie predicate.                                       |
| spring.cloud.gateway.predicate.header.enabled                | `true`                                                       | 开启 header predicate.                                       |
| spring.cloud.gateway.predicate.host.enabled                  | `true`                                                       | 开启 host predicate.                                         |
| spring.cloud.gateway.predicate.method.enabled                | `true`                                                       | 开启 method predicate.                                       |
| spring.cloud.gateway.predicate.path.enabled                  | `true`                                                       | 开启 path predicate.                                         |
| spring.cloud.gateway.predicate.query.enabled                 | `true`                                                       | 开启 query predicate.                                        |
| spring.cloud.gateway.predicate.read-body.enabled             | `true`                                                       | 开启 read-body predicate.                                    |
| spring.cloud.gateway.predicate.remote-addr.enabled           | `true`                                                       | 开启 remote-addr predicate.                                  |
| spring.cloud.gateway.predicate.weight.enabled                | `true`                                                       | 开启 weight predicate.                                       |
| spring.cloud.gateway.redis-rate-limiter.burst-capacity-header | `X-RateLimit-Burst-Capacity`                                 | 返回突发容量配置的标头名称.                                  |
| spring.cloud.gateway.redis-rate-limiter.config               |                                                              |                                                              |
| spring.cloud.gateway.redis-rate-limiter.include-headers      | `true`                                                       | 是否包括包含速率限制器信息的标头，默认为true.                |
| spring.cloud.gateway.redis-rate-limiter.remaining-header     | `X-RateLimit-Remaining`                                      | 标头名称，该标头返回当前秒内剩余请求数.                      |
| spring.cloud.gateway.redis-rate-limiter.replenish-rate-header | `X-RateLimit-Replenish-Rate`                                 | 返回补充费率配置的标头名称.                                  |
| spring.cloud.gateway.redis-rate-limiter.requested-tokens-header | `X-RateLimit-Requested-Tokens`                               | 返回请求的令牌配置的标头名称.                                |
| spring.cloud.gateway.routes                                  |                                                              | 路由清单.                                                    |
| spring.cloud.gateway.set-status.original-status-header-name  |                                                              | 标头名称，其中包含代理请求的http代码.                        |
| spring.cloud.gateway.streaming-media-types                   |                                                              |                                                              |
| spring.cloud.gateway.x-forwarded.enabled                     | `true`                                                       | If the XForwardedHeadersFilter is enabled.                   |
| spring.cloud.gateway.x-forwarded.for-append                  | `true`                                                       | If appending X-Forwarded-For as a list is enabled.           |
| spring.cloud.gateway.x-forwarded.for-enabled                 | `true`                                                       | If X-Forwarded-For is enabled.                               |
| spring.cloud.gateway.x-forwarded.host-append                 | `true`                                                       | If appending X-Forwarded-Host as a list is enabled.          |
| spring.cloud.gateway.x-forwarded.host-enabled                | `true`                                                       | If X-Forwarded-Host is enabled.                              |
| spring.cloud.gateway.x-forwarded.order                       | `0`                                                          | The order of the XForwardedHeadersFilter.                    |
| spring.cloud.gateway.x-forwarded.port-append                 | `true`                                                       | If appending X-Forwarded-Port as a list is enabled.          |
| spring.cloud.gateway.x-forwarded.port-enabled                | `true`                                                       | If X-Forwarded-Port is enabled.                              |
| spring.cloud.gateway.x-forwarded.prefix-append               | `true`                                                       | If appending X-Forwarded-Prefix as a list is enabled.        |
| spring.cloud.gateway.x-forwarded.prefix-enabled              | `true`                                                       | If X-Forwarded-Prefix is enabled.                            |
| spring.cloud.gateway.x-forwarded.proto-append                | `true`                                                       | If appending X-Forwarded-Proto as a list is enabled.         |
| spring.cloud.gateway.x-forwarded.proto-enabled               | `true`                                                       | If X-Forwarded-Proto is enabled.                             |