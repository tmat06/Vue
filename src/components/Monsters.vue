<template>
<div class='monster'>
    <div>
        <p>Monster #1: {{monster1}}</p>
        <p>Monster #2: {{monster2}}</p>
    </div>
    <button @click='battleRoyale'>Battle These Fools</button>


    <monster
      v-for='(monster, i) in monsters'
      :key='i'
      :monster='monster'
      :pickMonster='pickMonster'
      :editMonster='editMonster'
      :index='i'>
    </monster>




</div>
</template>

<script>
import Monster from "./Monster.vue";

export default {
  data() {
    return {
      monster1: "",
      monster2: ""
    };
  },
  props: ["monsters", "editMonster"],
  components: {
    monster: Monster
  },
  methods: {
      pickMonster(monster){
          if(!this.monster1){
              this.monster1 = monster
          } else {
              this.monster2 = monster
          }
      },
      battleRoyale(){
          if(!this.monster1 || !this.monster2){
              alert('fill in both spots homie')
          } else {

              if(this.monster1.name === 'TBone'){
                  alert('Winner: ' + this.monster1.name)
              } else if(this.monster1.attack > this.monster2.attack){
                  alert('Winner: ' + this.monster1.name)
              } else if(this.monster1.attack === this.monster2.attack){
                  if(this.monster1.health > this.monster2.health){
                      alert('Winner: ' + this.monster1.name)
                  } else {
                      alert('Winner: ' + this.monster2.name)
                  }
              } else {
                  alert('Winner :' + this.monster2.name)
              }
          }
      }
  }
};
</script>

<style>


</style>