# 3D Interactive Portfolio

个人 vibe coding 作品：以 AI 辅助编码方式完成的实验性单页作品集。重点在于把 Shader 背景、流体光标、滚动叙事、拖拽画廊与物理磁吸等交互组合成一套完整的视觉体验，而不是实现业务逻辑。

纯静态前端项目，无后端、无接口、无数据收集；页面内链接均为站内锚点，不包含下载入口、联系方式或站外跳转。

## 页面内容

页面由 `src/App.tsx` 按顺序组合：

| 区块 | 说明 |
| --- | --- |
| Hero | 超大渐变标题、锚点导航、磁吸悬浮肖像 |
| Dome Gallery | 可拖拽的穹顶式图片画廊 |
| About | 滚动逐字显现的简介与装饰图视差 |
| Ability | 能力条目交错入场 |
| Projects | Framer Motion 粘性堆叠项目卡片 |

全局叠加效果：动态 Silk 背景、SplashCursor 流体光标，以及由 GSAP / ScrollTrigger 驱动的滚动动画。仓库中还保留了若干未挂载的可复用特效组件（Three.js / WebGL 实验、玻璃拟态、文字动效等），可按需引入。

## 技术栈

- Vite + React 18 + TypeScript
- Tailwind CSS 3
- GSAP / ScrollTrigger / `@gsap/react`（滚动动画）
- Framer Motion（组件级动效与卡片堆叠）
- Three.js / `@react-three/fiber` / drei（特效组件）
- `@use-gesture/react`（拖拽手势）

## 本地运行

建议使用 Node.js 20+（CI 使用 Node 20）。

```bash
npm install
npm run dev
```

`vite.config.ts` 中配置了 `base: '/'`，因此本地访问地址为 `http://localhost:5173/`。项目部署在域名根路径（GitHub Pages 用户站点与 EdgeOne Makers），若改为部署到子路径，需同步修改 `base`，否则静态资源路径会不匹配。

## 构建与部署

```bash
npm run build     # 输出 dist/
npm run preview   # 本地预览构建结果
npm run lint      # ESLint 检查
```

推送到 `main` 分支后，`.github/workflows/deploy.yml` 会自动执行 `npm ci`、`npm run build` 并发布到 GitHub Pages（需在仓库 Settings → Pages 中将来源设为 GitHub Actions）。用户站点地址为 `https://liangshengfu.github.io/`。

说明：`npm run lint` 目前会对部分历史动效组件报告既有 ESLint 错误，属项目历史遗留，不影响运行，`npm run build` 正常通过。字体 Kanit 通过 Google Fonts 加载，离线时回退到系统无衬线字体。

## 目录结构

```
src/
├── main.tsx          应用入口
├── App.tsx           页面区块组合与全局效果层
├── index.css         Tailwind 入口与全局样式
├── components/       页面区块 + 可复用动效组件
└── lib/              工具函数
public/
├── images/           静态图片资源
└── ...               favicon 等站点资源
```
