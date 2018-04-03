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
# dubbo:method

方法级配置。对应的配置类： `com.alibaba.dubbo.config.MethodConfig`。同时该标签为 `<dubbo:service>` 或 `<dubbo:reference>` 的子标签，用于控制到方法级。

| 属性 | 对应<br>URL参数 | 类型 | 是否<br>必填 | 缺省值 | 作用 | 描述 |
| --- | --- | ---- | --- | --- | --- | --- |
| name | | 字符串 | <b>必填</b> | | 标识 | 方法名 |
| timeout | timeout | 整数 | 可选 | | 性能<br>调优 | 超时时间(毫秒) |
| retries | retries | 整数 | 可选 | | 性能<br>调优 | 重试次数(不包括第一次调用)，0表示不需要重试 |
| loadbalance | loadbalance | 字符串 | 可选 | | 性能<br>调优 | 负载均衡策略，可选：random、roundrobin、leastactive |
| async | async | 布尔 | 可选 | | 性能<br>调优 | 是否异步执行 |
| sent | sent | 布尔 | 可选 | true | 性能<br>调优 | 异步调用时，true表示网络已发出数据 |
| actives | actives | 整数 | 可选 | 0 | 性能<br>调优 | 每服务消费者最大并发调用限制 |
| executes | executes | 整数 | 可选 | 0 | 性能<br>调优 | 每服务每方法最大使用线程数限制，此属性只在&lt;dubbo:method&gt;作为&lt;dubbo:service&gt;子标签时有效 |
| deprecated | deprecated | 布尔 | 可选 | false | 服务<br>治理 | 服务方法是否过时，此属性只在&lt;dubbo:method&gt;作为&lt;dubbo:service&gt;子标签时有效 |
| sticky | sticky | 布尔 | 可选 | false | 服务<br>治理 | true表示该接口上所有方法使用同一个provider。如果需要更复杂的规则，请使用路由 |
| return | return | 布尔 | 可选 | true | 性能<br>调优 | 方法调用是否需要返回值,async设置为true时才生效，如果设置为true，则返回future，或回调onreturn等方法，如果设置为false，则请求发送成功后直接返回Null |
| oninvoke | attribute属性，不在URL中体现 | 字符串 | 可选 | | 性能<br>调优 | 方法执行前拦截 |
| onreturn | attribute属性，不在URL中体现 | 字符串 | 可选 | | 性能<br>调优 | 方法执行返回后拦截 |
| onthrow | attribute属性，不在URL中体现 | 字符串 | 可选 | | 性能<br>调优 | 方法执行有异常拦截 |
| cache | cache | 字符串<br>布尔 | 可选 | | 服务<br>治理 | 以调用参数为key，缓存返回结果，可选：lru、 threadlocal、jcache等 |
| validation | validation | 布尔 | 可选 | | 服务<br>治理 | 是否启用JSR303标准注解验证，如果启用，将对方法参数上的注解进行校验 |

比如:

```xml
<dubbo:reference interface="com.xxx.XxxService">
<dubbo:method name="findXxx" timeout="3000" retries="2" />
</dubbo:reference>
```

