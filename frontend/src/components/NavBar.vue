<script setup lang="ts">
import { ref } from 'vue'

const searchQuery = ref('')
const isMenuOpen = ref(false)
</script>

<template>
  <header class="navbar">
    <div class="navbar-content">
      <div class="navbar-left">
        <div class="logo">
          <span class="disc-icon">🥏</span>
          <h1>Berliner Discgolf Liga</h1>
        </div>

        <div class="search-bar">
          <span class="search-icon">🔍</span>
          <input
            v-model="searchQuery"
            type="text"
            placeholder="Search League..."
            class="search-input"
          />
        </div>
      </div>

      <nav class="nav-links">
        <a href="#" class="nav-link active">Dashboard</a>
        <a href="#" class="nav-link">Standings</a>
        <a href="#" class="nav-link">Schedule</a>
        <a href="#" class="nav-link">Players</a>
      </nav>

      <div class="navbar-right">
        <button class="btn-primary">Log Score</button>
        <div class="user-avatar">
          <span>👤</span>
        </div>
      </div>

      <button class="mobile-menu-btn" @click="isMenuOpen = !isMenuOpen">
        ☰
      </button>
    </div>

    <nav v-if="isMenuOpen" class="mobile-nav">
      <a href="#" class="nav-link active">Dashboard</a>
      <a href="#" class="nav-link">Standings</a>
      <a href="#" class="nav-link">Schedule</a>
      <a href="#" class="nav-link">Players</a>
      <button class="btn-primary mobile-btn">Log Score</button>
    </nav>
  </header>
</template>

<style scoped>
.navbar {
  background: var(--color-background-soft);
  border-bottom: 1px solid var(--color-border);
  position: sticky;
  top: 0;
  z-index: 100;
}

.navbar-content {
  max-width: 1400px;
  margin: 0 auto;
  padding: 1rem 2rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 2rem;
}

.navbar-left {
  display: flex;
  align-items: center;
  gap: 2rem;
  flex: 1;
}

.logo {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  white-space: nowrap;
}

.disc-icon {
  font-size: 1.75rem;
}

.logo h1 {
  font-size: 1.25rem;
  color: var(--text-white);
  font-weight: 700;
  margin: 0;
}

.search-bar {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  background: var(--bg-navy-dark);
  border: 1px solid var(--color-border);
  border-radius: 8px;
  padding: 0.5rem 1rem;
  max-width: 300px;
  flex: 1;
}

.search-icon {
  font-size: 1rem;
  opacity: 0.5;
}

.search-input {
  background: transparent;
  border: none;
  outline: none;
  color: var(--text-white);
  font-size: 0.875rem;
  width: 100%;
}

.search-input::placeholder {
  color: var(--text-gray-muted);
}

.nav-links {
  display: flex;
  gap: 2rem;
  align-items: center;
}

.nav-link {
  color: var(--text-gray-medium);
  text-decoration: none;
  font-size: 0.875rem;
  font-weight: 500;
  transition: color 0.3s ease;
  white-space: nowrap;
}

.nav-link:hover {
  color: var(--text-white);
}

.nav-link.active {
  color: var(--accent-blue);
}

.navbar-right {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.btn-primary {
  background: var(--accent-blue);
  color: white;
  border: none;
  padding: 0.625rem 1.5rem;
  border-radius: 8px;
  font-size: 0.875rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  white-space: nowrap;
}

.btn-primary:hover {
  background: var(--accent-blue-hover);
  transform: translateY(-1px);
}

.user-avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: var(--color-background-mute);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.25rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.user-avatar:hover {
  background: var(--color-border-hover);
}

.mobile-menu-btn {
  display: none;
  background: transparent;
  border: none;
  color: var(--text-white);
  font-size: 1.5rem;
  cursor: pointer;
  padding: 0.5rem;
}

.mobile-nav {
  display: none;
  flex-direction: column;
  padding: 1rem 2rem;
  gap: 1rem;
  border-top: 1px solid var(--color-border);
}

.mobile-nav .nav-link {
  padding: 0.5rem 0;
}

.mobile-btn {
  width: 100%;
  margin-top: 0.5rem;
}

@media (max-width: 1024px) {
  .nav-links {
    gap: 1rem;
  }

  .search-bar {
    max-width: 200px;
  }
}

@media (max-width: 768px) {
  .navbar-content {
    padding: 1rem;
  }

  .search-bar,
  .nav-links,
  .navbar-right .btn-primary {
    display: none;
  }

  .mobile-menu-btn {
    display: block;
  }

  .mobile-nav {
    display: flex;
  }

  .logo h1 {
    font-size: 1rem;
  }

  .disc-icon {
    font-size: 1.5rem;
  }
}
</style>
