<template>
  <div>
    <header>
      <h1>Monster Slayer</h1>
  </header>
  <div id="game">
      <section id="monster" class="container">
          <h2>Monster Health</h2>
          <div class="healthbar">
              <div class="healthbar__value" :style="monsterBarStyle"></div>
          </div>
      </section>
      <section id="player" class="container">
          <h2>Your Health</h2>
          <div class="healthbar">
              <div class="healthbar__value" :style="playerBarStyle"></div>
          </div>
      </section>
      <div class="container" v-if="winner">
        <h2>Game Over</h2>
        <h3 v-if="winner === 'monster'">You Lost</h3>
        <h3 v-else-if = "winner === 'player'">You Win</h3>
        <h3 v-else>Match Draw</h3>
        <button @click="restart">Start Over</button>
      </div>
      <section id="controls" v-else>
          <button @click="attackMonster" >ATTACK</button>
          <button @click="specialAttack" :disabled="canUseSA">SPECIAL ATTACK</button>
          <button @click="healPlayer">HEAL</button>
          <button @click="surrender">SURRENDER</button>
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
            monsterHealth: 100,
            currentRound: 0,
            winner: null
        }
    },
    watch:{
        playerHealth(val){
            if(val<=0 && this.monsterHealth <= 0){
                //draw
                this.winner = 'draw'
            }else if(val<=0){
                //palyer lost
                this.winner = 'monster'
            }
        },
        monsterHealth(val){
            if(val<=0 && this.playerHealth <= 0){
                //draw
                this.winner = 'draw'
            }else if(val<=0){
                //monster lost
                this.winner = 'player'
            }
        }
    },
    computed:{
        playerBarStyle(){
            if(this.playerHealth < 0){
                return { width: '0%' }
            }
            return { width: this.playerHealth + '%' }
        },
        monsterBarStyle(){
            if(this.monsterHealth < 0){
                return { width: '0%' }
            }
            return { width: this.monsterHealth + '%' }
        }, 
     canUseSA(){
        return this.currentRound % 3 !== 0
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
           this.attackPlayer();
           this.currentRound++
        },
        attackPlayer(){
            const attackValue  = this.getRandomVal(8,15);
            this.playerHealth -= attackValue
        },
        specialAttack(){
            this.currentRound++
            const attackValue  = this.getRandomVal(10,25);
            this.monsterHealth -= attackValue;
            this.attackPlayer();
        },
        healPlayer(){
            this.currentRound++
            const healValue = this.getRandomVal(8,20);
            if(this.playerHealth + healValue > 100){
                this.playerHealth = 100
            }
            else{
                this.playerHealth += healValue
            }
            this.attackPlayer()
        },
        restart(){
            this.playerHealth = 100,
            this.monsterHealth = 100,
            this.currentRound = 0,
            this.winner = null
        },
        surrender(){
            this.winner = 'monster'
        }
    }
}
</script>