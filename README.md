# 我的工作台 · 蓝胖子督促版

个人内容创作 + 业务流水线 + 自我督促的本地优先工作台。

## 开发

```bash
npm install
npm run dev
```

默认开发地址：`http://127.0.0.1:5174/`

构建：

```bash
npm run build
npm run preview
```

## 当前拆分

第一阶段只做工程拆分，不改产品逻辑：

- `index.html`：页面骨架
- `src/styles/workbench.css`：原内联样式
- `public/workbench.js`：原内联业务逻辑，作为 classic script 原样加载

原来的 inline `onclick` 和全局函数暂时保留，避免一次性改成模块作用域导致功能回归。因为 classic script 需要暴露全局函数，当前暂放在 `public/`，让 Vite 构建时原样复制。

## 数据与 AI

- 数据默认存浏览器本地 `localStorage`
- 左下角「导出 / 导入」可搬运数据
- AI 当前仍按原逻辑直连 Anthropic API，不可用时自动降级

代码不含任何个人数据，真实数据通过「导入」单独加载。

## 下一步建议

1. 把 `src/js/workbench.js` 按模块继续拆成 `store / gate / tasks / studio / radar / collect`。
2. 把 `localStorage` 升级为 IndexedDB / Dexie。
3. 把 AI 调用迁移到 Cloudflare Worker 代理，前端不直接暴露模型调用细节。
