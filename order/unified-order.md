# 🛒 统一下单

> 用于生成指定数字货币的支付数据，包括收款金额(USDT)、收款地址、收款地址二维码等。商户可选择直接跳转至[**官方的收银台**](checkout.md)供用户支付，也可以使用数据自定义收银台。在用户支付成功后，系统将即时进行**回调通知**。

**请求地址：**https://web.upay.ink/api/pay/unifiedorder

**请求方式：**POST

**传参方式：**数组

**请求参数：**

<table><thead><tr><th width="150">字段名称</th><th width="124">字段类型</th><th width="92">必填参数</th><th>说明</th></tr></thead><tbody><tr><td>appid</td><td>string(16)</td><td><strong>必填</strong></td><td>商户号</td></tr><tr><td>pay_money</td><td>string(16)</td><td><strong>必填</strong></td><td>金额，精确到小数点后2位</td></tr><tr><td>money_type</td><td>string(16)</td><td><strong>必填</strong></td><td><p>单位：<br>1:美元(USD) <br>2:人民币(CNY) <br>3:印度卢比(INR) <br>4:日元(JPY) <br>5:韩元(KRW) <br>6:菲律宾比索(PHP)</p><p>7:欧元(EUR)</p><p>8:英镑(GBP)</p><p>9:瑞士法郎(CHF)</p><p>10:新台币(TWD)</p><p>11:港币(HKD)</p><p>12:澳门元(MOP)</p><p>13:新加坡币(SGD)</p><p>14:新西兰元(NZD)</p><p>15:泰铢(THB)</p><p>16:加拿大元(CAD)<br>当切换货币类型时，会实时转换成等值 USDT</p></td></tr><tr><td>chain_type</td><td>string(16)</td><td><strong>必填</strong></td><td>链路：1:波场(TRC20) 2:以太坊(ERC20) </td></tr><tr><td>channel_type</td><td>string(16)</td><td><strong>必填</strong></td><td>通道类型：2:个人收款地址（需在商户后台设置收款钱包地址）</td></tr><tr><td>order_sn</td><td>string(32)</td><td><strong>必填</strong></td><td>用户端自主生成的订单号，在用户端要保证唯一性</td></tr><tr><td>notify_url</td><td>string(500)</td><td><strong>必填</strong></td><td>接收平台支付异步通知的回调地址。必须为可直接访问的 URL，不能带参数、session 验证、csrf 验证</td></tr><tr><td>callback_url</td><td>string(500)</td><td>选填</td><td>即时回调地址，支付成功后，点击返回到的商户地址。务必包含 http:// 开头</td></tr><tr><td>product_name</td><td>string(64)</td><td>选填</td><td>商品名称</td></tr><tr><td>pay_username</td><td>string(64)</td><td>选填</td><td>付款人名称</td></tr><tr><td>attach</td><td>string(127)</td><td>选填</td><td>用户自定义数据，在notify的时候会原样返回</td></tr><tr><td>signature</td><td>string(32)</td><td><strong>必填</strong></td><td>数据签名 详见<a href="../introduction/signature.md">签名算法</a></td></tr></tbody></table>

**请求返回：**

> 特别提醒：支付后回调函数，并不能标示支付状态。用户需进一步完成验单逻辑

返回参数：

<table><thead><tr><th width="122">字段名称</th><th width="242">参数含义</th><th width="97">必填参数</th><th>说明</th></tr></thead><tbody><tr><td>code</td><td>请求状态</td><td>必填</td><td>1 表示提交成功，其它表示提交失败</td></tr><tr><td>msg</td><td>消息描述</td><td>必填</td><td>失败原因</td></tr><tr><td>data</td><td>订单信息（数据类型：集合）</td><td>必填</td><td>返回数据，查看下表</td></tr></tbody></table>

**返回值data参数：**

<table><thead><tr><th width="209">字段名称</th><th>参数含义</th></tr></thead><tbody><tr><td>appid</td><td>商户号</td></tr><tr><td>order_sn</td><td>商户订单号</td></tr><tr><td>pay_usdt</td><td>订单金额，需要支付的 USDT</td></tr><tr><td>address</td><td>收款地址</td></tr><tr><td>img</td><td>收款地址的二维码</td></tr><tr><td>chain_type</td><td>链路：1:波场(TRC20) 2:以太坊(ERC20) </td></tr><tr><td>pay_url</td><td>官方收银台地址，商户可直接跳转到该地址供用户支付</td></tr><tr><td>en_pay_url</td><td>官方英文收银台地址，商户可直接跳转到该地址供国外用户支付</td></tr><tr><td>exchange_rate</td><td>下单时的汇率</td></tr><tr><td>time_out</td><td>订单过期时间，时间戳 单位 秒</td></tr><tr><td>signature</td><td>安全校验签名串</td></tr></tbody></table>
