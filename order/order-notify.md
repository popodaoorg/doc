# 🔔 订单异步通知

> 订单完成后，系统会自动向订单关联的回调地址（notifyUrl）发送通知消息，告知该笔订单的最终状态。

**请求方法：**POST

**请求类型：**application/json

**请求参数：**

<table><thead><tr><th width="188">字段名称</th><th width="119">字段类型</th><th width="102">是否必填</th><th width="99">是否签名</th><th>说明</th></tr></thead><tbody><tr><td>appId</td><td>string</td><td>是</td><td>是</td><td>商户号</td></tr><tr><td>orderNo</td><td>string</td><td>是</td><td>是</td><td>UPay 订单号</td></tr><tr><td>merchantOrderNo</td><td>string</td><td>是</td><td>是</td><td>商户订单号</td></tr><tr><td>chainType</td><td>string</td><td>是</td><td>是</td><td><p>链路：</p><p>1: 波场(TRC20)</p><p>2: 以太坊(ERC20)  </p><p>3: PayPal(PYUSD)</p></td></tr><tr><td>crypto</td><td>string</td><td>是</td><td>是</td><td>金额，单位 USDT / PYUSD</td></tr><tr><td>actualCrypto</td><td>string</td><td>是</td><td>是</td><td>订单实付金额，单位 USDT / PYUSD</td></tr><tr><td>poundage</td><td>string</td><td>是</td><td>是</td><td>手续费，单位 USDT / PYUSD</td></tr><tr><td>actualPoundage</td><td>string</td><td>是</td><td>是</td><td>订单实付手续费，单位 USDT / PYUSD</td></tr><tr><td>status</td><td>string</td><td>是</td><td>是</td><td><p>订单状态：<a href="broken-reference">订单状态</a></p><p>​</p></td></tr><tr><td>createdAt</td><td>string</td><td>是</td><td>是</td><td>订单创建时间，Unix 秒级时间戳</td></tr><tr><td>completedAt</td><td>string</td><td>是</td><td>是</td><td>订单完成时间，Unix 秒级时间戳</td></tr><tr><td>attach</td><td>string</td><td>否</td><td>否</td><td>用户自定义数据，在回调到 notifyUrl 的时候会原样返回</td></tr><tr><td>signature</td><td>string</td><td>是</td><td>是</td><td>数据签名，详见：<a href="broken-reference">签名算法</a></td></tr></tbody></table>

### 通知返回 <a href="#tong-zhi-fan-hui" id="tong-zhi-fan-hui"></a>

商户在收到通知信息后，在响应体的 body 中输出 OK 或者 ok（php例子：echo "OK";) ，否则会重复 5 次发送点对点通知。

### 重试规则如下： <a href="#tong-zhi-fan-hui" id="tong-zhi-fan-hui"></a>

如第一次通知失败，后续通知频率（秒）：10，30，60，300，600 。
