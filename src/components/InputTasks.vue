<script setup lang="ts">


import { reactive } from 'vue';
import Listagem from "./Listagem.vue";

interface Todo{
    id:number,
    name:string,
    done:boolean,
    hour:string
}
const arrayTarefas = reactive<Todo[]>([]);

const newTask = reactive<Omit<Todo, "id">>({
  name: "",
  hour: "",
  done:false
});



function handleAddTask(){

    if (newTask.name) {
        arrayTarefas.push({id:arrayTarefas.length+1,...newTask});
        console.log(arrayTarefas)
    }
    else {
        alert('Insira uma tarefa!')
    }
}




</script>

<template>
   <div class="home">
        <input class="home-input-text" v-model="newTask.name" type="text"  placeholder="Insira a tarefa" maxLength='60'/>
        <input class="home-input-time" v-model='newTask.hour' type="time"/>
        <button class="home-button-mais" @click='handleAddTask'>+</button>

    </div>
    <Listagem v-for="(tarefa,index) in arrayTarefas" :key="index" :tarefa="tarefa"/>
</template>

<style scoped>
.home{
    background-color: #FFF;
    box-shadow: 0px 0px 4px #CCC;
    border-radius: 10px;
    padding:20px;
    margin: -40px 2% 5px 2%;
    width:95%;

    display: flex;
    align-items: center;
    justify-content: center;
}

.home-input-text{
    width: 90%;
    height: 25px;
    border: 1px solid silver;
    border-radius: 10px;
    padding: 20px 15px
}
.home-input-text:focus{
    outline-color: #3fab24;
}
.home-input-time{
    margin-left: 3px;
    height: 25px;
    border: 1px solid silver;
    border-radius: 10px;
    padding: 20px 15px;
    min-width: 100px;
}
.home-input-time:focus{
    outline-color: #3fab24;
}
.home-button-mais {
    cursor: pointer;
    color:#3fab24;
    background: none;
    border:none;
    margin-left:5px;
    font-size: 1.5rem;
    width: 2rem;
    height: 2rem;
    border: 1px solid #3fab24;
    border-radius: 50%;
}
</style>
