# API 安全管理

如今，越来越多的企业需要将自身数据、能力、服务向外开放，通常通常会以 rest 的方式向外提供，在 DICE 上我们可以通过 API 网关的插件来对 API 的入口进行统一的管理，[API 网关](../microservice/api-gateway.md)提供IP拦截、服务负载保护、跨站防护、流量控制等多重手段保证 API 安全，降低 API 开放风险。

## 支持 HTTPS
HTTPS 在 HTTP 的基础上加入了 SSL 协议，对信息、数据加密，用来保证数据传输的安全。现如今被广泛使用。
API网关也支持使用HTTPS对您的API请求进行加密。可以控制到 API 级别，即您可以强制您的 API 只支持 HTTP、HTTPS 或者两者均支持。

开启 HTTPS 参考 [这里](./enable-https.md)。
## IP 拦截
IP 访问控制是 API 网关提供的 API 安全防护组件之一，负责控制 API 的调用来源 IP （支持IP段）。您可以通过配置某个 API 的 IP 白名单/黑名单来允许/拒绝某个来源的API请求。

IP 拦截配置参考 [这里](../microservice/api-gateway-advanced1.md#ip-拦截)。
## 服务负载保护

API 网关会按照配置的服务最大吞吐，对请求服务的流量去峰填谷，确保到达后端服务的请求速率在限定的吞吐内，保障后端服务不会因为处理大量的请求为导致无法提供服务或者服务质量高降低。

服务负载保护配置参考 [这里](../microservice/api-gateway-advanced1.md#服务负载保护)。
## 跨站防护( CSRF )

跨站请求伪造，也被称为 one-click attack 或者 session riding，通常缩写为 CSRF 或者 XSRF， 是一种挟制用户在当前已登录的 Web 应用程序上执行非本意的操作的攻击方法。CSRF 利用的是站对用户网页浏览器的信任来执行某某些非法操作，具体的工具行为如下：

1. 首先用户C浏览并登录了受信任站点A；
2. 登录信息验证通过以后，站点A会在返回给浏览器的信息中带上已登录的 cookie，cookie 信息会在浏览器端保存一定时间（根据服务端设置而定）；
3. 完成这一步以后，用户在没有登出（清除站点A的 cookie）站点A的情况下，访问恶意站点B；
4. 这时恶意站点 B的某个页面向站点A发起请求，而这个请求会带上浏览器端所保存的站点A的cookie；
5. 站点A根据请求所带的 cookie，判断此请求为用户C所发送的，该请求可能是邮件发送、打赏、交易转账等等，造成个人隐私泄露以及财产安全。

配置跨站防护参考 [这里](../microservice/api-gateway-advanced1.md#跨站防护-csrf-校验)。
