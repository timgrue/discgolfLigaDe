<script setup lang="ts">
import { ref } from 'vue'

interface Match {
  id: number
  date: string
  time: string
  homeTeam: string
  awayTeam: string
  course: string
  status: 'upcoming' | 'live' | 'completed'
}

const matches = ref<Match[]>([
  {
    id: 1,
    date: '2026-02-05',
    time: '14:00',
    homeTeam: 'Disc Devils Berlin',
    awayTeam: 'Chain Seekers',
    course: 'Tempelhofer Feld',
    status: 'upcoming',
  },
  {
    id: 2,
    date: '2026-02-05',
    time: '16:00',
    homeTeam: 'Frisbee Flyers',
    awayTeam: 'Berlin Baskets',
    course: 'Volkspark Friedrichshain',
    status: 'upcoming',
  },
  {
    id: 3,
    date: '2026-02-12',
    time: '14:00',
    homeTeam: 'Spree Spinners',
    awayTeam: 'Tiergarten Tossers',
    course: 'Tiergarten Course',
    status: 'upcoming',
  },
  {
    id: 4,
    date: '2026-02-12',
    time: '16:00',
    homeTeam: 'Chain Seekers',
    awayTeam: 'Frisbee Flyers',
    course: 'Mauerpark',
    status: 'upcoming',
  },
])

function formatDate(dateString: string): string {
  const date = new Date(dateString)
  return date.toLocaleDateString('en-US', { weekday: 'short', month: 'short', day: 'numeric' })
}
</script>

<template>
  <div class="match-schedule">
    <h2>Upcoming Matches</h2>
    <div class="schedule-container">
      <div v-for="match in matches" :key="match.id" class="match-card">
        <div class="match-date">
          <div class="date">{{ formatDate(match.date) }}</div>
          <div class="time">{{ match.time }}</div>
        </div>
        <div class="match-details">
          <div class="teams">
            <div class="team home">{{ match.homeTeam }}</div>
            <div class="vs">vs</div>
            <div class="team away">{{ match.awayTeam }}</div>
          </div>
          <div class="course">
            <span class="course-icon">📍</span>
            {{ match.course }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.match-schedule {
  padding: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

h2 {
  color: var(--color-heading);
  margin-bottom: 1.5rem;
  font-size: 2rem;
}

.schedule-container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 1.5rem;
}

.match-card {
  background: var(--color-background-soft);
  border-radius: 12px;
  padding: 1.5rem;
  border: 2px solid var(--color-border);
  transition: all 0.3s ease;
}

.match-card:hover {
  border-color: var(--color-border-hover);
  transform: translateY(-4px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
}

.match-date {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
  padding-bottom: 1rem;
  border-bottom: 1px solid var(--color-border);
}

.date {
  font-weight: 600;
  font-size: 1rem;
  color: var(--color-heading);
}

.time {
  font-weight: 500;
  color: var(--color-text);
  background: var(--color-background-mute);
  padding: 0.25rem 0.75rem;
  border-radius: 4px;
}

.match-details {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.teams {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 0.5rem;
}

.team {
  flex: 1;
  font-weight: 600;
  font-size: 0.95rem;
}

.team.home {
  text-align: right;
}

.team.away {
  text-align: left;
}

.vs {
  padding: 0 0.5rem;
  font-weight: 700;
  color: var(--color-text);
  font-size: 0.875rem;
}

.course {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.875rem;
  color: var(--color-text);
  background: var(--color-background-mute);
  padding: 0.5rem 0.75rem;
  border-radius: 6px;
}

.course-icon {
  font-size: 1rem;
}

@media (max-width: 768px) {
  .match-schedule {
    padding: 1rem;
  }

  .schedule-container {
    grid-template-columns: 1fr;
  }
}
</style>
