#公告 #迁移指南

团子画板（Dango）自上线以来，一直运行在 `dango.ink` 域名下。因该域名即将到期维护，为保障服务的持续可用与长期稳定，Dango 现迁移至 GitHub Pages 静态托管，并统一归入 `dango-canvas` 组织下管理。

由于 Dango 自设计之初就遵循纯客户端、本地优先（Local-First）且无后端的架构，这次迁移对数据和日常使用的影响极小。本文将针对不同使用场景，详细说明迁移步骤与链接更新方式。

---

## 1. 新访问地址一览

所有相关站点已整合迁移至 GitHub Pages 静态托管：

*   **在线画板（Web App）**：[https://dango-canvas.github.io/dango/](https://dango-canvas.github.io/dango/)
*   **产品落地页（Landing Page）**：[https://dango-canvas.github.io/page/](https://dango-canvas.github.io/page/)
*   **官方博客（Blog）**：[https://dango-canvas.github.io/blog/](https://dango-canvas.github.io/blog/)
*   **GitHub 组织主页**：[https://github.com/dango-canvas](https://github.com/dango-canvas)

---

## 2. 普通网页用户：如何迁移本地画板数据

### 机制说明
Dango 的核心理念是**本地优先**。你的画板草稿与节点数据保存在浏览器本地的 `localStorage` 中，从未上传到任何云端数据库。

受现代浏览器的**同源策略（Same-Origin Policy）**安全机制限制，不同的域名之间的本地存储互相隔离。因此，当你首次打开新的 GitHub Pages 域名时，浏览器无法直接读取旧域名下的本地画板，需要进行一次简单的数据交接。

### 迁移步骤（耗时约 10 秒）
1. 打开当前的 `dango.ink` 页面。
2. 按下快捷键 `Ctrl + S`（Mac 用户为 `Cmd + S`），或点击右下角导出菜单中的**导出为 Dango 文件**，将当前的画布保存为 `.dango` 文件。
3. 打开新地址：[https://dango-canvas.github.io/dango/](https://dango-canvas.github.io/dango/)。
4. 将刚刚下载的 `.dango` 文件**直接拖拽**进新网页的画布中（或点击右下角的导入按钮进行加载）。
5. 数据即刻无损加载完毕，并在新域名下自动建立本地持久化存储。

---

## 3. 分享链接与嵌入模式用户：如何更新链接

如果你此前在 Obsidian、Notion、个人博客中通过 Iframe 嵌入过 Dango 画板，或者收藏了分享链接：

### 机制说明
Dango 的分享链接与嵌入代码具有独特的**无状态特性**：画布的全部节点、连线与排版数据，均在客户端通过 `lz-string` 算法压缩并存放在 URL 的 `#`（Hash）片段中，完全不依赖中心化服务器解析。

### 更新方法：纯字符串网址替换
由于数据全部包含在链接后缀中，你只需要将原有的域名更换为新域名，后续的参数和 Hash 数据完全保持原样即可继续正常渲染。

#### ① 普通分享链接
*   旧链接格式：
    ```text
    https://dango.ink/#NoJgNMwAxgRAVPQPBuEN9wR2q...
    ```
*   替换为新链接：
    ```text
    https://dango-canvas.github.io/dango/#NoJgNMwAxgRAVPQPBuEN9wR2q...
    ```

#### ② Iframe 嵌入代码（Notion / Obsidian / 博客等）
*   旧嵌入代码：
    ```html
    <iframe src="https://dango.ink/?embed=true#NoJgNMwAxg..." style="width: 100%; height: 500px; border: none; border-radius: 12px;" allow="clipboard-write"></iframe>
    ```
*   只需将 `src` 中的网址替换为新地址：
    ```html
    <iframe src="https://dango-canvas.github.io/dango/?embed=true#NoJgNMwAxg..." style="width: 100%; height: 500px; border: none; border-radius: 12px;" allow="clipboard-write"></iframe>
    ```

---

## 4. 浏览器扩展与离线单文件分发

*   **Firefox 浏览器扩展**：后续版本将更新默认打开的 Web 目标地址，已安装用户可继续正常使用离线能力。
*   **单文件版本（Single-file Distribution）**：如果你直接使用的是从 Release 下载的 `dango.html` 单文件离线运行，则完全不受此次域名迁移影响。

---

## 5. 再次重申：安全与隐私承诺

迁移到 GitHub Pages 仅改变了静态文件的托管分发网络：
1. **零后端**：仍然没有后端服务与动态运行时。
2. **零数据上传**：所有渲染、压缩、解析均在你的设备 CPU/内存中执行。
3. **开源透明**：构建流程已通过 GitHub Actions 自动化公开，确保交付产物与源代码完全一致。

感谢大家对 Dango 的支持！如有任何疑问或反馈，欢迎在 [GitHub Issues](https://github.com/dango-canvas/dango/issues) 与我们交流。
