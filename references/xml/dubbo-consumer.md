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
white-space: nowrap;<
style>
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
# dubbo:consumer

服务消费者缺省值配置。配置类： `com.alibaba.dubbo.config.ConsumerConfig` 。同时该标签为 `<dubbo:reference>` 标签的缺省值设置。

| 属性 | 对应<br>URL参数 | 类型 | 是否<br>必填 | 缺省值 | 作用 | 描述 |
| --- | --- | ---- | --- | --- | --- | --- |
| timeout | timeout | 整数 | 可选 | 1000 | 性能<br>调优 | 超时时间(毫秒) |
| retries | retries | 整数 | 可选 | 2 | 性能<br>调优 | 重试次数(不包括第一次调用)，0表示不需要重试 |
| loadbalance | loadbalance | 字符串 | 可选 | random | 性能<br>调优 | 负载均衡策略，可选：random、roundrobin、leastactive |
| async | async | 布尔 | 可选 | false | 性能<br>调优 | 是否缺省异步执行 |
| connections | connections | 整数 | 可选 | 100 | 性能<br>调优 | 每个服务对每个提供者的最大连接数，rmi、http、hessian等短连接协议支持此配置，dubbo协议长连接不支持此配置 |
| generic | generic | 布尔 | 可选 | false | 服务<br>治理 | 是否缺省泛化接口，如果为泛化接口，将返回GenericService |
| check | check | 布尔 | 可选 | true | 服务<br>治理 | 启动时检查提供者是否存在，true报错，false忽略 |
| proxy | proxy | 字符串 | 可选 | javassist | 性能<br>调优 | 生成动态代理方式，可选：jdk/javassist |
| owner | owner | 字符串 | 可选 | | 服务<br>治理 | 调用服务负责人，用于服务治理 |
| actives | actives | 整数 | 可选 | 0 | 性能<br>调优 | 每服务消费者每服务每方法最大并发调用数 |
| cluster | cluster | 字符串 | 可选 | failover | 性能<br>调优 | 集群方式，可选：failover、failfast、failsafe、failback、forking |
| filter | filter | 字符串 | 可选 | | 性能<br>调优 | 服务消费方远程调用过程拦截器名称，多个名称用逗号分隔 |
| listener | listener | 字符串 | 可选 | | 性能<br>调优 | 服务消费方引用服务监听器名称，多个名称用逗号分隔 |
| registry | | 字符串 | 可选 | 向所有registry注册 | 配置<br>关联 | 向指定注册中心注册，在多个注册中心时使用，值为&lt;dubbo:registry&gt;的id属性，多个注册中心ID用逗号分隔，如果不想将该服务注册到任何registry，可将值设为N/A |
| layer | layer | 字符串 | 可选 | | 服务<br>治理 | 服务调用者所在的分层。如：biz、dao。 |
| init | init | 布尔 | 可选 | false | 性能<br>调优 | 是否在afterPropertiesSet初始化引用，否则等到有人注入或引用该实例时再初始化。 |
| cache | cache | 字符串<br>布尔 | 可选 | | 服务<br>治理 | 以调用参数为key，缓存返回结果，可选：lru、 threadlocal、jcache等 |
| validation | validation | 布尔 | 可选 | | 服务<br>治理 | 是否启用JSR303标准注解验证，如果启用，将对方法参数上的注解进行校验 |