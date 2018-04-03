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
# dubbo:monitor

监控中心配置。对应的配置类： `com.alibaba.dubbo.config.MonitorConfig`

| 属性 | 对应<br>URL参数 | 类型 | 是否<br>必填 | 缺省值 | 作用 | 描述 |
| --- | --- | ---- | --- | --- | --- | --- |
| protocol | protocol | 字符串 | 可选 | dubbo | 服务治理 | 监控中心协议，如果为"registry"，表示从注册中心发现监控中心地址，否则直连监控中心。 |
| address | &lt;url&gt; | 字符串 | 可选 | N/A | 服务治理 | 直连监控中心服务器地址 |
