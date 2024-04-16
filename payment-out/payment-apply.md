# 📤 提交代付

> 商户可调用该接口，发起账户提现申请。

**请求地址：**/v1/api/open/withdraw/apply

**请求方法：**POST

**请求类型：**application/json

**请求参数：**

<table><thead><tr><th width="187">字段名称</th><th width="146">字段类型</th><th width="109">是否必填</th><th width="109">是否签名</th><th>说明</th></tr></thead><tbody><tr><td>appId</td><td>string(8)</td><td>是</td><td>是</td><td>商户号</td></tr><tr><td>merchantOrderNo</td><td>string(14-32)</td><td>是</td><td>是</td><td>商户端自主生成的代付订单号，在商户端要保证唯一性</td></tr><tr><td>chainType</td><td>string(1)</td><td>是</td><td>是</td><td><p>链路：</p><p>1: 波场(TRC20) </p><p>2: 以太坊(ERC20)</p></td></tr><tr><td>crypto</td><td>string(10)</td><td>是</td><td>是</td><td>代付金额 单位：USDT</td></tr><tr><td>toAddress</td><td>string(64)</td><td>是</td><td>是</td><td>收款地址</td></tr><tr><td>attach</td><td>string(64)</td><td>否</td><td>否</td><td>用户自定义数据</td></tr><tr><td>signature</td><td>string(32)</td><td>是</td><td>是</td><td>数据签名，详见：<a href="../introduction/signature.md">签名算法</a></td></tr></tbody></table>

**返回值 data 参数：**

<table><thead><tr><th width="188.33333333333331">字段名称</th><th width="146">字段类型</th><th>说明</th></tr></thead><tbody><tr><td>appId</td><td>string</td><td>商户号</td></tr><tr><td>orderNo</td><td>string</td><td>UPay 订单号</td></tr><tr><td>merchantOrderNo</td><td>string</td><td>商户订单号</td></tr><tr><td>crypto</td><td>string</td><td>代付金额，单位 USDT</td></tr><tr><td>poundage</td><td>string</td><td>代付手续费，单位 USDT</td></tr><tr><td>status</td><td>string</td><td>代付状态，详见：<a href="payment-search.md#dai-fu-zhuang-tai">代付状态</a></td></tr><tr><td>createdAt</td><td>string</td><td>代付创建时间，Unix 秒级时间戳</td></tr><tr><td>completedAt</td><td>string</td><td>代付完成时间，Unix 秒级时间戳。订单为待支付时，该字段为空</td></tr></tbody></table>
