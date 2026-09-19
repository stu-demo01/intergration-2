# 芒市文旅介绍

芒市文旅主题的静态展示网站，包含景点筛选、人气统计图表和三维导览三个模块。

## 功能模块

| 模块 | 文件 | 说明 |
| --- | --- | --- |
| 首页 | `index.html` | 景点、统计、三维三个入口卡片 |
| 景点介绍 | `index.html#study` | 按地理位置 / 开放时间下拉筛选景点（数据写死在 JS 数组） |
| 人气统计 | `index.html#stats` | Chart.js 柱状图，加载 `data.json` 展示热门景点与美食人气指数 |
| 三维导览 | `scene.html` | Three.js 场景：勐焕大金塔、树包塔、孔雀湖、傣家小楼，支持鼠标拖拽旋转、滚轮缩放 |
| 图表数据 | `data.json` | 统计页数据，包含 `spots` 和 `foods` 两个数组 |

## 运行说明

需通过本地 HTTP 服务器访问（统计页使用 `fetch` 读取 `data.json`，直接双击打开 html 会因浏览器安全限制失败）。

方式一：Python（推荐，无需安装依赖）

```bash
python -m http.server 8000
```

方式二：Node.js

```bash
npx serve .
```

启动后浏览器访问：

- 首页：http://localhost:8000/index.html
- 三维：http://localhost:8000/scene.html

也可使用 VS Code 的 Live Server 插件打开。三维页和图表依赖在线 CDN，首次访问需联网。

## 资源来源说明

本项目无本地图片、模型或第三方素材文件，所有资源来源如下：

- **Chart.js 4.x**：jsDelivr CDN，`https://cdn.jsdelivr.net/npm/chart.js`，用于人气统计柱状图
- **Three.js 0.160.0**（含 OrbitControls）：jsDelivr CDN，
  `https://cdn.jsdelivr.net/npm/three@0.160.0/build/three.module.js` 及 `examples/jsm/`，通过 importmap 引入
- **三维场景模型**：全部由 Three.js 基础几何体（圆柱、圆锥、方块、圆形）在代码中拼装，无外部模型或贴图
- **字体**：使用系统自带 "Microsoft YaHei"，无外部字体文件
- **景点与美食数据**：写死在 `index.html` 的 JS 数组和 `data.json` 中，为课程演示用示例数据

## 技术栈

原生 HTML / CSS / JavaScript，无需构建工具。
