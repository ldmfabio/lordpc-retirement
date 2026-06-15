<script setup>
import { ref, onMounted } from 'vue'

const retirementDate = new Date('2026-08-01T00:00:00')
const daysRemaining = ref(0)
const retired = ref(false)

function updateCountdown() {
  const now = new Date()
  const diff = retirementDate - now

  retired.value = diff <= 0
  daysRemaining.value = Math.max(Math.ceil(diff / (1000 * 60 * 60 * 24)), 0)
}

onMounted(() => {
  updateCountdown()
  setInterval(updateCountdown, 1000 * 60 * 60)
})
</script>

<template>
  <main class="page">
    <section class="card">
      <div class="icon">🎓👑</div>

      <template v-if="!retired">
        <h1 class="lordpc">Lord PC</h1>

        <p class="subtitle">Countdown to Retirement</p>

        <p class="decree">
          By Royal Decree,<br />
          On the First Day of August<br />
          in the Year 2026,<br />
          Lord PC shall be relieved<br />
          of all academic duties.
        </p>

        <div class="days">{{ daysRemaining }}</div>

        <p class="remaining">days remaining</p>
      </template>

      <template v-else>
        <h1>Congratulations!</h1>

        <p class="decree">
          Lord PC has officially retired.
        </p>

        <p class="final">
          Long live Lord PC!
        </p>
      </template>
    </section>
  </main>
</template>

<style scoped>
.page {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #102542;
  color: #f8f1d8;
  font-family: Georgia, 'Times New Roman', serif;
  padding: 24px;
}

.card {
  max-width: 620px;
  width: 100%;
  text-align: center;
  border: 3px solid #d4af37;
  border-radius: 24px;
  padding: 48px 32px;
  background: #172f52;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.35);
}

.icon {
  font-size: 4rem;
  margin-bottom: 50px;
}

h1 {
  font-size: 3.5rem;
  margin: 0;
  margin-bottom: 24px;
}

.subtitle {
  font-size: 1.4rem;
  margin-top: 0;
  margin-bottom: 32px;
  color: #d4af37;
}

.decree {
  font-size: 1.4rem;
  line-height: 1.7;
  margin: 32px 0;
}

.days {
  font-size: 7rem;
  font-weight: bold;
  color: #d4af37;
  margin: 40px 0 0 0;
  line-height: 1;
}

.lordpc {
  font-size: 5rem;
  font-weight: bold;
  color: #d4af37;
  margin: 40px 0 0 0;
  line-height: 1;
}

.remaining {
  font-size: 1.3rem;
  text-transform: uppercase;
  letter-spacing: 3px;
  margin-top: 16px;
  margin-bottom: 0;
}

.final {
  font-size: 2rem;
  color: #d4af37;
  font-weight: bold;
}

/* Mobile responsivo */
@media (max-width: 768px) {
  .page {
    padding: 16px;
  }

  .card {
    padding: 32px 24px;
    border-width: 2px;
    border-radius: 16px;
  }

  .icon {
    font-size: 2.5rem;
    margin-bottom: 16px;
  }

  h1 {
    font-size: 2rem;
    margin-bottom: 16px;
  }

  .subtitle {
    font-size: 1.1rem;
    margin-bottom: 24px;
  }

  .decree {
    font-size: 1.1rem;
    margin: 24px 0;
  }

  .days {
    font-size: 4.5rem;
    margin: 28px 0 0 0;
    line-height: 1;
  }

  .remaining {
    font-size: 1rem;
    letter-spacing: 2px;
    margin-top: 12px;
  }

  .final {
    font-size: 1.5rem;
  }
}

@media (max-width: 480px) {
  .page {
    padding: 12px;
  }

  .card {
    padding: 24px 16px;
    border-width: 2px;
  }

  .icon {
    font-size: 2rem;
    margin-bottom: 12px;
  }

  h1 {
    font-size: 1.6rem;
    margin-bottom: 12px;
  }

  .subtitle {
    font-size: 0.95rem;
    margin-bottom: 16px;
  }

  .decree {
    font-size: 0.95rem;
    margin: 16px 0;
  }

  .days {
    font-size: 3.5rem;
    margin: 20px 0 0 0;
    line-height: 1;
  }

  .remaining {
    font-size: 0.85rem;
    letter-spacing: 1px;
    margin-top: 10px;
  }

  .final {
    font-size: 1.2rem;
  }
}
</style>