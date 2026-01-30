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
    <div class="schedule-header">
      <h2>League Schedule</h2>
      <span class="calendar-icon">📅</span>
    </div>

    <div class="schedule-container">
      <div v-for="match in matches.slice(0, 3)" :key="match.id" class="match-card">
        <div class="match-date">
          <div class="date-label">
            {{ formatDate(match.date).split(' ')[0] }}
          </div>
          <div class="date-value">
            {{ formatDate(match.date).split(' ').slice(1).join(' ') }}
          </div>
        </div>
        <div class="match-details">
          <div class="teams">
            <div class="team">{{ match.homeTeam }}</div>
            <div class="vs">vs.</div>
            <div class="team">{{ match.awayTeam }}</div>
          </div>
          <div class="course">
            <span class="course-icon">📍</span>
            <span>{{ match.course }} • {{ match.time }} Uhr</span>
          </div>
        </div>
      </div>

      <button class="full-schedule-btn">
        Full Season Schedule
      </button>
    </div>
  </div>
</template>

<style scoped>
.match-schedule {
  background: var(--color-background-soft);
  border: 1px solid var(--color-border);
  border-radius: 12px;
  padding: 1.5rem;
  max-width: 100%;
}

.schedule-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1.5rem;
}

.schedule-header h2 {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--text-white);
  margin: 0;
}

.calendar-icon {
  font-size: 1.5rem;
  opacity: 0.5;
}

.schedule-container {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.match-card {
  background: var(--bg-navy-light);
  border-radius: 8px;
  padding: 1rem;
  border: 1px solid var(--color-border);
  transition: all 0.3s ease;
  display: flex;
  gap: 1rem;
}

.match-card:hover {
  border-color: var(--color-border-hover);
  background: var(--color-background-mute);
}

.match-date {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-width: 60px;
  padding: 0.5rem;
  background: var(--color-background-soft);
  border-radius: 8px;
  border: 1px solid var(--color-border);
}

.date-label {
  font-size: 0.75rem;
  color: var(--accent-blue);
  font-weight: 600;
  text-transform: uppercase;
}

.date-value {
  font-size: 1rem;
  font-weight: 700;
  color: var(--text-white);
  margin-top: 0.25rem;
}

.match-details {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  flex: 1;
}

.teams {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.team {
  font-weight: 600;
  font-size: 0.875rem;
  color: var(--text-white);
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.vs {
  color: var(--text-gray-muted);
  font-size: 0.75rem;
  font-weight: 600;
}

.course {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.75rem;
  color: var(--text-gray-medium);
}

.course-icon {
  font-size: 0.875rem;
}

.full-schedule-btn {
  width: 100%;
  padding: 0.875rem;
  background: transparent;
  border: 1px solid var(--accent-blue);
  color: var(--accent-blue);
  border-radius: 8px;
  font-size: 0.875rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  margin-top: 0.5rem;
}

.full-schedule-btn:hover {
  background: var(--accent-blue);
  color: white;
  transform: translateY(-1px);
}

@media (max-width: 768px) {
  .match-schedule {
    padding: 1rem;
  }

  .match-card {
    flex-direction: column;
  }

  .match-date {
    flex-direction: row;
    justify-content: space-between;
    width: 100%;
    min-width: auto;
  }

  .team {
    font-size: 0.8rem;
  }
}
</style>
