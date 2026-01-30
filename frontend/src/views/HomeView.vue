<script setup lang="ts">
import TeamStandings from '../components/TeamStandings.vue'
import MatchSchedule from '../components/MatchSchedule.vue'
import CourseSpotlight from '../components/CourseSpotlight.vue'
</script>

<template>
  <main>
    <div class="hero">
      <h1>Berliner Discgolf Liga</h1>
      <p>Experience the excitement of competitive disc golf in Berlin</p>
    </div>
    <TeamStandings />
    <MatchSchedule />
    <CourseSpotlight />
  </main>
</template>

<style scoped>
.hero {
  text-align: center;
  padding: 4rem 2rem 2rem;
  background: linear-gradient(135deg, var(--color-background-soft), var(--color-background-mute));
  margin-bottom: 2rem;
}

.hero h1 {
  font-size: 3rem;
  color: var(--color-heading);
  margin-bottom: 1rem;
  font-weight: 700;
}

.hero p {
  font-size: 1.25rem;
  color: var(--color-text);
}

@media (max-width: 768px) {
  .hero {
    padding: 2rem 1rem 1rem;
  }

  .hero h1 {
    font-size: 2rem;
  }

  .hero p {
    font-size: 1rem;
  }
}
</style>
