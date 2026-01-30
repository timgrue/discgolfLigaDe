<script setup lang="ts">
import { ref } from 'vue'

interface Team {
  position: number
  name: string
  played: number
  wins: number
  draws: number
  losses: number
  points: number
}

const standings = ref<Team[]>([
  { position: 1, name: 'Disc Devils Berlin', played: 8, wins: 7, draws: 0, losses: 1, points: 21 },
  { position: 2, name: 'Frisbee Flyers', played: 8, wins: 6, draws: 1, losses: 1, points: 19 },
  { position: 3, name: 'Chain Seekers', played: 8, wins: 5, draws: 1, losses: 2, points: 16 },
  { position: 4, name: 'Berlin Baskets', played: 8, wins: 4, draws: 0, losses: 4, points: 12 },
  { position: 5, name: 'Spree Spinners', played: 8, wins: 2, draws: 2, losses: 4, points: 8 },
  { position: 6, name: 'Tiergarten Tossers', played: 8, wins: 1, draws: 1, losses: 6, points: 4 },
])
</script>

<template>
  <div class="team-standings">
    <h2>Team Standings</h2>
    <div class="table-container">
      <table>
        <thead>
          <tr>
            <th>Pos</th>
            <th>Team</th>
            <th>Played</th>
            <th>W</th>
            <th>D</th>
            <th>L</th>
            <th>Points</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="team in standings" :key="team.position">
            <td class="position">{{ team.position }}</td>
            <td class="team-name">{{ team.name }}</td>
            <td>{{ team.played }}</td>
            <td>{{ team.wins }}</td>
            <td>{{ team.draws }}</td>
            <td>{{ team.losses }}</td>
            <td class="points">{{ team.points }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style scoped>
.team-standings {
  width: 100%;
  margin: 0 auto;
}

h2 {
  color: var(--color-heading);
  margin-bottom: 1.5rem;
  font-size: 2rem;
}

.table-container {
  overflow-x: auto;
  background: var(--color-background-soft);
  border-radius: 8px;
  padding: 1rem;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th {
  background: var(--color-background-mute);
  padding: 1rem;
  text-align: left;
  font-weight: 600;
  border-bottom: 2px solid var(--color-border);
}

td {
  padding: 0.875rem 1rem;
  border-bottom: 1px solid var(--color-border-hover);
}

tr:last-child td {
  border-bottom: none;
}

tr:hover {
  background: var(--color-background-mute);
}

.position {
  font-weight: 700;
  width: 60px;
}

.team-name {
  font-weight: 600;
}

.points {
  font-weight: 700;
  color: var(--color-heading);
}

@media (max-width: 768px) {
  .team-standings {
    padding: 1rem;
  }

  th, td {
    padding: 0.5rem;
    font-size: 0.875rem;
  }
}
</style>
