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
# dubbo:registry

注册中心配置。对应的配置类： `com.alibaba.dubbo.config.RegistryConfig`。同时如果有多个不同的注册中心，可以声明多个 `<dubbo:registry>` 标签，并在 `<dubbo:service>` 或 `<dubbo:reference>` 的 `registry` 属性指定使用的注册中心。

| 属性 | 对应<br>URL参数 | 类型 | 是否<br>必填 | 缺省值 | 作用 | 描述 |
| --- | --- | ---- | --- | --- | --- | --- |
| id | | 字符串 | 可选 | | 配置<br>关联 | 注册中心BeanId |
| address | &lt;host:port&gt; | 字符串 | <b>必填</b> | | 服务<br>发现 | 注册中心服务器地址 |
| protocol | &lt;protocol&gt; | 字符串 | 可选 | dubbo | 服务<br>发现 | 注册中心地址协议 |
| port | &lt;port&gt; | 整数 | 可选 | 9090 | 服务<br>发现 | 注册中心缺省端口 |
| username | &lt;username&gt; | 字符串 | 可选 | | 服务<br>治理 | 登录注册中心用户名 |
| password | &lt;password&gt; | 字符串 | 可选 | | 服务<br>治理 | 登录注册中心密码 |
| transport | registry.<br>transporter | 字符串 | 可选 | netty | 性能<br>调优 | 网络传输方式 |
| timeout | registry.<br>timeout | 整数 | 可选 | 5000 | 性能<br>调优 | 注册中心请求超时时间(毫秒) |
| session | registry.<br>session | 整数 | 可选 | 60000 | 性能<br>调优 | 注册中心会话超时时间(毫秒) |
| file | registry.<br>file | 字符串 | 可选 | | 服务<br>治理 | 使用文件缓存注册中心地址列表及服务提供者列表 |
| wait | registry.<br>wait | 整数 | 可选 | 0 | 性能<br>调优 | 停止时等待通知完成时间(毫秒) |
| check | check | 布尔 | 可选 | true | 服务<br>治理 | 注册中心不存在时，是否报错 |
| register | register | 布尔 | 可选 | true | 服务<br>治理 | 是否向注册中心注册服务 |
| subscribe | subscribe | 布尔 | 可选 | true | 服务<br>治理 | 是否向注册中心订阅服务 |
| dynamic | dynamic | 布尔 | 可选 | true | 服务<br>治理 | 服务是否动态注册 |

