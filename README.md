# 长夜灯塔 · 隐私与支援页

`site/` 是两页静态站点，内容与 `PRIVACY.md` / `SUPPORT.md` 一致，无外部依赖
（无 CDN、无字体请求、无脚本），可以直接放到任何静态托管上。

- `index.html` — 支援页 + 常见问题（中英）
- `privacy.html` — 隐私政策（中英）
- `style.css` — 近黑底、金色强调，与 App 的视觉语言一致

> 先把 `support@nightbeacon.app` 换成你能实际收信的地址。域名尚未注册时，
> 这个邮箱和 App Store Connect 里的支援链接都会失效。

## 发布

App Store Connect 需要两个**可公开访问**的网址：隐私政策网址、支援网址。
任选一种托管方式：

### GitHub Pages

1. 把仓库推送到 GitHub（公开仓库，或 GitHub Pro 的私有仓库 Pages）。
2. Settings → Pages → Source 选 `Deploy from a branch`，
   Branch 选发布分支，目录选 `/site`。
3. 等待几分钟，得到 `https://<user>.github.io/<repo>/`（支援页）
   和 `https://<user>.github.io/<repo>/privacy.html`。

### Cloudflare Pages / Vercel / Netlify

新建项目，构建命令留空，输出目录填 `site`，直接部署即可。

### 任意静态服务器

把 `site/` 里的三个文件上传到同一目录即可，不需要 PHP、数据库或构建步骤。

## 填回 App Store Connect

| 字段 | 值 |
| --- | --- |
| 隐私政策网址 | `https://<你的域名>/privacy.html` |
| 支援网址 | `https://<你的域名>/` |

如果希望 App 内也能打开这两页，把网址填进 `EarthOnline/SupportLinks.swift`
（目前未创建，1.1 再加），或直接在「设置 → 关于」里加两行链接。

## 本地预览

```bash
cd site
python3 -m http.server 8080
# 打开 http://localhost:8080
```

## 维护

政策或 FAQ 变更时，同时更新三处：

1. `PRIVACY.md` / `SUPPORT.md`（仓库内的纯文本版本）
2. `site/` 里对应的 HTML
3. 页面底部的「最后更新」日期
