# 📝 Vue 3 + Element Plus Todo List

一个基于 Vue 3 + Element Plus 的美观、响应式的 Todo List 应用，支持任务增删、过滤、勾选完成、持久化存储，以及拖拽排序功能。最终部署在 GitHub Pages 上，方便展示和访问。

## 🚀 项目预览

👉 在线地址：[https://cao818.github.io/vue-todo-app](https://cao818.github.io/vue-todo-app/)

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
vue-todo-app/                # 项目根目录
├── public/                  # 静态资源目录（favicon、static files）
├── src/
│   ├── assets/              # 图片、样式、图标等
│   ├── components/          # 可复用组件（如 Todolist.vue和counter.vue 等）
│   ├── App.vue              # 根组件，包含 Todo 核心交互逻辑
│   ├── main.js              # 项目入口，初始化 Vue + Element Plus、图标等
├── .gitignore               # Git 忽略配置
├── package.json             # 项目配置与依赖列表
├── vite.config.js           # Vite 构建和部署配置
├── README.md                # 项目说明文档


# 克隆项目
git clone https://github.com/cao818/vue-todo-app.git

cd vue-todo-app

# 安装依赖
npm install

# 启动开发服务器
npm run dev
