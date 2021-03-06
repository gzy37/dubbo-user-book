<style>
table {
  width: 100%;
  max-width: 65em;
  border: 1px solid #dedede;
  margin: 15px auto;
  border-collapse: collapse;
  empty-cells: show;
}
table th,
table td {
  height: 35px;
  border: 1px solid #dedede;
  padding: 0 10px;
}
table th {
  font-weight: bold;
  text-align: center !important;
  background: rgba(158,188,226,0.2);
  white-space: nowrap;
}
table tbody tr:nth-child(2n) {
  background: rgba(158,188,226,0.12);
}
table td:nth-child(1) {
  white-space: nowrap;
}
table td:nth-child(6) {
  white-space: nowrap;
}
table tr:hover {
  background: #efefef;
}
.table-area {
  overflow: auto;
}
</style>

<script type="text/javascript">
[].slice.call(document.querySelectorAll('table')).forEach(function(el){
    var wrapper = document.createElement('div');
    wrapper.className = 'table-area';
    el.parentNode.insertBefore(wrapper, el);
    el.parentNode.removeChild(el);
    wrapper.appendChild(el);
})
</script>
# 成熟度

## 功能成熟度

| 特性 | 成熟度 | 优点 | 问题 | 建议 | 用户 |
| -------- |---------|---------|---------|---------|---------|
|并发控制 | 已测试 | 并发控制 |   | 试用 | | 
|连接控制 | 已测试 | 连接数控制 |   | 试用 |  |
|直连提供者 | 已测试 | 点对点直连服务提供方，用于测试 |   | 测试 | 阿里巴巴 |
|分组聚合 | 已测试 | 分组聚合返回值，用于菜单聚合等服务 | 特殊场景使用 | 生产 | |
|参数验证 | 已测试 | 参数验证，JSR303验证框架集成 | 对性能有影响 | 试用 | 来往 |
|结果缓存 | 已测试 | 结果缓存，用于加速请求 |   | 试用 | |  
|泛化引用 | 稳定 | 泛化调用，无需业务接口类进行远程调用，用于测试平台，开放网关桥接等 |   | 生产 | 阿里巴巴 |
|泛化实现 | 稳定 | 泛化实现，无需业务接口类实现任意接口，用于Mock平台 |   | 生产 | 阿里巴巴 |
|回声测试 | 已测试 | 回声测试 |   | 试用 |  |
|隐式传参 | 稳定 | 附加参数 |   | 生产 | | 
|异步调用 | 已测试 | 不可靠异步调用 |   | 试用 |  |
|本地调用 | 已测试 | 本地调用 |   | 试用 |  |
|参数回调 | 已测试 | 参数回调 | 特殊场景使用 | 试用 | 注册中心 |
|事件通知 | 已测试 | 事件通知，在远程调用执行前后触发 |   | 试用 | | 
|本地存根 | 稳定 | 在客户端执行部分逻辑 |   | 生产 | 阿里巴巴 |
|本地伪装 | 稳定 | 伪造返回结果，可在失败时执行，或直接执行，用于服务降级 | 需注册中心支持 | 生产 | 阿里巴巴 |
|延迟暴露 | 稳定 | 延迟暴露服务，用于等待应用加载warmup数据，或等待spring加载完成 |   | 生产 | 阿里巴巴 |
|延迟连接 | 已测试 | 延迟建立连接，调用时建立 |   | 试用 | 注册中心
|粘滞连接 | 已测试 | 粘滞连接，总是向同一个提供方发起请求，除非此提供方挂掉，再切换到另一台 |   | 试用 | 注册中心 |
|令牌验证 | 已测试 | 令牌验证，用于服务授权 | 需注册中心支持 | 试用 |  |
|路由规则 | 已测试 | 动态决定调用关系 | 需注册中心支持 | 试用 |  |
|配置规则 | 已测试 | 动态下发配置，实现功能的开关 | 需注册中心支持 | 试用 | |  
|访问日志 | 已测试 | 访问日志，用于记录调用信息 | 本地存储，影响性能，受磁盘大小限制 | 试用 | | 
|分布式事务 | 研究中 | JTA/XA三阶段提交事务 | 不稳定 | 不可用 | &nbsp; |
 
## 策略成熟度
| 注册中心 | 成熟度 | 优点 | 问题 | 建议 | 用户|
| -------- |---------|---------|---------|---------|---------|
|Zookeeper | 稳定 | 支持基于网络的集群方式，有广泛周边开源产品，建议用dubbo-2.3.3以上版本，推荐使用 | 依赖于Zookeeper的稳定性 | 生产 |  |
|Redis | 稳定 | 支持基于客户端双写的集群方式，性能高 | 要求服务器时间同步，用于检查心跳过期脏数据 | 生产 |  |
|Multicast | 已测试 | 去中心化，不需要安装注册中心 | 依赖于网络拓普和路由，跨机房有风险 | 小规模应用或开发测试环境 |  |
|Simple | 已测试 | Dogfooding，注册中心本身也是一个标准的RPC服务 | 没有集群支持，可能单点故障 | 试用 | &nbsp; |

| 监控中心 | 成熟度 | 优点 | 问题 | 建议 | 用户|
| -------- |---------|---------|---------|---------|---------|
|Simple | 稳定 | 支持JFreeChart统计报表 | 没有集群支持，可能单点故障，但故障后不影响RPC运行 | 生产 | &nbsp; |

| 协议 | 成熟度 | 优点 | 问题 | 建议 | 用户|
| -------- |---------|---------|---------|---------|---------|
|Dubbo | 稳定 | 采用NIO复用单一长连接，并使用线程池并发处理请求，减少握手和加大并发效率，性能较好（推荐使用） | 在大文件传输时，单一连接会成为瓶颈 | 生产 | 阿里巴巴|
|Rmi | 稳定 | 可与原生RMI互操作，基于TCP协议 | 偶尔会连接失败，需重建Stub | 生产 | 阿里巴巴|
|Hessian | 稳定 | 可与原生Hessian互操作，基于HTTP协议 | 需hessian.jar支持，http短连接的开销大 | 生产 | &nbsp; |

| 传输 | 成熟度 | 优点 | 问题 | 建议 | 用户|
| -------- |---------|---------|---------|---------|---------|
|Netty | 稳定 | JBoss的NIO框架，性能较好（推荐使用） | 一次请求派发两种事件，需屏蔽无用事件 | 生产 | 阿里巴巴|
|Mina | 稳定 | 老牌NIO框架，稳定 | 待发送消息队列派发不及时，大压力下，会出现FullGC | 生产 | 阿里巴巴|
|Grizzly | 已测试 | Sun的NIO框架，应用于GlassFish服务器中 | 线程池不可扩展，Filter不能拦截下一Filter | 试用 | &nbsp; |

| 序列化 | 成熟度 | 优点 | 问题 | 建议 | 用户|
| -------- |---------|---------|---------|---------|---------|
|Hessian | 稳定 | 性能较好，多语言支持推荐使用 | Hessian的各版本兼容性不好，可能和应用使用的Hessian冲突，Dubbo内嵌了hessian3.2.1的源码 | 生产 | 阿里巴巴|
|Dubbo | 已测试 | 通过不传送POJO的类元信息，在大量POJO传输时，性能较好 | 当参数对象增加字段时，需外部文件声明 | 试用 |  |
|Json | 已测试 | 纯文本，可跨语言解析，缺省采用FastJson解析 | 性能较差 | 试用 |  |
|Java | 稳定 | Java原生支持 | 性能较差 | 生产 | &nbsp; |

| 代理 | 成熟度 | 优点 | 问题 | 建议 | 用户|
| -------- |---------|---------|---------|---------|---------|
|Javassist | 稳定 | 通过字节码生成代替反射，性能比较好（推荐使用） | 依赖于javassist.jar包，占用JVM的Perm内存，Perm可能要设大一些：java -XX:PermSize=128m | 生产 | 阿里巴巴|
|Jdk | 稳定 | JDK原生支持 | 性能较差 | 生产 | &nbsp; |

| 集群 | 成熟度 | 优点 | 问题 | 建议 | 用户|
| -------- |---------|---------|---------|---------|---------|
|Failover | 稳定 | 失败自动切换，出现失败重试其它服务器，通常用于读操作（推荐使用） | 重试会带来更长延迟 | 生产 | 阿里巴巴|
|Failfast | 稳定 | 快速失败，只发起一次调用，失败立即报错,通常用于非幂等性的写操作 | 如果有机器正在重启，可能会出现调用失败 | 生产 | 阿里巴巴|
|Failsafe | 稳定 | 失败安全，出现异常时，直接忽略，通常用于写入审计日志等操作 | 调用信息丢失 | 生产 | Monitor|
|Failback | 已测试 | 失败自动恢复，后台记录失败请求，定时重发，通常用于消息通知操作 | 不可靠，重启丢失 | 生产 | 注册中心|
|Forking | 已测试 | 并行调用多个服务器，只要一个成功即返回，通常用于实时性要求较高的读操作 | 需要浪费更多服务资源 | 生产 |  |
|Broadcast | 已测试 | 广播调用所有提供者，逐个调用，任意一台报错则报错，通常用于更新提供方本地状态 | 速度慢，任意一台报错则报错 | 生产 | &nbsp; | 

| 负载均衡 | 成熟度 | 优点 | 问题 | 建议 | 用户|
| -------- |---------|---------|---------|---------|---------|
|Random | 稳定 | 随机，按权重设置随机概率（推荐使用） | 在一个截面上碰撞的概率高，重试时，可能出现瞬间压力不均 | 生产 | 阿里巴巴|
|RoundRobin | 稳定 | 轮循，按公约后的权重设置轮循比率 | 存在慢的机器累积请求问题，极端情况可能产生雪崩 | 生产 |  |
|LeastActive | 稳定 | 最少活跃调用数，相同活跃数的随机，活跃数指调用前后计数差，使慢的机器收到更少请求 | 不支持权重，在容量规划时，不能通过权重把压力导向一台机器压测容量 | 生产 | &nbsp; |
|ConsistentHash | 稳定 | 一致性Hash，相同参数的请求总是发到同一提供者，当某一台提供者挂时，原本发往该提供者的请求，基于虚拟节点，平摊到其它提供者，不会引起剧烈变动 | 压力分摊不均 | 生产 | &nbsp; |

| 路由规则 | 成熟度 | 优点 | 问题 | 建议 | 用户|
| -------- |---------|---------|---------|---------|---------|
|条件路由 | 稳定 | 基于条件表达式的路由规则，功能简单易用 | 有些复杂多分支条件情况，规则很难描述 | 生产 | 阿里巴巴|
|脚本路由 | 已测试 | 基于脚本引擎的路由规则，功能强大 | 没有运行沙箱，脚本能力过于强大，可能成为后门 | 试用 | &nbsp; |


| 容器 | 成熟度 | 优点 | 问题 | 建议 | 用户|
| -------- |---------|---------|---------|---------|---------|
|Spring | 稳定 | 自动加载META-INF/spring目录下的所有Spring配置 |   | 生产 | 阿里巴巴|
|Jetty | 稳定 | 启动一个内嵌Jetty，用于汇报状态 | 大量访问页面时，会影响服务器的线程和内存 | 生产 | 阿里巴巴|
|Log4j | 稳定 | 自动配置log4j的配置，在多进程启动时，自动给日志文件按进程分目录 | 用户不能控制log4j的配置，不灵活 | 生产 | 阿里巴巴|