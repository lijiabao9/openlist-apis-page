# openlist-api-pages

基于 [OpenList-APIPages](https://github.com/OpenListTeam/OpenList-APIPages) 精简而来的 Cloudflare Worker 部署版本。

## 与原版的区别

原项目同时支持以下部署方式：

- Cloudflare Workers
- Cloudflare Pages Functions
- Node.js 本地服务 (Hono + Webpack)
- Docker 部署
- 腾讯 EdgeOne

本分支 **仅保留 Cloudflare Workers 部署**，砍掉了其余所有部署方式和冗余文件。

### 移除内容

| 移除项 | 说明 |
| -------- | ------ |
| `src/basic.ts` | Node.js 本地服务入口，依赖 dotenv + @hono/node-server |
| `functions/` | Cloudflare Pages Functions 模式 |
| `Dockerfile` / `Dockerfile-Lite` | Docker 容器化部署 |
| `docker-compose.yml` | Docker 编排 |
| `entrypoint.sh` / `entrypoint-lite.sh` | Docker 入口脚本 |
| `alitoken2.py` | Python 阿里云盘令牌脚本 |
| `edgeone.json` | 腾讯 EdgeOne 配置 |
| `webpack.config.cjs` | Webpack 打包配置 |
| 冗余 npm 依赖 | 从 23 个精简至 7 个 |

## 快速开始

```bash
# 安装依赖
npm install

# 本地调试
npm run dev

# 部署到 Cloudflare Workers
npm run deploy
```

## 配置

编辑 `wrangler.jsonc`，填入各网盘的 API 密钥：

| 变量 | 说明 |
| ------ | ------ |
| `MAIN_URLS` | 主站 URL |
| `PROXY_API` | 代理 API 地址 |
| `*_uid` / `*_key` | 各网盘 OAuth 应用的 Client ID / Secret |

支持以下网盘：

- OneDrive
- 阿里云盘（页面登录 + 扫码 + TV 版）
- 百度网盘
- 115 网盘（页面登录 + 扫码）
- 123 云盘
- Google Drive
- Yandex Disk
- Dropbox
- 夸克网盘

## License

沿用原项目许可。
