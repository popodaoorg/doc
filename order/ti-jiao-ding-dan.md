# 🛒 提交订单

> 用于生成指定数字货币的支付数据，商户可以通过支付链接引导用户跳转至 UPay 收银台付款。在用户支付成功后，系统将即时进行**回调通知**。
>
> 注意：用户必须严格按照订单金额进行付款，如果付款金额不一致，将会导致**订单无法被处理**。

**请求地址：**/v1/api/open/order/apply

**请求方式：**POST

**请求类型：**application/json

**请求参数：**

<table><thead><tr><th width="180">字段名称</th><th width="140">字段类型</th><th width="97">是否必填</th><th width="98">是否签名</th><th>说明</th></tr></thead><tbody><tr><td>appId</td><td>string(8)</td><td><strong>是</strong></td><td><strong>是</strong></td><td>商户号</td></tr><tr><td>merchantOrderNo</td><td>string(14-32)</td><td><strong>是</strong></td><td><strong>是</strong></td><td>商户端自主生成的订单号，在商户端要保证唯一性</td></tr><tr><td>chainType</td><td>string(1)</td><td><strong>是</strong></td><td><strong>是</strong></td><td><p>链路：</p><p>1: 波场(TRC20) </p><p>2: 以太坊(ERC20)</p><p>3: PayPal(PYUSD)  </p></td></tr><tr><td>fiatAmount</td><td>string(10)</td><td><strong>是</strong></td><td><strong>是</strong></td><td>法币金额，精确到小数点后 4 位</td></tr><tr><td>fiatCurrency</td><td>string(3)</td><td><strong>是</strong></td><td><strong>是</strong></td><td><p>USD (美元)</p><p>CNY (人民币)</p><p>INR (卢比)</p><p>JPY (日元)</p><p>KRW (韩元)</p><p>PHP (比索)</p><p>EUR (欧元)</p><p>GBP (英镑)</p><p>CHF (瑞士法郎)</p><p>TWD (新台币)</p><p>HKD (港币)</p><p>MOP (澳门元)</p><p>SGD (新加坡币)</p><p>NZD (新西兰元)</p><p>THB (泰铢)</p><p>CAD (加拿大元)</p></td></tr><tr><td>attach</td><td>string(64)</td><td>否</td><td>否</td><td>用户自定义数据，在回调到  notifyUrl 的时候会原样返回</td></tr><tr><td>productName</td><td>string(32)</td><td>否</td><td>否</td><td>商品名称</td></tr><tr><td>notifyUrl</td><td>string(256)</td><td><strong>是</strong></td><td><strong>是</strong></td><td>接收异步通知的回调地址。必须为可直接访问的 URL，不能带参数、session 验证、csrf 验证</td></tr><tr><td>redirectUrl</td><td>string(256)</td><td>否</td><td>否</td><td>支付成功后，前端重定向地址。务必包含 http:// 或 https:// 开头</td></tr><tr><td>signature</td><td>string(32)</td><td><strong>是</strong></td><td><strong>是</strong></td><td>数据签名，详见：<a href="broken-reference">签名算法</a></td></tr></tbody></table>

**返回值 data 参数：**

<table><thead><tr><th>字段名称</th><th width="172.66666666666666">字段类型</th><th>说明</th></tr></thead><tbody><tr><td>appId</td><td>string</td><td>商户号</td></tr><tr><td>orderNo</td><td>string</td><td>UPay 订单号</td></tr><tr><td>merchantOrderNo</td><td>string</td><td>商户订单号</td></tr><tr><td>exchangeRate</td><td>string</td><td>下单时的法币汇率</td></tr><tr><td>crypto</td><td>string</td><td>订单金额，单位 USDT / PYUSD</td></tr><tr><td>status</td><td>string</td><td>订单状态，详见：<a href="broken-reference">订单状态</a></td></tr><tr><td>payUrl</td><td>string</td><td>收银台地址，商户可直接跳转到该地址供用户支付</td></tr></tbody></table>
