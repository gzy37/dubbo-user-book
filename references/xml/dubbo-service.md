<style>
table {
width: 100%;
max-width: 65em;
border: 1px solid #dedede;
margin: 15px auto;
border-collapse: collapse;
empty-cells: show;
}
table td {
height: 35px;
border: 1px solid #dedede;
padding: 0px;
}
table th,
table td {
height: 35px;
border: 1px solid #dedede;
padding: 0px;
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
# dubbo:service

服务提供者暴露服务配置。对应的配置类：`com.alibaba.dubbo.config.ServiceConfig`

| 属性 | 对应URL参数 | 类型 | 是否<br>必填 | 缺省值 | 作用 | 描述 |
| --- | --- | ---- | --- | --- | --- | --- |
| interface | | 类 | <b>必填</b> | | 服务<br>发现 | 服务接口名 |
| ref | | 对象 | <b>必填</b> | | 服务<br>发现 | 服务对象实现引用 |
| version | version | 字符串 | 可选 | 0.0.0 | 服务<br>发现 | 服务版本，建议使用两位数字版本 |
| group | group | 字符串 | 可选 | | 服务<br>发现 | 服务分组，当一个接口有多个实现，可以用分组区分 |
| path | &lt;path&gt; | 字符串 | 可选 | 接口名 | 服务<br>发现 | 服务路径 |
| delay | delay | 整数 | 可选 | 0 | 性能<br>调优 | 服务延迟注册时间(毫秒) ，设为-1表示Spring容器初始化完成暴露服务 |
| timeout | timeout | 整数 | 可选 | 1000 | 性能<br>调优 | 服务调用超时时间(毫秒) |
| retries | retries | 整数 | 可选 | 2 | 性能<br>调优 | 服务调用重试次数(不含第一次调用，不需要重试设为0) |
| connections | connections | 整数 | 可选 | 100 | 性能<br>调优 | 最大连接数 |
| loadbalance | loadbalance | 字符串 | 可选 | random | 性能<br>调优 | 负载均衡策略，可选值：random、roundrobin、leastactive，分别表示：随机，轮循，最少活跃调用 |
| async | async | 布尔 | 可选 | false | 性能<br>调优 | 是否异步执行 |
| stub | stub | 类<br>布尔 | 可选 | false | 服务<br>治理 | 设为true，表示使用缺省代理类名，即：接口名 + Local后缀，服务接口客户端本地代理类名，用于在客户端执行本地逻辑，如本地缓存等|
| mock | mock | 类<br>布尔 | 可选 | false | 服务<br>治理 | 设为true，表示使用缺省Mock类名，即：接口名 + Mock后缀，服务接口调用失败Mock实现类，该Mock类必须有一个无参构造函数，与Local的区别在于，Local总是被执行，而Mock只在出现非业务异常(比如超时，网络异常等)时执行，Local在远程调用之前执行，Mock在远程调用后执行。 |
| token | token | 字符串<br>布尔 | 可选 | false | 服务<br>治理 | 令牌验证，为空表示不开启，如果为true，表示随机生成动态令牌，否则使用静态令牌，令牌的作用是防止消费者绕过注册中心直接访问，保证注册中心的授权功能有效，如果使用点对点调用，需关闭令牌功能 |
| registry | | 字符串 | 可选 | 缺省向所有registry注册 | 配置<br>关联 | 向指定注册中心注册，在多个注册中心时使用，值为&lt;dubbo:registry&gt;的id属性，多个注册中心ID用逗号分隔，如果不想将该服务注册到任何registry，可将值设为N/A |
| provider | | 字符串 | 可选 | 缺使用第一个provider配置 | 配置<br>关联 | 指定provider，值为&lt;dubbo:provider&gt;的id属性 |
| deprecated | deprecated | 布尔 | 可选 | false | 服务<br>治理 | 是否过时，设为true消费方引用时将打印服务过时警告error日志 |
| dynamic | dynamic | 布尔 | 可选 | true | 服务<br>治理 | 是否动态注册，设为false后需人工启用/禁用服务。 |
| accesslog | accesslog | 字符串<br>布尔 | 可选 | false | 服务<br>治理 | 设为true，将向logger中输出访问日志，也可填写访问日志文件路径，直接把访问日志输出到指定文件 |
| owner | owner | 字符串 | 可选 | | 服务<br>治理 | 服务负责人 |
| document | document | 字符串 | 可选 | | 服务<br>治理 | 服务文档URL |
| weight | weight | 整数 | 可选 | | 性能<br>调优 | 服务权重 |
| executes | executes | 整数 | 可选 | 0 | 性能<br>调优 | 服务提供者最大可并行执行请求数 |
| actives | actives | 整数 | 可选 | 0 | 性能<br>调优 | 服务消费者最大并发调用数 |
| proxy | proxy | 字符串 | 可选 | javassist | 性能<br>调优 | 动态代理方式，可选：jdk、javassist |
| cluster | cluster | 字符串 | 可选 | failover | 性能<br>调优 | 集群方式，可选：failover、failfast、failsafe、failback、forking |
| filter | service.filter | 字符串 | 可选 | default | 性能<br>调优 | 服务提供方远程调用过程拦截器名称，多个名称用逗号分隔 |
| listener | exporter.listener | 字符串 | 可选 | default | 性能<br>调优 | 服务提供方导出服务监听器名称，多个名称用逗号分隔 |
| protocol | | 字符串 | 可选 | | 配置<br>关联 | 暴露服务的协议，在多协议时使用，值为&lt;dubbo:protocol&gt;的id属性，多个协议ID用逗号分隔 |
| layer | layer | 字符串 | 可选 | | 服务<br>治理 | 服务提供者所在的分层。如：biz、dao |
| register | register | 布尔 | 可选 | true | 服务<br>治理 | 该协议的服务是否注册到注册中心 |

