<template>
  <div id="app">
     <section class="row">
        <div class="small-6 columns">
            <h1 class="text-center">Player</h1>
            <div class="healthbar">
                <div class="healthbar text-center" :style="myStyle" style="background-color: green; margin: 0; color: white;">
                  {{ player }}
                </div>
            </div>
        </div>
        <div class="small-6 columns">
            <h1 class="text-center">Monster</h1>
            <div class="healthbar">
                <div class="healthbar text-center" :style="monsterStyle" style="background-color: green; margin: 0; color: white;">
                  {{ monster }}
                </div>
            </div>
        </div>
    </section>
    <section v-if="show" class="row controls">
        <div class="small-12 columns">
            <button v-on:click="show = !show" id="start-game">START NEW GAME</button>
        </div>
    </section>
    <section v-else class="row controls">
        <div class="small-12 columns">
            <button v-on:click="normalDmg" id="attack">ATTACK</button>
            <button v-on:click="specialDmg" id="special-attack">SPECIAL ATTACK</button>
            <button v-on:click="iNeedHealing" id="heal">HEAL</button>
            <button v-on:click="giveUp" id="give-up">GIVE UP</button>
        </div>
    </section>
    <section class="row log">
        <div class="small-12 columns">
          <ul class="log ul monster-turn"v-for="mun in mList">

                <li class="log ul player-turn"v-for="item in list">
                  you took {{  }} of damage
                </li>
                <li>
                  The monster took {{ mun }} of damage
                </li>
            </ul>
        </div>
    </section>
  </div>
</template>

<script>
export default {
   name: "app",
   data() {
      return {
         show: true,
         player: 100,
         monster: 100,
         list: [],
         mList: []
      };
   },
   methods: {
      normalDmg() {
         const random = Math.floor(Math.random() * 10);
         const mRandom = Math.floor(Math.random() * 10);
         this.monster = this.monster - mRandom;
         this.player = this.player - random;
         this.list.unshift(mRandom);
         this.mList.unshift(mRandom);
         if (this.monster <= 0) {
            this.monster = 0;
            alert("You Win");
            this.player = 100;
            this.monster = 100;
            this.show = true;
            this.list = [];
            this.mList = [];
         }
         if (this.player <= 0) {
            this.player = 0;
            alert("You Suck, Loser!");
            this.player = 100;
            this.monster = 100;
            this.show = true;
            this.list = [];
            this.mList = [];
         }
      },
      specialDmg() {
         this.monster = this.monster - Math.floor(Math.random() * 20);
         this.player = this.player - Math.floor(Math.random() * 20);
         if (this.monster <= 0) {
            this.monster = 0;
            alert("You Win");
            this.player = 100;
            this.monster = 100;
            this.show = true;
         }
         if (this.player <= 0) {
            this.player = 0;
            alert("You Suck, Loser!");
            this.player = 100;
            this.monster = 100;
            this.show = true;
         }
      },
      iNeedHealing() {
         this.player = this.player + Math.floor(Math.random() * 10);
         this.player = this.player - Math.floor(Math.random() * 10);

         if (this.player > 100) {
            this.player = 100;
         }
         if (this.player <= 0) {
            this.player = 0;
            alert("You Suck, Loser!");
            this.player = 100;
            this.monster = 100;
            this.show = true;
         }
      },
      giveUp() {
         this.player = 100;
         this.monster = 100;
         this.show = true;
         this.list = [];
         this.mList = [];
      }
   },
   computed: {
      monsterStyle() {
         return { width: this.monster + "%" };
      },
      myStyle() {
         return { width: this.player + "%" };
      }
   }
};
</script>

<style>
</style>
