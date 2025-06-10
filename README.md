# 📝 Vue 3 + Element Plus Todo List

一个基于 Vue 3 + Element Plus 的美观、响应式的 Todo List 应用，支持任务增删、过滤、勾选完成、持久化存储，以及拖拽排序功能。最终部署在 GitHub Pages 上，方便展示和访问。

## 🚀 项目预览

👉 在线地址：[https://cao818.github.io/vue-todo-app](https://cao818.github.io/vue-todo-app/)](https://your-username.github.io/vue-todo-app)

## ✨ 功能特性

- ✅ 添加新任务（支持回车快捷键）
- ✅ 勾选任务完成/未完成状态
- ✅ 删除任务（含图标按钮）
- ✅ 任务拖拽排序（基于 `vuedraggable`）
- ✅ 三种筛选视图（全部、未完成、已完成）
- ✅ 本地 `localStorage` 持久化存储
- ✅ 响应式布局，适配移动端
- ✅ Element Plus UI + 图标支持

## 📦 技术栈

- [Vue 3](https://vuejs.org/)
- [Element Plus](https://element-plus.org/)
- [vuedraggable](https://github.com/SortableJS/vue.draggable.next)
- [GitHub Pages](https://pages.github.com/)

## 📂 项目结构

```bash
.
├── public/                   # 公共资源
├── src/
│   ├── App.vue               # 主组件，Todo List 页面
│   ├── main.js               # 应用入口
├── .gitignore
├── index.html
├── package.json
├── vite.config.js            # Vite 配置文件（包含部署路径配置）
└── README.md

# 克隆项目
git clone https://github.com/your-username/vue-todo-app.git
cd vue-todo-app

# 安装依赖
npm install

# 启动开发服务器
npm run dev
