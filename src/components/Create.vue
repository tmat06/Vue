<template>
<div>
    <form class='form' @submit.prevent='addMonster'>
        <input class='input-box' placeHolder='Name' v-model='newName'/>
        <input class='input-box' placeHolder='Health' v-model='newHealth'/>
        <input class='input-box' placeHolder='Attack' v-model='newAttack'/>
        <button type='submit' @submit='addMonster'>Create</button>
    </form>
</div>
</template>
<script>
export default{
    data(){
        return{
            newName: '',
            newHealth: '',
            newAttack:''
        }
    },
    methods:{
        addMonster(){
            console.log('newName', this.newName, 'newHealth', this.newHealth, 'newAttack', this.newAttack)
            this.createMonster(this.newName, this.newHealth, this.newAttack)
        }
    
    },
    props: ['createMonster'],
    
}
</script>
<style>
.form{
    background-color: grey;
    display: flex;
    flex-direction: column;
    padding: 30px;
    border-radius: 25px;
}
.input-box{
    margin: 5px;
}
</style>