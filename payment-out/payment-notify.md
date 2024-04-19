# 📬 代付异步通知

> 用户支付完成后，系统会自动向订单关联的回调地址（notify\_url）发送通知消息，告知该笔订单已支付完成。

**请求方式：**POST

**传参方式：**数组

**请求参数：**

<table data-full-width="true"><thead><tr><th width="169">字段名称</th><th>说明</th></tr></thead><tbody><tr><td>appid</td><td>商户号</td></tr><tr><td>pay_money</td><td>金额，单位 CNY。</td></tr><tr><td>pay_usdt</td><td>金额，单位 USDT。</td></tr><tr><td>order_sn</td><td>商户订单号</td></tr><tr><td>status</td><td>订单状态：<a href="payment-search.md">查看订单查询表中的订单状态</a></td></tr><tr><td>success_time</td><td>成功时间</td></tr><tr><td>attach</td><td>用户附加数据</td></tr><tr><td>signature</td><td>数据签名 详见<a href="../introduction/signature.md">签名算法</a></td></tr></tbody></table>

## 通知返回

商户在收到通知信息后，在页面输出“OK”（ OK 两个字母大写， php 例子：echo "OK";），否则会重复 5 次发送点对点通知。



## 通知重试

系统向商户创建订单时指定的 notify\_url 发送 回调通知 后，如该 notify\_url 返回的不是 “OK”（ 没有双引号，OK 两个字母大写 )，则系统会触发 重试机制。

**相关规则如下：**

1. 间隔 5 秒 会进行第 1 次重试。
2. 如第一次重试仍为失败，后续通知频率（秒）：10，20，60，300。超过 5 分钟后如需推送，可以在后台手动补发。

\
