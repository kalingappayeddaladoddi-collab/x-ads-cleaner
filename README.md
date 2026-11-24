# 🧹 Browser Helper — X 去广告脚本

装一次，刷 X 时再也不会看到推广。

不是那种“先让广告闪出来再盖住”的 CSS 遮挡流。本脚本在广告 **进入浏览器之前** 就动手 —— GraphQL 响应刚回来、React 还没渲染，推广条目已经从 JSON 数据里被摘除。所以：

- ❌ 不闪屏（广告从没画出来过）
- ❌ 不留白（没有“删完 DOM 塌陷”的空洞）
- ❌ 不卡（普通响应先过字符串闸门，不含广告特征的直接放行，**零 JSON.parse 开销**）
- ✅ 时间线、推荐栏、趋势、搜索里的推广一网打尽

## ✨ 特性

- **数据层去广告**：在 XHR / Fetch 响应层拦截，推广推文、推广账号、推广趋势在渲染前被掐死
- **多语言覆盖**：`Promoted / Sponsored / 已推广 / 廣告 / Anzeigen / プロモーション / 홍보 / 公開宣传`…… 全球语言版本都能识别
- **三层防线**：网络层拦截 → 流式响应探测 → DOM 安全区兜底（只碰 `UserCell` / `trend`，绝不误伤正文）
- **右下悬浮按钮**：一键开关，实时显示“已摘除 N 条”，开着关着一目了然
- **快捷键**：`Ctrl + Alt + A` 随时切换，开关状态自动记忆，重启浏览器保持
- **极致轻量**：无面板、无弹窗、无依赖，装完 X 就变干净了
- **已混淆发布**：代码经过字符串加密 + 十六进制标识符混淆， greppable 标识符清零

## 🚀 使用

1. 浏览器安装 [Tampermonkey](https://www.tampermonkey.net/) 或 Violentmonkey（推荐 **Firefox**，兼容最佳）
2. 复制到 <download 链接>
3. 打开 x.com，右下角出现 🧹 按钮即生效
4. 按钮显示「开 已摘除 N」= 工作中；点一下即关

> 强刷一次页面（`Ctrl+Shift+R`）确保脚本在页面加载前注入。

## 🌐 支持范围

- 桌面：Chrome / Edge / Brave / Opera / Firefox / Safari（Safari 需 Userscripts 扩展）
- 手机：Firefox for Android 最佳
- 站点：`x.com` / `twitter.com` / `mobile.twitter.com` / `pro.x.com`

## 🧪 控制台诊断（进阶）

```js
window.xad.toggle()   // 开关
window.xad.debug()    // 打开调试日志
window.xad.diag()     // 一行输出 拦截/命中/删除 统计
```

## 📄 License

MIT
