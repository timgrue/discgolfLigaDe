<script setup lang="ts">
import StatCard from '../components/StatCard.vue'
import TeamStandings from '../components/TeamStandings.vue'
import MatchSchedule from '../components/MatchSchedule.vue'
import CourseSpotlight from '../components/CourseSpotlight.vue'
import RecentMatchResults from '../components/RecentMatchResults.vue'
</script>

<template>
  <main class="dashboard">
    <div class="container">
      <!-- Main Content Grid -->
      <div class="content-grid">
        <!-- Left Column - Standings and Results -->
        <div class="main-column">
          <!-- Stat Cards -->
          <div class="stats-grid">
            <StatCard title="Total Players" :value="124" subtitle="+6 this week" />
            <StatCard title="Weeks Remaining" :value="4" />
            <StatCard title="Next Round Date" value="Oct 24" />
          </div>
          <TeamStandings />
          <RecentMatchResults />
        </div>

        <!-- Right Sidebar - Schedule and Spotlight -->
        <div class="sidebar">
          <MatchSchedule />
          <CourseSpotlight />
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
.dashboard {
  background: var(--color-background);
  min-height: calc(100vh - 200px);
  padding: 2rem 0;
}

.container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 2rem;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
}

.content-grid {
  display: grid;
  grid-template-columns: 1fr 400px;
  gap: 2rem;
}

.main-column {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.sidebar {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

@media (max-width: 1200px) {
  .content-grid {
    grid-template-columns: 1fr 350px;
  }
}

@media (max-width: 1024px) {
  .content-grid {
    grid-template-columns: 1fr;
  }

  .sidebar {
    order: -1;
  }
}

@media (max-width: 768px) {
  .container {
    padding: 0 1rem;
  }

  .stats-grid {
    grid-template-columns: 1fr;
  }
}
</style>
