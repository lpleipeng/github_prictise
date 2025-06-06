<script setup>
import TodoList from './components/TodoList.vue'
</script>

<template>
  <div class="app-container">
    <header>
      <div class="logo-container">
        <a href="https://vuejs.org/" target="_blank">
          <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
        </a>
      </div>
      <h1>Vue待办事项应用</h1>
    </header>
    
    <main>
      <TodoList />
    </main>
    
    <footer>
      <p>使用Vue 3 + Vite构建 | <a href="https://github.com/lpleipeng/github_prictise" target="_blank">GitHub仓库</a></p>
    </footer>
  </div>
</template>

<style scoped>
.app-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

header {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 2rem;
  flex-direction: column;
}

.logo-container {
  margin-bottom: 1rem;
}

.logo {
  height: 4em;
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

h1 {
  font-size: 2.5rem;
  color: #42b883;
  margin: 0;
}

main {
  flex: 1;
}

footer {
  margin-top: 2rem;
  text-align: center;
  font-size: 0.9rem;
  color: #888;
}

footer a {
  color: #42b883;
  text-decoration: none;
}

footer a:hover {
  text-decoration: underline;
}
</style>
