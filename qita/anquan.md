# 安全

**前端常见攻击**
* **XSS攻击**
> 在web前端方面，XSS攻击可以简单的理解为页面被javascript代码注入了。

    * 对前端输出数据进行转义，过滤script标签，包括：用户提交数据、URL参数获取到的数据
    * img标签的src进行验证，防止被注入onerror事件
    * 保护好cookie，可以设置为httponly


* **CSRF攻击**
> Cross-site request forgery跨站请求伪造，也被称为"One Click Attack"。本质是网站中的一些提交行为，被黑客利用。

    * 遵守post与get的使用，对数据的提交与更改要用post请求
    * 页面生成csrf token（随机并唯一的令牌），之后请求都带上这个token做校验


* 网络劫持攻击
> 很多时候访问网站，会经过很多层代理，数据可能被中间代理层的劫持者截获，导致用户账户密码等泄露。

    * 如果可以，使用https


* 控制台注入代码
> 用户被引诱按下F12并粘贴代码导致被攻击。


**相关文章**
* [聊一聊WEB前端安全那些事儿](https://segmentfault.com/a/1190000006672214)
* [浅谈WEB安全性（前端向）](http://www.cnblogs.com/vajoy/p/4176908.html)