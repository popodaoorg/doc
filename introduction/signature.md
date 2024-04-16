# 🔗 签名算法

## 签名生成的通用步骤如下

1. 设所有发送或者接收到的数据为集合 M，将集合 M 内 **需要加签** 的参数按照参数名 ASCII 码从小到大排序（字典序），使用 URL 键值对的格式（即 key1=value1\&key2=value2…）拼接成字符串 stringA。
2. 在 stringA 最后拼接上 `&appSecret=密钥` 得到 stringSignTemp 字符串，并对 stringSignTemp 进行 MD5 运算，再将得到的字符串所有字符转换为大写，得到 signature 值。



## 特别注意以下重要规则

* 参数名 ASCII 码从小到大排序（字典序）。
* 参数名区分大小写。
* 传送的 signature 参数不参与签名，将生成的签名与该 signature 值作校验。
* 接口可能增加字段，验证签名时必须支持增加的扩展字段。



## 举例 (PHP)

例如传递的参数如下：

```
appId: 12345
chainType: 1
merchantOrderNo: 123123123123
productName：Goods
```

第一步：去掉 **不需要加签** 的参数，对 **需要加签** 的参数按照 key=value 的格式，并按照参数名 ASCII 字典序排序如下

<pre class="language-php" data-overflow="wrap"><code class="lang-php"><strong>$stringA = 'appId=12345&#x26;chainType=1&#x26;merchantOrderNo=123123123123';
</strong></code></pre>

第二步：对上一步中的字符串拼接 `&appSecret=密钥`

<pre class="language-php" data-overflow="wrap"><code class="lang-php"><strong>$stringSignTemp = $stringA.'&#x26;appSecret=密钥';
</strong></code></pre>

第三步：对上一步中字符串取 md5 值

{% code overflow="wrap" %}
```php
$signature = md5($stringSignTemp);
```
{% endcode %}

第四步：对上面 md5 值转化为大写

```php
$signature = strtoupper($signature);
```
