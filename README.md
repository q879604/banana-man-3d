# 🍌 香蕉人 3D · Banana Man

一个**纯静态、零依赖、可离线运行**的 3D 互动页面：打开就是一根长着大眼睛的香蕉人，
可以拖动环绕观看、缩放，背景是流动的抽象极光。

## 目录结构

```
banana-man-3d.html   # 单文件版整站（1.36 MB，双击即开，可直接发给别人）
public/index.html    # 实际部署的入口（内容与上面的单文件版一致）
wrangler.jsonc       # Cloudflare Workers 静态资源托管配置
```

## Cloudflare 部署（Workers）

仓库已经配好，Cloudflare 上连接本仓库后**不需要任何构建命令**，
默认的 `npx wrangler deploy` 即可直接发布：

- `wrangler.jsonc` 里的 `assets.directory = "./public"` 告诉 wrangler 把 `public/` 当静态站点托管；
- 纯静态资源托管，**不产生请求计费**，也不消耗 Worker 脚本 CPU 时间；
- `name` 需与面板上该 Worker 的项目名一致（CI 会自动用面板名覆盖，不一致只会打一条 warning）。

改内容：直接编辑 `public/index.html`，提交即自动重新部署。

## 本地预览

```bash
npx wrangler dev          # 本地起服务预览
npx wrangler deploy --dry-run   # 只校验配置，不真的发布
```
