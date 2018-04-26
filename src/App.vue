<template>
  <div id="app">
    <h1 class='title'>Monster Smash</h1>
    <div class='nav-buttons'>

      <section>
      <button @click='handleToggle(true)'  class="btn btn-dark">Create</button>
      </section>

      <section>
      <button @click='handleToggle(false)'  class="btn btn-dark">Monsters</button>
      </section>

    </div>

    <div v-if='toggle'>

      <!-- passing fn? -->
      <create  :createMonster='createMonster'>
      </create>
    </div>



    <div v-else>

      <!-- running through monster array? -->
      <monsters 
      :monsters='monsters'
      :editMonster='editMonster'
      >
        </monsters>
    </div>

  </div>
</template>

<script>

import Create from './components/Create';
import Monsters from './components/Monsters';

export default {
  data() {
    return {
      toggle: true,
      monsters: [],
    };
  },
  methods: {
    handleToggle(bool) {
      this.toggle = bool;
    },
    createMonster(name, health, attack){
      let newMonster = {
        name,
        health,
        attack
      }
      console.log('we good')
      this.monsters.push(newMonster)
      console.log('ya we still aight')
      this.handleToggle(false);
      
    },
    editMonster(name, health, attack, i){
      console.log('gettin hit in app')
      this.monsters[i] = {name, health, attack}
    }
  },
  components:{
    create: Create,
    monsters: Monsters
  }
};
</script>


<style>
@import url('https://fonts.googleapis.com/css?family=Freckle+Face');

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: 'Freckle Face', cursive;
  background-color: #E1E1E1;
  padding: 10px 0 200px 0;
}
.title {
  color: red;
  text-shadow: 1px 1px 1px black;
  letter-spacing: 5px; 
}
.nav-buttons {
  display: flex;
}
</style>
