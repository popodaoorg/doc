# 🔍 订单查询

> 该接口供商户主动查询订单状态。多用于商户自定义收银台的场景。

**请求地址：**https://web.upay.ink/api/pay/search

**请求方式：**POST

**传参方式：**数组

**请求参数：**

<table><thead><tr><th width="131">字段名称</th><th width="125">字段类型</th><th width="133">必填参数</th><th>说明</th></tr></thead><tbody><tr><td>appid</td><td>string(16)</td><td>必填</td><td>商户号</td></tr><tr><td>order_sn</td><td>string(50)</td><td>必填</td><td>商户订单号</td></tr><tr><td>signature</td><td>string(32)</td><td>必填</td><td>数据签名 详见<a href="../introduction/signature.md">签名算法</a></td></tr></tbody></table>

**返回参数：**

<table><thead><tr><th width="115">字段名称</th><th width="171">参数含义</th><th width="98">必填参数</th><th>说明</th></tr></thead><tbody><tr><td>code</td><td>请求状态</td><td>必填</td><td>1表示查询成功，其它表示查询失败</td></tr><tr><td>msg</td><td>消息描述</td><td>必填</td><td>失败原因</td></tr><tr><td>data</td><td>订单信息（数据类型：集合）</td><td>必填</td><td>返回数据，查看下表</td></tr></tbody></table>

**返回值 data 参数：**

<table><thead><tr><th width="245.5">字段名称</th><th>参数含义</th></tr></thead><tbody><tr><td>appid</td><td>商户号</td></tr><tr><td>order_sn</td><td>商户订单号</td></tr><tr><td>pay_usdt</td><td>订单金额，支付的 USDT</td></tr><tr><td>pay_money</td><td>订单金额，支付的 CNY</td></tr><tr><td>status</td><td>订单状态：查看下表</td></tr><tr><td>success_time</td><td>成功时间</td></tr><tr><td>signature</td><td>安全校验签名串</td></tr></tbody></table>

**订单状态：**

| status | 描述   |
| ------ | ---- |
| 0      | 待支付  |
| 1      | 支付成功 |
| 2      | 超时   |
| 3      | 失败   |
| 4      | 部分付款 |
| 5      | 退款中  |
| 6      | 退款成功 |
| 7      | 部分退款 |
| 8      | 退款失败 |
