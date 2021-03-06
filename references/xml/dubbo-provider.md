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
table td:nth-child(3) {
white-space: nowrap;
}
table td:nth-child(4) {
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
# dubbo:provider

服务提供者缺省值配置。对应的配置类： `com.alibaba.dubbo.config.ProviderConfig`。同时该标签为 `<dubbo:service>` 和 `<dubbo:protocol>` 标签的缺省值设置。

| 属性 | 对应<br>URL参数 | 类型 | 是否<br>必填 | 缺省值 | 作用 | 描述 |
| --- | --- | ---- | --- | --- | --- | --- |
| id | | 字符串 | 可选 | dubbo | 配置<br>关联 | 协议BeanId |
| protocol | &lt;protocol&gt; | 字符串 | 可选 | dubbo | 性能<br>调优 | 协议名称 |
| host | &lt;host&gt; | 字符串 | 可选 | 自动查找本机IP | 服务<br>发现 | 服务主机名，多网卡选择或指定VIP及域名时使用，为空则自动查找本机IP |
| threads | threads | 整数 | 可选 | 100 | 性能<br>调优 | 服务线程池大小(固定大小) |
| payload | payload | 整数 | 可选 | 88388608 | 性能<br>调优 | 请求及响应数据包大小，单位：字节 |
| path | &lt;path&gt; | 字符串 | 可选 | | 服务<br>发现 | 提供者上下文路径，为服务path的前缀 |
| server | server | 字符串 | 可选 | dubbo协议缺省为netty，http协议缺省为servlet | 性能<br>调优 | 协议的服务器端实现类型 |
| client | client | 字符串 | 可选 | dubbo协议缺省为netty | 性能<br>调优 | 协议的客户端实现类型 |
| codec | codec | 字符串 | 可选 | dubbo | 性能<br>调优 | 协议编码方式 |
| serialization | serialization | 字符串 | 可选 | dubbo协议缺省为hessian2，rmi协议缺省为java，http协议缺省为json | 性能<br>调优 | 协议序列化方式，当协议支持多种序列化方式时使用 |
| default | | 布尔 | 可选 | false | 配置<br>关联 | 是否为缺省协议，用于多协议 |
| filter | filter | 字符串 | 可选 | | 性能<br>调优 | 服务提供方远程调用过程拦截器名称，多个名称用逗号分隔 |
| listener | listener | 字符串 | 可选 | | 性能<br>调优 | 服务提供方导出服务监听器名称，多个名称用逗号分隔 |
| threadpool | threadpool | 字符串 | 可选 | fixed | 性能<br>调优 | 线程池类型，可选：fixed、cached |
| accepts | accepts | 整数 | 可选 | 0 | 性能<br>调优 | 服务提供者最大接受连接数 |
| version | version | 字符串 | 可选 | 0.0.0 | 服务<br>发现 | 服务版本 |
| group | group | 字符串 | 可选 | | 服务<br>发现 | 服务分组，当一个接口有多个实现，可以用分组区分 |
| delay | delay | 整数 | 可选 | 0 | 性能<br>调优 | 延迟注册服务时间(毫秒)，-1表示Spring容器初始化完成暴露服务 |
| timeout | timeout | 整数 | 可选 | 1000 | 性能<br>调优 | 超时时间(毫秒) |
| retries | retries | 整数 | 可选 | 2 | 性能<br>调优 | 重试次数(不包括第一次调用)，0表示不需要重试 |
| connections | connections | 整数 | 可选 | 0 | 性能<br>调优 | 对每个提供者的最大连接数 |
| loadbalance | loadbalance | 字符串 | 可选 | random | 性能<br>调优 | 负载均衡策略，可选：random、roundrobin、leastactive |
| async | async | 布尔 | 可选 | false | 性能<br>调优 | 是否异步执行 |
| stub | stub | 布尔 | 可选 | false | 服务<br>治理 | true表示使用缺省代理类名 |
| mock | mock | 布尔 | 可选 | false | 服务<br>治理 | true表示使用缺省Mock类名 |
| token | token | 布尔 | 可选 | false | 服务<br>治理 | 令牌验证，false表示不开启，true表示随机生成动态令牌 |
| registry | registry | 字符串 | 可选 | 缺省向所有registry注册 | 配置<br>关联 | 向指定注册中心注册，在多个注册中心时使用，值为registry的id属性，多个注册中心ID用逗号分隔，如果不想将该服务注册到任何registry，可将值设为N/A |
| dynamic | dynamic | 布尔 | 可选 | true | 服务<br>治理 | 是否动态注册，false表示需人工启用/禁用服务。 |
| accesslog | accesslog | 字符串<br>布尔 | 可选 | false | 服务<br>治理 | true表示向logger中输出访问日志，字符串表示把访问日志输出到指定文件 |
| owner | owner | 字符串 | 可选 | | 服务<br>治理 | 服务负责人，用于服务治理 |
| document | document | 字符串 | 可选 | | 服务<br>治理 | 服务文档URL |
| weight | weight | 整数 | 可选 | | 性能<br>调优 | 服务权重 |
| executes | executes | 整数 | 可选 | 0 | 性能<br>调优 | 服务提供者每服务每方法最大可并行执行请求数 |
| actives | actives | 整数 | 可选 | 0 | 性能<br>调优 | 每服务消费者每服务每方法最大并发调用数 |
| proxy | proxy | 字符串 | 可选 | javassist | 性能<br>调优 | 生成动态代理方式，可选：jdk、javassist |
| cluster | cluster | 字符串 | 可选 | failover | 性能<br>调优 | 集群方式，可选：failover、failfast、failsafe、failback、forking |
| deprecated | deprecated | 布尔 | 可选 | false | 服务<br>治理 | 服务是否过时，true表示消费方引用时将打印服务过时警告日志 |
| queues | queues | 整数 | 可选 | 0 | 性能<br>调优 | 线程池队列大小，建议不要设置，当线程池满时应立即失败，重试其它服务提供机器。 |
| charset | charset | 字符串 | 可选 | UTF-8 | 性能<br>调优 | 序列化编码 |
| buffer | buffer | 整数 | 可选 | 8192 | 性能<br>调优 | 网络读写缓冲区大小 |
| iothreads | iothreads | 整数 | 可选 | CPU + 1 | 性能<br>调优 | IO线程池，接收网络读写中断，以及序列化和反序列化，不处理业务|
| telnet | telnet | 字符串 | 可选 | | 服务<br>治理 | 所支持的telnet命令，多个命令用逗号分隔 |
| contextpath | contextpath | 字符串 | 可选 | 缺省为空串 | 服务<br>治理 | |
| layer | layer | 字符串 | 可选 | | 服务<br>治理 | 服务提供者所在的分层。 |