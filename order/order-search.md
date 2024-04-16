# 🔍 订单查询

> 该接口供商户主动查询订单信息。

**请求地址：**/v1/api/open/order/search

**请求方式：**POST

**请求类型：**application/json

**请求参数：**

<table><thead><tr><th width="191">字段名称</th><th width="142">字段类型</th><th width="108">是否必填</th><th width="104">是否签名</th><th>说明</th></tr></thead><tbody><tr><td>appId</td><td>string(8)</td><td>是</td><td>是</td><td>商户号</td></tr><tr><td>merchantOrderNo</td><td>string(14-32)</td><td>是</td><td>是</td><td>商户订单号</td></tr><tr><td>signature</td><td>string(32)</td><td>是</td><td>是</td><td>数据签名，详见：<a href="broken-reference">签名算法</a></td></tr></tbody></table>

#### **返回值 data 参数：**

<table><thead><tr><th width="192">字段名称</th><th width="142.33333333333331">字段类型</th><th>说明</th></tr></thead><tbody><tr><td>appId</td><td>string</td><td>商户号</td></tr><tr><td>orderNo</td><td>string</td><td>UPay 订单号</td></tr><tr><td>merchantOrderNo</td><td>string</td><td>商户订单号</td></tr><tr><td>chainType</td><td>string</td><td><p>链路：</p><p>1: 波场(TRC20) </p><p>2: 以太坊(ERC20)</p><p>3: PayPal(PYUSD) </p></td></tr><tr><td>crypto</td><td>string</td><td>订单金额，单位 USDT / PYUSD</td></tr><tr><td>actualCrypto</td><td>string</td><td>订单实付金额，单位 USDT / PYUSD</td></tr><tr><td>poundage</td><td>string</td><td>手续费，单位 USDT / PYUSD</td></tr><tr><td>actualPoundage</td><td>string</td><td>订单实付手续费，单位 USDT / PYUSD</td></tr><tr><td>status</td><td>string</td><td>订单状态，详见：<a href="broken-reference">订单状态</a></td></tr><tr><td>attach</td><td>string</td><td>用户自定义数据</td></tr><tr><td>createdAt</td><td>string</td><td>订单创建时间，Unix 秒级时间戳</td></tr><tr><td>completedAt</td><td>string</td><td>订单完成时间，Unix 秒级时间戳。订单为待支付时，该字段为空</td></tr></tbody></table>

#### **订单状态：**

<table><thead><tr><th width="194">status</th><th width="142.66666666666666">字段类型</th><th>说明</th><th data-hidden></th></tr></thead><tbody><tr><td>0</td><td>string</td><td>待支付</td><td>待支付</td></tr><tr><td>1</td><td>string</td><td>支付成功</td><td>支付成功</td></tr><tr><td>2</td><td>string</td><td>支付超时</td><td>超时</td></tr><tr><td>3</td><td>string</td><td>支付失败</td><td>失败</td></tr></tbody></table>
