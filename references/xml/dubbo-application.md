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

# dubbo:application

应用信息配置。对应的配置类：`com.alibaba.dubbo.config.ApplicationConfig`

| 属性 | 对应<br>URL参数 | 类型 | 是否<br>必填 | 缺省值 | 作用 | 描述 |
| --- | --- | ---- | --- | --- | --- | --- |
| name | application | 字符串 | <b>必填</b> | | 服务<br>治理 | 当前应用名称，用于注册中心计算应用间依赖关系 |
| version | version | 字符串 | 可选 | | 服务<br>治理 | 当前应用的版本 |
| owner | owner | 字符串 | 可选 | | 服务<br>治理 | 应用负责人，用于服务治理 |
| organization | organization | 字符串 | 可选 | | 服务<br>治理 | 组织名称，用于注册中心区分服务来源 |
| architecture| architecture | 字符串 | 可选 | | 服务<br>治理 | 用于服务分层对应的架构。如，intl、china。不同的架构使用不同的分层。 |
| environment | environment | 字符串 | 可选 | | 服务<br>治理 | 应用环境，如：develop、test、product，不同环境使用不同的缺省值，以及作为只用于开发测试功能的限制条件 |
| compiler | compiler | 字符串 | 可选 | javassist | 性能<br>调优 | Java字节码编译器，用于动态类的生成，可选：jdk或javassist |
| logger | logger | 字符串 | 可选 | slf4j | 性能<br>调优 | 日志输出方式，可选：slf4j、jcl、log4j、jdk |