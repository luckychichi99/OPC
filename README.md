
```markdown
# 投必盈 - 智能诊疗系统移动端 (OPC)

基于 [unibest](https://github.com/codercp/unibest) + [yudao-vue-pro](https://github.com/yudaocode/yudao-vue-pro) 构建的高性能移动端诊疗管理系统。

## 🌟 项目背景
本项目名为 **OPC (One-Point-Care)**，中文品牌名**“投必盈”**。它是一款集健康诊断、专业评估、品牌展示于一体的移动端应用，旨在通过数字化的方式连接患者与医疗服务。

## 🛠 技术架构
* **核心框架**：Vue 3 + uni-app (unibest 插件化架构)
* **构建工具**：Vite 5
* **样式处理**：UnoCSS (原子化 CSS)
* **语言支持**：TypeScript (全类型安全)
* **组件库**：uni-ui + 扩展自定义业务组件
* **路由管理**：集成拦截器，支持自动化路由配置与权限校验

## 📂 业务模块说明

```text
src/pages
├── index/                # 首页：功能矩阵(feature-cards)、科普知识、服务入口
├── diagnosis/            # 智能诊断：核心自测与诊断流程
├── evaluation/           # 评估模块：
│   └── result/           # 评估结果展示与数据分析
├── brand/                # 品牌展示：品牌介绍与关联服务
├── service/              # 服务中心：业务功能聚合页
└── profile/              # 个人中心：用户资料、诊疗记录与系统设置

```

## 🔧 开发环境配置

### 1. 获取代码与安装

```bash
git clone [https://github.com/luckychichi99/OPC.git](https://github.com/luckychichi99/OPC.git)
cd OPC
pnpm install

```

### 2. 环境变量配置

编辑根目录下的 `.env` 文件：

* `VITE_APP_TITLE`: 投必盈
* `VITE_SERVER_BASEURL`: 指向你的后端 API（如 `http://192.168.x.x:48080/admin-api`）
* `VITE_WX_APPID`: `wx63c280fe3248a3e7`

### 3. 运行与发布

* **开发环境 (微信小程序)**: `pnpm dev:mp-weixin`
* **生产环境 (微信小程序)**: `pnpm build:mp-weixin`
* **H5 预览**: `pnpm dev:h5`

## 🛡 核心逻辑

* **路由拦截**: 在 `src/router/interceptor.ts` 中实现了登录态校验及页面跳转逻辑。
* **加密传输**: 配合后端开启 AES 算法对 Request 和 Response 进行加密处理（见 `.env` 配置）。

## 📄 开源协议

本项目遵循 MIT 开源协议。

```

---

### 更新到 GitHub 的步骤：

1. **保存文件**：将上面的内容保存到你本地的 `README.md`。
2. **提交更新**：
   ```bash
   git add README.md
   git commit -m "docs: 重新编写符合投必盈业务逻辑的 README"

```

3. **推送到云端**：
```bash
git push -f origin main

```

