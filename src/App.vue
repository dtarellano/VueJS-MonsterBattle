<template>
  <div id="app">
     <section class="row">
        <div class="small-6 columns">
            <h1 class="text-center">YOU</h1>
            <div class="healthbar">
                <div class="healthbar text-center" style="background-color: green; margin: 0; color: white;">

                </div>
            </div>
        </div>
        <div class="small-6 columns">
            <h1 class="text-center">MONSTER</h1>
            <div class="healthbar">
                <div class="healthbar text-center" style="background-color: green; margin: 0; color: white;">

                </div>
            </div>
        </div>
    </section>
    <section class="row controls">
        <div class="small-12 columns">
            <button id="start-game">START NEW GAME</button>
        </div>
    </section>
    <section class="row controls">
        <div class="small-12 columns">
            <button id="attack">ATTACK</button>
            <button id="special-attack">SPECIAL ATTACK</button>
            <button id="heal">HEAL</button>
            <button id="give-up">GIVE UP</button>
        </div>
    </section>
    <section class="row log">
        <div class="small-12 columns">
            <ul>
                <li>

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
         msg: "Welcome to Your Vue.js App"
      };
   }
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
