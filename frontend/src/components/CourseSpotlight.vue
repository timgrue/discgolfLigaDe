<script setup lang="ts">
import { ref } from 'vue'

interface Course {
  name: string
  location: string
  holes: number
  distance: string
  difficulty: string
  description: string
  nextMatch: {
    date: string
    teams: string
  }
  features: string[]
}

const course = ref<Course>({
  name: 'Tempelhofer Feld',
  location: 'Tempelhof-Schöneberg, Berlin',
  holes: 18,
  distance: '3.2 km',
  difficulty: 'Intermediate',
  description:
    'The iconic Tempelhofer Feld disc golf course offers a unique playing experience on the former airport grounds. With wide open fairways and challenging wind conditions, this course tests both distance and precision.',
  nextMatch: {
    date: 'February 5, 2026',
    teams: 'Disc Devils Berlin vs Chain Seekers',
  },
  features: [
    'Open fairways with strategic obstacles',
    'Challenging wind conditions',
    'Historic location',
    'Well-maintained baskets',
    'Spectator-friendly layout',
  ],
})
</script>

<template>
  <div class="course-spotlight">
    <h2>Course Spotlight</h2>
    <div class="spotlight-card">
      <div class="course-header">
        <h3>{{ course.name }}</h3>
        <div class="location">
          <span class="location-icon">📍</span>
          {{ course.location }}
        </div>
      </div>

      <div class="course-info">
        <div class="info-grid">
          <div class="info-item">
            <span class="label">Holes:</span>
            <span class="value">{{ course.holes }}</span>
          </div>
          <div class="info-item">
            <span class="label">Distance:</span>
            <span class="value">{{ course.distance }}</span>
          </div>
          <div class="info-item">
            <span class="label">Difficulty:</span>
            <span class="value">{{ course.difficulty }}</span>
          </div>
        </div>

        <div class="course-description">
          <p>{{ course.description }}</p>
        </div>

        <div class="features">
          <h4>Course Features</h4>
          <ul>
            <li v-for="(feature, index) in course.features" :key="index">
              <span class="bullet">🥏</span>
              {{ feature }}
            </li>
          </ul>
        </div>

        <div class="next-match">
          <div class="next-match-header">
            <span class="icon">🏆</span>
            <span class="label">Next Match at This Course</span>
          </div>
          <div class="match-info">
            <div class="match-date">{{ course.nextMatch.date }}</div>
            <div class="match-teams">{{ course.nextMatch.teams }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.course-spotlight {
  max-width: 900px;
  margin: 0 auto;
}

h2 {
  color: var(--color-heading);
  margin-bottom: 1.5rem;
  font-size: 2rem;
}

.spotlight-card {
  background: var(--color-background-soft);
  border-radius: 12px;
  padding: 2rem;
  border: 2px solid var(--color-border);
}

.course-header {
  margin-bottom: 2rem;
  padding-bottom: 1.5rem;
  border-bottom: 2px solid var(--color-border);
}

.course-header h3 {
  font-size: 2rem;
  color: var(--color-heading);
  margin-bottom: 0.5rem;
}

.location {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: var(--color-text);
  font-size: 1.1rem;
}

.location-icon {
  font-size: 1.2rem;
}

.info-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 1.5rem;
  margin-bottom: 2rem;
}

.info-item {
  background: var(--color-background-mute);
  padding: 1rem;
  border-radius: 8px;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.info-item .label {
  font-size: 0.875rem;
  color: var(--color-text);
  font-weight: 500;
}

.info-item .value {
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--color-heading);
}

.course-description {
  margin-bottom: 2rem;
}

.course-description p {
  line-height: 1.7;
  color: var(--color-text);
  font-size: 1.05rem;
}

.features {
  margin-bottom: 2rem;
}

.features h4 {
  color: var(--color-heading);
  margin-bottom: 1rem;
  font-size: 1.25rem;
}

.features ul {
  list-style: none;
  padding: 0;
}

.features li {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.5rem 0;
  color: var(--color-text);
}

.bullet {
  font-size: 1.25rem;
}

.next-match {
  background: linear-gradient(135deg, rgba(72, 187, 120, 0.1), rgba(56, 161, 105, 0.1));
  border-radius: 8px;
  padding: 1.5rem;
  border-left: 4px solid #48bb78;
}

.next-match-header {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  margin-bottom: 1rem;
  font-weight: 600;
  color: var(--color-heading);
}

.next-match-header .icon {
  font-size: 1.5rem;
}

.match-info {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.match-date {
  font-weight: 700;
  font-size: 1.1rem;
  color: var(--color-heading);
}

.match-teams {
  font-size: 1rem;
  color: var(--color-text);
}

@media (max-width: 768px) {
  .course-spotlight {
    padding: 1rem;
  }

  .spotlight-card {
    padding: 1.5rem;
  }

  .course-header h3 {
    font-size: 1.5rem;
  }

  .info-grid {
    grid-template-columns: 1fr;
  }
}
</style>
