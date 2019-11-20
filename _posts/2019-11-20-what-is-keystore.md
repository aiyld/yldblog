---
layout: post
title:  "什么是KeyStore？KeyStore加解密详解"
categories: [ 区块链 ]
author: yld
tag: article
marks: ["前端", "源代码", "区块链", "钱包", "KeyStore", "加密算法"]
---

<p class="drop-cap">在许多密码学应用中，用户安全最终取决于密码，并且由于密码通常不能直接用作密码密钥，因此需要进行一些处理，KeyStore正是在这种背景下孕育而生。KeyStore是基于用户的密码的和待加密的信息生成的一段JSON。KeyStore存储是目前区块链行业的共识和规范，被众多主流链如BTC，ETH规范认可。大部分区块链钱包采用的存储办法是KeyStore存储形式，如Binance DEX和TrustWallet等等钱包。</p>
<p>KeyStore存储具有以下特点</p>
<ol>
<li>可校验；只有唯一的密码可以解密获得加密的信息</li>
<li>不可串改；KeyStore的加密部分，只要被修改了值将无法获得原始的加密信息，甚至不能通过密码校验</li>
<li>破解难度大；加解密需要通过层层哈希算法和千万次推导和加解密算法，每一次加解密都要耗时2-5秒左右，让暴力破解成为不可能的事情</li>
</ol>

<p>KeyStore是怎么生成？又是怎么解密的呢？首先先看KeyStore的基本构成：</p>
<pre><code>
{
    "crypto" : {
        "cipher" : "aes-128-ctr",
        "cipherparams" : {
            "iv" : "6087dab2f9fdbbfaddc31a909735c1e6"
        },
        "ciphertext" : "5318b4d5bcd28de64ee5559e671353e16f075ecae9f99c7a79a38af5f869aa46",
        "kdf" : "pbkdf2",
        "kdfparams" : {
            "c" : 262144,
            "dklen" : 32,
            "prf" : "hmac-sha256",
            "salt" : "ae3cd4e7013836a3df6bd7241b12db061dbe2c6785853cce422d148a624ce0bd"
        },
        "mac" : "517ead924a9d0dc3124507e3393d175ce3ff7c1e96529c6c555ce9e51205e9b2"
    },
    "id" : "3198bc9c-6672-5ab3-d995-4942343ae5b6",
    "version" : 3
}
</code></pre>

<h3>它包含了三部分信息</h3>
<blockquote><dl>
<dt><strong>crypto</strong></dt>
<dd>KeyStore加密信息的核心，接下来主要说明这一块的内容。</dd>
<dt><strong>id</strong></dt>
<dd>这个KeyStore的唯一ID。对于加解密并无关联</dd>
<dt><strong>version</strong></dt>
<dd>版本号。对于加解密并无关联</dd>
</dl></blockquote>

<h3>KeyStore的核心<strong>crypto</strong></h3>
<dl>
<dt><strong>cipher</strong></dt>
<dd>使用的加密算法；aes-128-ctr是一种加密算法，它的参数是：用户密码、待加密信息、iv、<strong>中间秘钥</strong></dd>
<dt><strong>cipherparams</strong></dt>
<dd>加密的参数；iv是一般是一个随机的32位的十六进制字符串</dd>
<dt><strong>ciphertext</strong></dt>
<dd>加密的结果；待加密信息和用户密码通过一系列加密算法，最终生成的就是这样的一个十六进制字符串。我们的解密最终</dd>
<dt><strong>kdf</strong></dt>
<dd>基于用户密码的算法，通过密码和参数kdfparams，产生<strong>中间秘钥</strong>，这个中间秘钥将用于生成mac和ciphertext。一般用到的算法是：pbkdf2或scrypt</dd>
<dt><strong>kdfparams</strong></dt>
<dd>
<p>kdf算法的参数</p>
<dd><strong>c</strong>: 算法加密次数，越高越安全，但同时也更耗时间和性能。</dd>
<dd><strong>dklen</strong>: 生成中间秘钥的字节数</dd>
<dd><strong>prf</strong>: 哈希算法</dd>
<dd><strong>salt</strong>: 一般是一个随机的32位的十六进制字符串</dd>
</dd>
<dt><strong>mac</strong></dt>
<dd>用于验证密码的正确及验证ciphertext是否原装未经过修改；它通过产生的<strong>中间秘钥</strong>和<strong>ciphertext</strong>，经过SHA3哈希算法最终得到。</dd>
</dl>

<div class="text-center">
<img src="/assets/images/posts/keystore.png"/>
</div>

<p>上述KeyStore的密码和待加密的信息如下：</p>
<ul>
<li>密码：testpassword</li>
<li>待加密的信息（这里是一个私钥）：7a28b5ba57c53603b0b07b56bba752f7784bf506fa95edc395f5cf6c7514fe9d</li>
</ul>

<p>那么它的推导信息如下：</p>
<ul>
<li>Derived key(中间秘钥): f06d69cdc7da0faffb1008270bca38f5e31891a3a773950e6d0fea48a7188551</li>
<li>MAC Body: e31891a3a773950e6d0fea48a71885515318b4d5bcd28de64ee5559e671353e16f075ecae9f99c7a79a38af5f869aa46</li>
<li>MAC: 517ead924a9d0dc3124507e3393d175ce3ff7c1e96529c6c555ce9e51205e9b2</li>
<li>Cipher key: f06d69cdc7da0faffb1008270bca38f5</li>
</ul>

<p>相关文档：</p>
<p>Web3 Secret Storage Definition: <a href="https://github.com/ethereum/wiki/wiki/Web3-Secret-Storage-Definition" target="_blank">https://github.com/ethereum/wiki/wiki/Web3-Secret-Storage-Definition</a></p>
