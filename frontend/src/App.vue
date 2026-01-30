<script setup lang="ts">
import { RouterView } from 'vue-router'
import NavBar from './components/NavBar.vue'
</script>

<template>
  <div id="app">
    <NavBar />
    <RouterView />
    <footer>
      <div class="footer-content">
        <div class="footer-links">
          <a href="#">Terms</a>
          <a href="#">Privacy</a>
          <a href="#">Help Center</a>
        </div>
        <p>&copy; 2026 Discgolfliga.de. Alle Rechte vorbehalten.</p>
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

footer {
  margin-top: auto;
  background: var(--color-background);
  border-top: 1px solid var(--color-border);
  padding: 2rem;
}

.footer-content {
  max-width: 1400px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
}

.footer-links {
  display: flex;
  gap: 2rem;
}

.footer-links a {
  color: var(--text-gray-medium);
  text-decoration: none;
  font-size: 0.875rem;
  transition: color 0.3s ease;
}

.footer-links a:hover {
  color: var(--text-white);
}

.footer-content p {
  font-size: 0.875rem;
  color: var(--text-gray-muted);
  margin: 0;
}

@media (max-width: 768px) {
  .footer-links {
    flex-direction: column;
    gap: 1rem;
    text-align: center;
  }
}
</style>
