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
# dubbo:argument

方法参数配置。对应的配置类： `com.alibaba.dubbo.config.ArgumentConfig`。该标签为 `<dubbo:method>` 的子标签，用于方法参数的特征描述，比如： 
 
```xml
<dubbo:method name="findXxx" timeout="3000" retries="2">
    <dubbo:argument index="0" callback="true" />
</dubbo:method>
```
| 属性 | 对应<br>URL参数 | 类型 | 是否必填 | 缺省值 | 作用 | 描述 |
| --- | --- | ---- | --- | --- | --- | --- | --- |
| index | | 整数 | <b>与type二选一</b> | | 标识 | 方法名 |
| type | | 字符串 | <b>与index二选一</b> | | 标识 | 通过参数类型查找参数的index |
| callback | | 布尔 | 可选 | | 服务<br>治理 | 参数是否为callback接口，如为callback，服务提供方将生成反向代理，可以从服务提供方反向调用消费方，通常用于事件推送. |
