# 📤 提交代付

> 商户可调用该接口，发起账户提现申请。

**请求地址：**https://web.upay.ink/api/df/apply

**请求方式：**POST

**传参方式：**数组

**请求参数：**

<table><thead><tr><th width="175">字段名称</th><th width="122">字段类型</th><th width="100">必填参数</th><th>说明</th></tr></thead><tbody><tr><td>appid</td><td>string(16)</td><td>必填</td><td>商户号</td></tr><tr><td>money</td><td>string(16)</td><td>必填</td><td>代付金额 单位：USDT</td></tr><tr><td>chain_type</td><td>string(16)</td><td>必填</td><td>链路：1:波场(TRC20) 2:以太坊(ERC20) </td></tr><tr><td>df_sn</td><td>string(32)</td><td>必填</td><td>用户端自主生成的代付订单号，在用户端要保证唯一性</td></tr><tr><td>notify_url</td><td>string(500)</td><td>必填</td><td>接收平台异步通知的回调地址。必须为可直接访问的 URL，不能带参数、session 验证、csrf 验证</td></tr><tr><td>receive_address</td><td>string(64)</td><td>必填</td><td>收款地址</td></tr><tr><td>attach</td><td>string(127)</td><td>选填</td><td>用户自定义数据，在 notify 的时候会原样返回</td></tr><tr><td>signature</td><td>string(32)</td><td>必填</td><td>数据签名 详见<a href="../introduction/signature.md">签名算法</a></td></tr></tbody></table>

**返回参数：**

<table><thead><tr><th width="123">字段名称</th><th width="117">参数含义</th><th width="107">必填参数</th><th>说明</th></tr></thead><tbody><tr><td>code</td><td>请求状态</td><td>必填</td><td>1 表示提交成功，其它表示提交失败</td></tr><tr><td>msg</td><td>消息描述</td><td>必填</td><td>描述</td></tr></tbody></table>
