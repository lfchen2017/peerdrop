# PeerDrop

基于 Cloudflare Workers 的文件实时传输工具，支持 P2P 直连和 CF 中继两种模式，文件不落盘。

## 特性

- **P2P 直连** — 双方勾选"优先 P2P"时通过 WebRTC 打洞直传，速度更快
- **CF 中继** — 打洞失败或任一方不勾选时自动回退，无需公网 IP
- **不落盘** — 文件通过 WebSocket / DataChannel 实时流式传输，不存储在服务器
- **密码保护** — 发送端需登录，接收端通过链接直接接收
- **免费部署** — Durable Object SQLite 类，Cloudflare 免费计划可用

## 一键部署

1. **Fork** 本仓库到你的 GitHub 账号
2. 打开 [Cloudflare Workers & Pages](https://dash.cloudflare.com/?to=/:account/workers-and-pages/create)，选择 **Continue with GitHub**
3. 选择你 Fork 的仓库，填写：
   - 构建命令：`npm run build`
   - 部署命令：`npm run deploy`
4. 等待部署完成
5. 进入 Workers → peerdrop → **Settings → Variables and Secrets**，添加 `PASSWORD`（Secret 类型）作为登录密码

部署完成后，打开 Workers 分配的域名即可使用。

> **提示：** Workers 默认域名（`*.workers.dev`）在部分网络环境下不可访问。如遇此情况，请前往 Workers → peerdrop → **Settings → Domains & Routes** 添加自定义域名（需要一个已托管在 Cloudflare 的域名）。

## 使用方式

1. 发送方打开首页，输入密码登录
2. 选择文件，点击"生成传输链接"
3. 将链接发给接收方
4. 接收方打开链接，选择保存位置，开始实时传输

双方需保持页面打开直到传输完成。

## 致谢

本项目参考了以下内容：

- [原文](https://mp.weixin.qq.com/s/quSRxZWAJeRa6CwhU4Ernw)
