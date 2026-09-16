---
layout: default
permalink: /index.html
title: CVE PoC 大块彩色对照（按固件）
date: 2026-09-15
source_note: "../"
tags:
  - IoT漏洞挖掘
  - CVE
  - PoC相似性
---

# CVE PoC 大块彩色对照（按固件）

> [!info] 版本说明
> 这版专门解决“表格太碎”的问题：不把请求拆成方法、路径、字段等小行，而是把原 PoC 的 HTTP 请求体、XML、JSON 或关键脚本大块并排展示，只在原文字上加颜色。

## 颜色规则

<span style="color:#b91c1c;font-weight:700">红色标题：同接口或同骨架高度相似，载荷可能存在差异。</span><br>
<span style="color:#17803d;font-weight:700">绿色文字：两边原 PoC 中完全相同的部分。</span><br>
<span style="color:#c2410c;font-weight:700">橙色文字：原 PoC 中实际发生变化的字段、参数、长度或载荷。</span><br>
<span style="color:#64748b;font-weight:700">蓝灰文字：只作候选，不标成确认相似。</span>

> [!warning] 只处理颜色，不改 PoC 逻辑
> 原始请求主体、头部、字段顺序和生成式按采集来源完整保留；Host、Cookie、Token、HNAP_AUTH、Basic Authorization、实验密码等必须由运行环境提供的值继续保留为来源中的变量或安全占位，不把不存在的固定值写死。每个 PoC 大块标题下方都提供可直接打开的原始网页或 payload.seed 链接。

## 可能相似的 CVE（按固件排序）

> <span style="color:#b91c1c;font-weight:700">A 级/红色：同接口或同骨架高度相似，载荷可能存在差异；</span><span style="color:#c2410c;font-weight:700">B 或 B+ 级/橙色：请求骨架高度接近但仍有变化；</span><span style="color:#64748b;font-weight:700">C 级/蓝灰：只记录可能相似，不作确认判断。</span>

### A7100RU

- <span style="color:#b91c1c;font-weight:700">A 级：</span>CVE-2023-26978 ↔ CVE-2023-27135

[打开 A7100RU 大块对照](A7100RU.html)

### AC500

- <span style="color:#c2410c;font-weight:700">B 级：</span>CVE-2023-46060 ↔ CVE-2024-32318

[打开 AC500 大块对照](AC500.html)

### DIR-816

- <span style="color:#c2410c;font-weight:700">B+ 级：</span>CVE-2022-29322 ↔ CVE-2023-43238

[打开 DIR-816 大块对照](DIR-816.html)

### DIR-818LW

- <span style="color:#b91c1c;font-weight:700">A 级：</span>CVE-2019-12786 ↔ CVE-2019-12787 ↔ CVE-2019-13481

[打开 DIR-818LW 大块对照](DIR-818LW.html)

### DIR-823G

- <span style="color:#b91c1c;font-weight:700">A 级：</span>CVE-2019-7297 ↔ CVE-2022-43109
- <span style="color:#c2410c;font-weight:700">B 级：</span>CVE-2019-13128 ↔ CVE-2019-15528
- <span style="color:#b91c1c;font-weight:700">A 级：</span>CVE-2019-15529 ↔ CVE-2019-15530 ↔ CVE-2020-25367 ↔ CVE-2020-25368

[打开 DIR-823G 大块对照](DIR-823G.html)

### DIR-823X

- <span style="color:#b91c1c;font-weight:700">A 级：</span>CVE-2025-11095 ↔ CVE-2025-11097
- <span style="color:#c2410c;font-weight:700">B 级：</span>CVE-2025-11095 ↔ CVE-2025-11099
- <span style="color:#b91c1c;font-weight:700">A 级：</span>CVE-2026-1544 ↔ CVE-2026-2063

[打开 DIR-823X 大块对照](DIR-823X.html)

### T6

> 版本基准：CVE-2022-32045/32046/32047/32051/32052 = T6-V2（V4.1.9cu.5179_B20201015）；CVE-2025-7613/7524/7615 = T6（V4.1.5cu.748_B20211015）。两组不是同一硬件修订。

- <span style="color:#b91c1c;font-weight:700">A 级：</span>CVE-2025-7613 ↔ CVE-2025-7615
- <span style="color:#c2410c;font-weight:700">B 级：</span>CVE-2025-7613 ↔ CVE-2025-7524
- <span style="color:#b91c1c;font-weight:700">A 级：</span>CVE-2022-32045 ↔ CVE-2022-32046 ↔ CVE-2022-32047 ↔ CVE-2022-32051 ↔ CVE-2022-32052

[打开 T6 大块对照](T6.html)

## 固件对照页

- [A7100RU 大块对照](A7100RU.html)
- [AC500 大块对照](AC500.html)
- [DIR-816 大块对照](DIR-816.html)
- [DIR-818LW 大块对照](DIR-818LW.html)
- [DIR-823G 大块对照](DIR-823G.html)
- [DIR-823X 大块对照](DIR-823X.html)
- [T6 大块对照](T6.html)

> [!tip] 与前两版的关系
> `PoC相似性-按固件` 是两栏嵌入版，`彩色对照` 是细粒度字段表版，本目录 `大块对照` 是原始请求大块并排版；三者都保留，优先使用本目录。
