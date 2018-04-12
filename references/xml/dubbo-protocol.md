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
# dubbo:protocol

服务提供者协议配置。对应的配置类： `com.alibaba.dubbo.config.ProtocolConfig`。同时，如果需要支持多协议，可以声明多个 `<dubbo:protocol>` 标签，并在 `<dubbo:service>` 中通过 `protocol` 属性指定使用的协议。

| 属性 | 对应<br>URL参数 | 类型 | 是否<br>必填 | 缺省值 | 作用 | 描述 |
| --- | --- | ---- | --- | --- | --- | --- |
| id | | 字符串 | 可选 | dubbo | 配置<br>关联 | 协议BeanId |
| name | &lt;protocol&gt; | 字符串 | <b>必填</b> | dubbo | 性能<br>调优 | 协议名称 |
| port | &lt;port&gt; | 整数 | 可选 | | 服务<br>发现 | 服务端口 |
| host | &lt;host&gt; | 字符串 | 可选 | 自动查找本机IP | 服务<br>发现 | 服务主机名|
| threadpool | threadpool | 字符串 | 可选 | fixed | 性能<br>调优 | 线程池类型 |
| threads | threads | 整数 | 可选 | 100 | 性能<br>调优 | 服务线程池大小 |
| iothreads | threads | 整数 | 可选 | cpu个数+1 | 性能<br>调优 | io线程池大小 |
| accepts | accepts | 整数 | 可选 | 0 | 性能<br>调优 | 服务提供方最大接受连接数 |
| payload | payload | 整数 | 可选 | 88388608 | 性能<br>调优 | 请求及响应数据包大小，单位：字节 |
| codec | codec | 字符串 | 可选 | dubbo | 性能<br>调优 | 协议编码方式 |
| serialization | serialization | 字符串 | 可选 |  | 性能<br>调优 | 协议序列化方式 |
| accesslog | accesslog | 字符串<br>布尔 | 可选 | | 服务<br>治理 | true表示将向logger中输出访问日志，字符串表示把访问日志输出到指定文件 |
| path | &lt;path&gt; | 字符串 | 可选 | | 服务<br>发现 | 提供者上下文路径，为服务path的前缀 |
| transporter | transporter | 字符串 | 可选 |  | 性能<br>调优 | 协议的服务端和客户端实现类型 |
| server | server | 字符串 | 可选 |  | 性能<br>调优 | 协议的服务器端实现类型 |
| client | client | 字符串 | 可选 |  | 性能<br>调优 | 协议的客户端实现类型 |
| dispatcher | dispatcher | 字符串 | 可选 | dubbo协议缺省为all | 性能<br>调优 | 协议的消息派发方式 |
| queues | queues | 整数 | 可选 | 0 | 性能<br>调优 | 线程池队列大小 |
| charset | charset | 字符串 | 可选 | UTF-8 | 性能<br>调优 | 序列化编码 |
| buffer | buffer | 整数 | 可选 | 8192 | 性能<br>调优 | 网络读写缓冲区大小 |
| heartbeat | heartbeat | 整数 | 可选 | 0 | 性能<br>调优 | 心跳间隔 |
| telnet | telnet | 字符串 | 可选 | | 服务<br>治理 | 所支持的telnet命令，多个命令用逗号分隔 |
| register | register | 布尔 | 可选 | true | 服务<br>治理 | 该协议的服务是否注册到注册中心 |
| contextpath | contextpath | 字符串 | 可选 | 缺省为空串 | 服务<br>治理 | &nbsp;|

