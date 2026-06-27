---
title: DataviewJS 测试页
tags:
  - 交易日志
  - 测试
---

# DataviewJS 测试

```dataviewjs
// 测试 0：p.file.lists 是否能读到内联字段
const pages = dv.pages('"09_知识库管理/引用数据库"');
dv.paragraph("📊 测试 0：找到引用数据库页面数 = " + pages.length);
if (pages.length > 0) {
  const p = pages[0];
  dv.paragraph("📊 页面 lists 条数 = " + (p.file.lists ? p.file.lists.length : 'undefined'));
  if (p.file.lists && p.file.lists.length > 0) {
    const first = p.file.lists[0];
    dv.paragraph("📊 第一条 list text = " + first.text);
    dv.paragraph("📊 第一条 list 类别 = " + first.类别 + " | 语录 = " + first.语录);
  }
}


dv.span("<br><br>");
// 测试 7：轮询硬编码语录
const hardQuotes = ["纪律是交易者和赌徒之间的分界线。", "计划你的交易，交易你的计划。", "保住本金是第一原则。", "截断亏损，让利润奔跑。"];
let container7 = dv.el('div', "");
container7.id = "quote-rolling-7";

function rollQuote7() {
  const c = document.getElementById("quote-rolling-7");
  if (!c) return;
  c.innerHTML = '<blockquote style="border-left: 4px solid #7f6df2; padding: 10px 20px; background: rgba(127,109,242,0.08); border-radius: 4px; margin: 0;">' + hardQuotes[Math.floor(Math.random() * hardQuotes.length)] + '</blockquote>';
}
rollQuote7();
setInterval(rollQuote7, 3000);
```
