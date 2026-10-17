# FFEE Cover Design

免费在线封面制作工具，支持全球主流社交平台及中国平台尺寸预设，无需注册即可使用，一键导出高清无水印图片。

> Free online cover maker for Twitter, LinkedIn, Instagram, TikTok, YouTube, Xiaohongshu, WeChat, Bilibili, Douyin and Zhihu. No signup required, generate HD covers in one click.

---

## ✨ 功能特性

- **多平台尺寸预设** — 内置 30+ 平台尺寸模板，覆盖 Twitter/X、LinkedIn、Facebook、Instagram、TikTok、Pinterest、YouTube、Vimeo、Twitch、Podcast 等全球平台，以及小红书、微信、Bilibili、抖音、知乎等中国平台。
- **自定义尺寸** — 支持输入任意宽高（100–5000px），满足特殊需求。
- **快捷比例** — 内置 16:5、16:9、4:3、1:1、9:16、4:5、3:2、2:3、3:4、1.91:1、2:1、21:9、16:10 等多种常用比例。
- **批量导出** — 一次选择多个平台，一键导出全部适配尺寸图片。
- **免费图库** — 内置 Unsplash 免费商用图库和 Bing 每日壁纸（仅限个人使用）。
- **本地图片上传** — 支持上传自己的图片作为封面背景。
- **可拖拽文字** — 标题与副标题可自由拖动，支持字号、颜色、字体、对齐方式、位置调整。
- **背景遮罩** — 多种透明度遮罩预设，提升文字可读性。
- **无需注册** — 完全免费，打开即用，导出无水印。
- **多语言界面** — 支持 English、中文、Français、Deutsch 切换（当前页面语言为英文）。
- **纯前端处理** — 所有图片处理在浏览器本地完成，不上传服务器，保护隐私。

---

## 🔌 外部服务与依赖

本项目为单文件纯前端应用，但依赖以下**外部服务**。部署前请务必了解每一项的作用、调用方式及注意事项。

| 服务 | 类型 | 作用 | 调用方式 | 是否必需 | 注意事项 |
|------|------|------|----------|----------|----------|
| **html2canvas** | JS 库（CDN） | 将 DOM 画布渲染为 Canvas，用于导出 PNG 图片 | `<script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js">` | ✅ 必需 | 导出功能完全依赖它；若 CDN 被墙或加载失败，点击下载会提示 `html2canvas not loaded`。可自行下载后改为本地引用。 |
| **Microsoft Clarity** | 分析脚本（CDN） | 匿名用户行为分析（点击、滚动、热图等） | 页面 `<head>` 内联脚本，`t.src="https://www.clarity.ms/tag/yv3wfphb08"` | ⭕ 可选 | 项目 ID `yv3wfphb08` 是原站（ffee.me）的，**部署到自己的域名时请替换为你自己的 Clarity 项目 ID**，或直接删除该脚本以保护访客隐私。 |
| **Unsplash 图片** | 图片 API（直链） | 内置免费商用图库 | `https://images.unsplash.com/photo-xxx?w=400` 直链 | ⭕ 可选 | 图片通过 `images.unsplash.com` 直链加载，无需 API Key。遵循 [Unsplash License](https://unsplash.com/license)，可免费商用。若图片失效，可在 `unsplashImages` 数组中替换 URL。 |
| **Bing 每日壁纸 API** | 第三方 API（`bing.biturl.top`） | 获取 Bing 每日壁纸作为背景图 | `fetch("https://bing.biturl.top/?resolution=1920&format=json&index=0&mkt=en-US")` | ⭕ 可选 | 该 API 为**第三方非官方服务**，稳定性无保证，可能随时失效或限流。返回的壁纸**仅限个人使用**，禁止商用或二次上传。若失效可替换为其他壁纸 API 或移除 Bing 选项。 |
| **ffee.me Logo** | 图片（直链） | 顶部工具栏品牌图标 | `https://ffee.me/logo.svg` | ⭕ 可选 | 指向原站资源。部署到自己的站点时建议替换为自己的 Logo（本地或自有 CDN），避免依赖他人域名。 |
| **Google AdSense** | 广告位（占位） | 页面中的两处广告槽位（Canvas 下方 728×90、底部 728×90） | 当前仅为 HTML 占位 `<div class="ad-slot">`，**未加载真实广告脚本** | ⭕ 可选 | 如需启用广告，需自行申请 AdSense 账号并插入官方 `<ins class="adsbygoogle">` 代码；不启用则保留占位或直接删除。 |

> ⚠️ **部署到自己的域名前，请检查以上每一项**：至少替换 Clarity 项目 ID 与 ffee.me Logo；如不需要 Bing 壁纸或广告位，可直接删除对应代码以简化依赖。

---

## 🚀 快速开始

### 直接使用

直接在浏览器中打开 `index.html` 即可使用（需联网加载 html2canvas 和图库图片）。

links:https://ffee.me/cover-design/
