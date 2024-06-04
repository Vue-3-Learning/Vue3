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
          <button @click="attackMonster">ATTACK</button>
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
        getRandomVal(min,max){
            return Math.floor(Math.random() * (max-min) + min)
        },
        attackMonster() {
            //we'll attack the monster and reduce its health with a random number for example value between 5 and 12 so
           const attackValue = this.getRandomVal(5,12);
           this.monsterHealth -= attackValue;
           this.attackPlayer()
        },
        attackPlayer(){
            const attackValue  = this.getRandomVal(8,15);
            this.playerHealth -= attackValue
        }
    }
}
</script>