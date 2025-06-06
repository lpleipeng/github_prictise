<script setup>
import { ref } from 'vue';

// 待办事项列表
const todos = ref([
  { id: 1, text: '学习Vue 3基础', completed: true },
  { id: 2, text: '完成待办事项应用', completed: false },
  { id: 3, text: '部署到GitHub Pages', completed: false }
]);

// 新待办事项输入
const newTodo = ref('');

// 添加新待办事项
const addTodo = () => {
  if (newTodo.value.trim()) {
    todos.value.push({
      id: Date.now(),
      text: newTodo.value.trim(),
      completed: false
    });
    newTodo.value = '';
  }
};

// 删除待办事项
const removeTodo = (id) => {
  todos.value = todos.value.filter(todo => todo.id !== id);
};

// 切换待办事项完成状态
const toggleComplete = (id) => {
  const todo = todos.value.find(todo => todo.id === id);
  if (todo) {
    todo.completed = !todo.completed;
  }
};
</script>

<template>
  <div class="todo-container">
    <h2>待办事项列表</h2>
    
    <!-- 添加新待办事项 -->
    <div class="add-todo">
      <input 
        type="text" 
        v-model="newTodo" 
        placeholder="添加新的待办事项..."
        @keyup.enter="addTodo"
      />
      <button @click="addTodo">添加</button>
    </div>
    
    <!-- 待办事项列表 -->
    <ul class="todo-list">
      <li v-for="todo in todos" :key="todo.id" :class="{ completed: todo.completed }">
        <div class="todo-item">
          <input 
            type="checkbox" 
            :checked="todo.completed"
            @change="toggleComplete(todo.id)"
          />
          <span>{{ todo.text }}</span>
          <button class="delete-btn" @click="removeTodo(todo.id)">删除</button>
        </div>
      </li>
    </ul>
    
    <!-- 统计信息 -->
    <div class="todo-stats">
      <p>总计: {{ todos.length }} | 已完成: {{ todos.filter(t => t.completed).length }}</p>
    </div>
  </div>
</template>

<style scoped>
.todo-container {
  max-width: 500px;
  margin: 0 auto;
  padding: 20px;
  background-color: #2c3e50;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

h2 {
  color: #ecf0f1;
  text-align: center;
  margin-bottom: 20px;
}

.add-todo {
  display: flex;
  margin-bottom: 20px;
}

input[type="text"] {
  flex: 1;
  padding: 10px;
  border: none;
  border-radius: 4px 0 0 4px;
  font-size: 16px;
}

.add-todo button {
  padding: 10px 15px;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 0 4px 4px 0;
  cursor: pointer;
  font-size: 16px;
}

.add-todo button:hover {
  background-color: #3aa876;
}

.todo-list {
  list-style-type: none;
  padding: 0;
  margin: 0;
}

.todo-item {
  display: flex;
  align-items: center;
  padding: 10px;
  background-color: #34495e;
  margin-bottom: 8px;
  border-radius: 4px;
  transition: all 0.3s ease;
}

.todo-item:hover {
  background-color: #3d5a74;
}

.todo-item input[type="checkbox"] {
  margin-right: 10px;
}

.todo-item span {
  flex: 1;
  color: #ecf0f1;
}

.completed .todo-item span {
  text-decoration: line-through;
  color: #95a5a6;
}

.delete-btn {
  background-color: #e74c3c;
  color: white;
  border: none;
  border-radius: 4px;
  padding: 5px 10px;
  cursor: pointer;
  font-size: 14px;
}

.delete-btn:hover {
  background-color: #c0392b;
}

.todo-stats {
  margin-top: 20px;
  text-align: center;
  color: #bdc3c7;
  font-size: 14px;
}
</style>