<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header class="app-header">
    <div class="menu-container">
      <nav>
        <RouterLink to="/" class="menu-item">Főoldal</RouterLink>&nbsp&nbsp
        <RouterLink to="/megjelenesek" class="menu-item">Megjelenések</RouterLink>&nbsp&nbsp
        <RouterLink to="/about" class="menu-item">Készítette</RouterLink>&nbsp&nbsp
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>

.app-header {
  background-color: #e60012;
  padding: 10px;
  text-align: center;
}

.menu-container {
  display: flex;
  justify-content: center;
}

.menu-item {
  background-color: #e60012;
  color: white;
  text-decoration: none;
  padding: 10px 15px;
  border-radius: 20px;
  margin: 0 10px;
  transition: background-color 0.3s ease;
}

.menu-item:hover {
  background-color: #ff4040;
}
</style>
