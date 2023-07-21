# 🔗 签名算法

## 签名生成的通用步骤如下

1. 设所有发送或者接收到的数据为集合M，将集合M内非空参数值的参数按照参数名 ASCII 码从小到大排序（字典序），使用 URL 键值对的格式（即key1=value1\&key2=value2…）拼接成字符串 stringA。
2. 在 stringA 最后拼接上 `&appsecret=密钥` 得到 stringSignTemp 字符串，并对stringSignTemp 进行 MD5 运算，再将得到的字符串所有字符转换为大写，得到sign值。



## 特别注意以下重要规则

* 参数名 ASCII 码从小到大排序（字典序）；
* 如果参数的值为空不参与签名；
* 参数名区分大小写；
* 验证调用返回或平台主动通知签名时，传送的 sign 参数不参与签名，将生成的签名与该 sign 值作校验。
* 接口可能增加字段，验证签名时必须支持增加的扩展字段。



## 举例

例如传递的参数如下：

```
appid: 12345
pay_money: 1
order_sn: 123123123123
```

第一步：对参数按照 key=value 的格式，并按照参数名 ASCII 字典序排序如下

{% code overflow="wrap" %}
```php
appid=12345&order_sn=123123123123&pay_money=1
```
{% endcode %}

第二步：对上一步中的字符串拼接 `&appsecret=密钥`

{% code overflow="wrap" %}
```php
appid=12345&order_sn=123123123123&pay_money=1&appsecret=xxxxxxxxx
```
{% endcode %}

第三步：对上一步中字符串取 md5 值

{% code overflow="wrap" %}
```php
$sign = md5('appid=12345&order_sn=123123123123&pay_money=1&appsecret=xxxxxxxxx');
```
{% endcode %}

第四步：对上面 md5 值转化为大写

```php
$sign = strtoupper($sign);
```



## PHP代码示例

```php
// 签名方法
function sign(array $data, $appsecret) {
    ksort($data);
    $sign = strtoupper(md5(urldecode(http_build_query($data)).'&appsecret='.$appsecret));
    return $sign;
}

// 用法示例
$data = [
    'appid' => '12345',
    'pay_money' => 1,
    'order_sn' => '123123123123',
];

// 平台通信密钥
$appsecret = 'xxxxxxxxxxx';
$sign = sign($data, $appsecret);

```

\
