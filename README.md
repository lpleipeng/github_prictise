# Vue待办事项应用

一个使用Vue 3和Vite构建的简单待办事项(Todo)应用。

## 功能特点

- 添加新的待办事项
- 标记待办事项为已完成
- 删除待办事项
- 显示待办事项统计信息
- 响应式设计，适配不同设备

## 技术栈

- Vue 3 (Composition API)
- Vite
- CSS (无需额外UI库)

## 本地开发

### 安装依赖

```bash
npm install
```

### 启动开发服务器

```bash
npm run dev
```

### 构建生产版本

```bash
npm run build
```

### 预览生产构建

```bash
npm run preview
```

## 项目结构

```
/src
  /assets        # 静态资源
  /components    # Vue组件
    TodoList.vue # 待办事项列表组件
  App.vue        # 主应用组件
  main.js        # 应用入口
  style.css      # 全局样式
```

## 许可证

MIT
