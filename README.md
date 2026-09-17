# IoT PoC Obsidian-style Preview

[打开 GitHub Pages 页面](https://xuan-crane.github.io/IoT-PoC-Obsidian-GitHub-Preview/)

根目录的 Markdown 文件现在就是页面的唯一源文件。GitHub 直接预览时，比较块会按顺序显示；GitHub Pages 会用同一份内容把它们排成双栏：

- `00-大块版索引.md`：总索引；
- `A7100RU.md`、`AC500.md`、`DIR-816.md`、`DIR-818LW.md`、`DIR-823G.md`、`DIR-823X.md`、`T6.md`：按固件的页面源文件；
- 修改这些根目录 Markdown 并推送到 `main` 后，GitHub Pages 会自动重新构建并同步页面；
- `_layouts/default.html` 和 `assets/css/style.css` 只负责网页外观与复制按钮，不承载 PoC 内容；
- `docs/` 保留为此前版本的备份，不是当前 Pages 的数据源。

GitHub 直接查看源文件：

- [A7100RU.md](A7100RU.md) · [AC500.md](AC500.md) · [DIR-816.md](DIR-816.md) · [DIR-818LW.md](DIR-818LW.md)
- [DIR-823G.md](DIR-823G.md) · [DIR-823X.md](DIR-823X.md) · [T6.md](T6.md)
