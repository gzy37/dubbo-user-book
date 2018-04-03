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
# dubbo:reference

服务消费者引用服务配置。对应的配置类： `com.alibaba.dubbo.config.ReferenceConfig`

| 属性 | 对应<br>URL参数 | 类型 | 是否<br>必填 | 缺省值 | 作用 | 描述 |
| --- | --- | ---- | --- | --- | --- | --- |
| id | | 字符串 | <b>必填</b> | | 配置<br>关联 | 服务引用BeanId |
| interface | | 类 | <b>必填</b> | | 服务<br>发现 | 服务接口名 |
| version | version | 字符串 | 可选 | | 服务<br>发现 | 服务版本，与服务提供者的版本一致 |
| group | group | 字符串 | 可选 | | 服务<br>发现 | 服务分组，必须和服务提供方一致 |
| url | url | 字符串 | 可选 | | 服务<br>治理 | 点对点直连服务提供者地址，将绕过注册中心 |
| stub | stub | 类<br>布尔 | 可选 | | 服务<br>治理 | 服务接口客户端本地代理类名 |
| mock | mock | 类<br>布尔 | 可选 | | 服务<br>治理 | 服务接口调用失败Mock实现类名|
| timeout | timeout | 整数 | 可选 | 使用consumer的timeout | 性能<br>调优 | 服务方法调用超时时间(毫秒) |
| retries | retries | 整数 | 可选 | 使用consumer的retries | 性能<br>调优 | 远程服务调用重试次数，不包括第一次调用，不需要重试请设为0 |
| connections | connections | 整数 | 可选 | 使用consumer的connections | 性能<br>调优 | 对每个提供者的最大连接数，rmi、http、hessian等短连接协议表示限制连接数，dubbo等长连接协表示建立的长连接个数 |
| loadbalance | loadbalance | 字符串 | 可选 | 使用consumer的loadbalance | 性能<br>调优 | 负载均衡策略，可选值：random、roundrobin、leastactive，分别表示：随机，轮循，最少活跃调用 |
| async | async | 布尔 | 可选 | 使用consumer的async | 性能<br>调优 | 是否异步执行，不可靠异步，只是忽略返回值，不阻塞执行线程 |
| generic | generic | 布尔 | 可选 | 使用consumer的generic | 服务<br>治理 | 是否缺省泛化接口，如果为泛化接口，将返回 |
| check | check | 布尔 | 可选 | 使用consumer的check | 服务<br>治理 | 启动时检查提供者是否存在，true报错，false忽略 |
| cache | cache | 字符串<br>布尔 | 可选 | | 服务<br>治理 | 以调用参数为key，缓存返回结果，可选：lru、 threadlocal、 jcache等 |
| validation | validation | 布尔 | 可选 | | 服务<br>治理 | 是否启用JSR303标准注解验证，如果启用，将对方法参数上的注解进行校验 |
| proxy | proxy | 布尔 | 可选 | javassist | 性能<br>调优 | 选择动态代理实现策略，可选：javassist、 jdk |
| client | client | 字符串 | 可选 | | 性能<br>调优 | 客户端传输类型设置，如Dubbo协议的netty或mina。 |
| registry | | 字符串 | 可选 | 将从所有注册中心获服务列表后合并结果 | 配置<br>关联 | 从指定注册中心注册获取服务列表，在多个注册中心时使用，值为&lt;dubbo:registry&gt;的id属性，多个注册中心ID用逗号分隔 |
| owner | owner | 字符串 | 可选 | | 服务<br>治理 | 调用服务负责人，用于服务治理，请填写负责人公司邮箱前缀 |
| actives | actives | 整数 | 可选 | 0 | 性能<br>调优 | 每服务消费者每服务每方法最大并发调用数 |
| cluster | cluster | 字符串 | 可选 | failover | 性能<br>调优 | 集群方式，可选：failover、failfast、failsafe、failback、forking |
| layer | layer | 字符串 | 可选 | | 服务<br>治理 | 服务调用者所在的分层。如：biz、dao。 |
| init | init | 布尔 | 可选 | false | 性能<br>调优 | 是否在afterPropertiesSet()时饥饿初始化引用，否则等到有人注入或引用该实例时再初始化。 |
| protocol | protocol | 字符串 | 可选 | | 服务<br>治理 | 只调用指定协议的服务提供方，其它协议忽略。 |
| filter | reference.<br>filter | 字符串 | 可选 | default | 性能<br>调优 | 服务消费方远程调用过程拦截器名称，多个名称用逗号分隔 |
| listener | invoker.<br>listener | 字符串 | 可选 | default | 性能<br>调优 | 服务消费方引用服务监听器名称，多个名称用逗号分隔 |

