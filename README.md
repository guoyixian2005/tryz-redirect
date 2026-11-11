# 铜仁一中旧域名中转跳转 (`i.tryz.net` / `tryz.net` -> `https://gztryz.cn`)

本仓库同时兼容两种免费静态/边缘中转部署方案：

1. **GitHub + Vercel（推荐，支持服务端真正 HTTP 301 + 百度改版检测）**
   - Vercel 读取根目录 [`vercel.json`](./vercel.json) 返回 `HTTP 301 -> https://gztryz.cn/$1`；
   - `public/` 目录满足 Vercel `Other` 框架默认输出要求；
   - 在 Vercel 项目 **Settings -> Domains** 添加 `i.tryz.net`（可选 `www.tryz.net`、`tryz.net`），并按 Vercel 页面显示的记录值到新网 DNS 修改解析。

2. **仅使用 GitHub Pages（仅浏览器访问自动跳转）**
   - 在 GitHub 仓库 **Settings -> Pages** 开启 `Deploy from a branch`（`main` / `/ (root)`）；
   - Custom domain 填写 `i.tryz.net`；
   - 到新网 DNS 将 `i` 记录的 CNAME 改为 `<你的GitHub用户名>.github.io`；
   - 注意：GitHub Pages 返回 `HTTP 200` + `meta refresh`/JS 跳转，浏览器访客会自动跳到 `https://gztryz.cn`，但百度站长“网站改版 301 校验”需要 Vercel 等能返回服务端 `HTTP 301` 的节点才能通过。
