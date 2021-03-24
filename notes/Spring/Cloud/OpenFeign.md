| Name                                         | Default                                         | Description                                                  |
| :------------------------------------------- | :---------------------------------------------- | :----------------------------------------------------------- |
| feign.autoconfiguration.jackson.enabled      | `false`                                         | 如果为true，则将提供PageJacksonModule和SortJacksonModule bean用于Jackson页面解码. |
| feign.circuitbreaker.enabled                 | `false`                                         | 如果为true，则将使用Spring Cloud CircuitBreaker断路器包装OpenFeign客户端. |
| feign.client.config                          |                                                 |                                                              |
| feign.client.decode-slash                    | `true`                                          | 伪客户端默认情况下不对斜杠“ /”字符进行编码。 要更改此行为，请将“ decodeSlash”设置为“ false”. |
| feign.client.default-config                  | `default`                                       |                                                              |
| feign.client.default-to-properties           | `true`                                          |                                                              |
| feign.compression.request.enabled            | `false`                                         | 允许压缩Feign发送的请求.                                     |
| feign.compression.request.mime-types         | `[text/xml, application/xml, application/json]` | 支持的mime类型列表.                                          |
| feign.compression.request.min-request-size   | `2048`                                          | 最小阈值内容大小.                                            |
| feign.compression.response.enabled           | `false`                                         | 可以压缩来自Feign的响应.                                     |
| feign.compression.response.useGzipDecoder    | `false`                                         | 启用要使用的默认gzip解码器.                                  |
| feign.encoder.charset-from-content-type      | `false`                                         | 指示字符集是否应从{@code Content-Type}标头派生.              |
| feign.httpclient.connection-timeout          | `2000`                                          |                                                              |
| feign.httpclient.connection-timer-repeat     | `3000`                                          |                                                              |
| feign.httpclient.disable-ssl-validation      | `false`                                         |                                                              |
| feign.httpclient.enabled                     | `true`                                          | 允许通过Feign使用Apache HTTP客户端.                          |
| feign.httpclient.follow-redirects            | `true`                                          |                                                              |
| feign.httpclient.hc5.enabled                 | `false`                                         | 允许通过Feign使用Apache HTTP Client 5.                       |
| feign.httpclient.hc5.pool-concurrency-policy |                                                 | 池并发策略.                                                  |
| feign.httpclient.hc5.pool-reuse-policy       |                                                 | 池连接重用策略.                                              |
| feign.httpclient.hc5.socket-timeout          | `5`                                             | 套接字超时的默认值.                                          |
| feign.httpclient.hc5.socket-timeout-unit     |                                                 | 套接字超时单位的默认值.                                      |
| feign.httpclient.max-connections             | `200`                                           |                                                              |
| feign.httpclient.max-connections-per-route   | `50`                                            |                                                              |
| feign.httpclient.time-to-live                | `900`                                           |                                                              |
| feign.httpclient.time-to-live-unit           |                                                 |                                                              |
| feign.metrics.enabled                        | `true`                                          | 启用伪装的指标功能.                                          |
| feign.okhttp.enabled                         | `false`                                         | 允许通过Feign使用OK HTTP客户端.                              |