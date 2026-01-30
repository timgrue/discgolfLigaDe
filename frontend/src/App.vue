<script setup lang="ts">
import { RouterView } from 'vue-router'
</script>

<template>
  <div id="app">
    <header>
      <div class="header-content">
        <div class="logo">
          <span class="disc-icon">🥏</span>
          <h1>Berliner Discgolf Liga</h1>
        </div>
      </div>
    </header>

    <RouterView />

    <footer>
      <div class="footer-content">
        <p>&copy; 2026 Berliner Discgolf Liga. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>

<style scoped>
#app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

header {
  background: var(--color-background-soft);
  border-bottom: 2px solid var(--color-border);
  position: sticky;
  top: 0;
  z-index: 100;
}

.header-content {
  max-width: 1400px;
  margin: 0 auto;
  padding: 1rem 2rem;
}

.logo {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.disc-icon {
  font-size: 2.5rem;
}

.logo h1 {
  font-size: 1.75rem;
  color: var(--color-heading);
  font-weight: 700;
  margin: 0;
}

footer {
  margin-top: auto;
  background: var(--color-background-soft);
  border-top: 2px solid var(--color-border);
  padding: 2rem;
}

.footer-content {
  max-width: 1400px;
  margin: 0 auto;
  text-align: center;
  color: var(--color-text);
}

@media (max-width: 768px) {
  .header-content {
    padding: 1rem;
  }

  .logo h1 {
    font-size: 1.25rem;
  }

  .disc-icon {
    font-size: 2rem;
  }
}
</style>
