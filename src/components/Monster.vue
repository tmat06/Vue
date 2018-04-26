<template>

<div>

    <div class='each-monster'  v-if='toggle'>
        <div>

          <div @click='pickMonster(monster)'>
              Monster Name: 
         {{monster.name}}
          </div>
           <div>
              Health:
         {{monster.health}}
               </div>
                <div>
                 Attack:
         {{monster.attack}}
               </div>
        </div>
        <button @click='handleToggle(false)'>Edit</button>

        </div>
    <div v-else>
    <form class='form' @submit.prevent='updateMonster()'>
        <input class='input-box' placeHolder='Name' v-model='newName'/>
        <input class='input-box' placeHolder='Health' v-model='newHealth'/>
        <input class='input-box' placeHolder='Attack' v-model='newAttack'/>
        <button type='submit' @submit='updateMonster()'>Create</button>
    </form>
    </div>
</div>
</template>
<script>
export default {
  data() {
    return {
      toggle: true,
      newName: "",
      newHealth: "",
      newAttack: ""
    };
  },
  props: ["monster", "pickMonster", "editMonster", "index"],
  methods: {
    handleToggle(bool) {
      this.toggle = bool;
    },
    updateMonster() {
        console.log("updateMonstah gettin hit yo!")
      this.editMonster(this.newName, this.newHealth, this.newAttack, this.index);
      this.monster.name = this.newName; 
      this.monster.health = this.newHealth; 
      this.monster.attack = this.newAttack; 
      this.handleToggle(true)
    }
  }
};
</script>
<style>
.each-monster {
  margin: 5px 0;
  padding: 5px;
  background-color: rgb(206, 206, 212);
  display: flex;
  flex-direction: column;
  width: 100%;
}
</style>