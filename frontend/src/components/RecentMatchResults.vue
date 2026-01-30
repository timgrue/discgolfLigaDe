<script setup lang="ts">
interface MatchResult {
  team1: string
  team1Abbr: string
  team1Score: number
  team2: string
  team2Abbr: string
  team2Score: number
  status: string
  round: string
}

const matches: MatchResult[] = [
  {
    team1: 'Early Birdies Berlin',
    team1Abbr: 'EB',
    team1Score: 54,
    team2: 'Lichterfelder Allstars',
    team2Abbr: 'LA',
    team2Score: 58,
    status: 'FINAL',
    round: 'Round 12 • Oct 17'
  },
  {
    team1: 'Empor Berlin',
    team1Abbr: 'EB',
    team1Score: 61,
    team2: 'Pepperdisc',
    team2Abbr: 'PD',
    team2Score: 52,
    status: 'FINAL',
    round: 'Round 12 • Oct 17'
  }
]
</script>

<template>
  <div class="recent-matches">
    <div class="section-header">
      <h2>Recent Match Results</h2>
      <span class="round-info">{{ matches[0]?.round }}</span>
    </div>

    <div class="matches-grid">
      <div v-for="(match, index) in matches" :key="index" class="match-card">
        <div class="team team-1">
          <span class="team-abbr">{{ match.team1Abbr }}</span>
          <span class="team-name">{{ match.team1 }}</span>
        </div>

        <div class="score-section">
          <div class="score">
            <span class="score-value">{{ match.team1Score }}</span>
            <span class="vs">VS</span>
            <span class="score-value">{{ match.team2Score }}</span>
          </div>
          <span class="status">{{ match.status }}</span>
        </div>

        <div class="team team-2">
          <span class="team-abbr">{{ match.team2Abbr }}</span>
          <span class="team-name">{{ match.team2 }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.recent-matches {
  background: var(--color-background);
}

.section-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1.5rem;
}

.section-header h2 {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--text-white);
  margin: 0;
}

.round-info {
  font-size: 0.875rem;
  color: var(--text-gray-medium);
}

.matches-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.5rem;
}

.match-card {
  background: var(--color-background-soft);
  border: 1px solid var(--color-border);
  border-radius: 12px;
  padding: 1.5rem;
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  gap: 1.5rem;
  align-items: center;
  transition: all 0.3s ease;
}

.match-card:hover {
  border-color: var(--color-border-hover);
}

.team {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.team-1 {
  align-items: flex-start;
}

.team-2 {
  align-items: flex-end;
}

.team-abbr {
  display: inline-block;
  padding: 0.25rem 0.75rem;
  background: var(--color-background-mute);
  color: var(--accent-blue);
  border-radius: 6px;
  font-weight: 700;
  font-size: 0.875rem;
}

.team-name {
  font-size: 0.875rem;
  color: var(--text-white);
  font-weight: 500;
}

.score-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
}

.score {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.score-value {
  font-size: 2rem;
  font-weight: 700;
  color: var(--text-white);
}

.vs {
  font-size: 0.75rem;
  color: var(--text-gray-muted);
  font-weight: 600;
}

.status {
  display: inline-block;
  padding: 0.25rem 0.75rem;
  background: rgba(0, 217, 163, 0.1);
  color: var(--accent-success);
  border-radius: 6px;
  font-size: 0.75rem;
  font-weight: 700;
}

@media (max-width: 768px) {
  .matches-grid {
    grid-template-columns: 1fr;
  }

  .match-card {
    grid-template-columns: 1fr;
    gap: 1rem;
    text-align: center;
  }

  .team-1,
  .team-2 {
    align-items: center;
  }
}
</style>
