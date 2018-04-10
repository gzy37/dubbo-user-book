# 上下文信息

上下文中存放的是当前调用过程中所需的环境信息，所有配置信息都将转换为 URL 的参数。

RpcContext 是一个 ThreadLocal 的临时状态记录器，当接收到 RPC 请求或发起 RPC 请求时，RpcContext 的状态都会变化。比如：A调B，B再调C，则B机器上，B调C之前，RpcContext 记录的是A调B的信息，B调C之后，RpcContext 记录的是B调C的信息。

## 服务消费方

```java
// 远程调用
xxxService.xxx();
// 本端是否为消费端，这里会返回true
boolean isConsumerSide = RpcContext.getContext().isConsumerSide();
// 获取最后一次调用的提供方IP地址
String serverIP = RpcContext.getContext().getRemoteHost();
// 获取当前服务配置信息，所有配置信息都将转换为URL的参数
String app = RpcContext.getContext().getUrl().getParameter("application");
// 注意：每发起RPC调用，上下文状态会变化
yyyService.yyy();
```

## 服务提供方

```java
public class XxxServiceImpl implements XxxService { 
    public void xxx() {
        // 本端是否为提供端，这里会返回true
        boolean isProviderSide = RpcContext.getContext().isProviderSide();
        // 获取调用方IP地址
        String clientIP = RpcContext.getContext().getRemoteHost();
        // 获取当前服务配置信息，所有配置信息都将转换为URL的参数
        String app = RpcContext.getContext().getUrl().getParameter("application");
        // 注意：每发起RPC调用，上下文状态会变化
        yyyService.yyy();
        // 此时本端变成消费端，这里会返回false
        boolean isProviderSide = RpcContext.getContext().isProviderSide();
    } 
}
```