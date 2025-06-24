# API 接口

Folo 主要 API 路由集中在 SSR 服务（Fastify）和部分 Serverless 函数，支持内容聚合、OG 图生成、静态页面、Webhook 等。

## SSR 服务主要接口
- `/og/:type/:id`  
  - 生成 Open Graph 图像，type 支持 feed/user/list。
- `/privacy-policy`  
  - 返回隐私政策 HTML。
- `/terms`  
  - 返回服务条款 HTML。
- `*`  
  - SSR 渲染页面，动态注入 meta、环境变量。

## Serverless API
- `/api/vercel_webhook`  
  - Vercel 部署回调，校验签名并自动清理 Cloudflare 缓存。

## 移动端 API 封装
- `/v1/trendings?language=xx`  
  - 获取热门内容聚合（apps/mobile/src/api/trending.ts）。

## 说明
- 其他 API 路由和业务接口通过 SSR 服务动态注册，部分接口依赖于 shared/env.ssr、meta-handler、lib/seo 等模块。
- 具体业务 API 可根据 SSR 路由和 packages/internal/database schema 扩展。
