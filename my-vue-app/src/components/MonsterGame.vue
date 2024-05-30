<template>
  <div>
    <header>
      <h1>Monster Slayer</h1>
  </header>
  <div id="game">
      <section id="monster" class="container">
          <h2>Monster Health</h2>
          <div class="healthbar">
              <div class="healthbar__value"></div>
          </div>
      </section>
      <section id="player" class="container">
          <h2>Your Health</h2>
          <div class="healthbar">
              <div class="healthbar__value"></div>
          </div>
      </section>
      <section id="controls">
          <button>ATTACK</button>
          <button>SPECIAL ATTACK</button>
          <button>HEAL</button>
          <button>SURRENDER</button>
      </section>
      <section id="log" class="container">
          <h2>Battle Log</h2>
          <ul></ul>
      </section>
  </div>
  </div>
</template>
<script>
export default {
    data() {
        return {
            playerHealth: 100,
            monsterHealth: 100
        }
    },
    methods: {
        attack() {

        },

    }
}
</script>