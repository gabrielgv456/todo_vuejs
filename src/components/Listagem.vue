<script setup lang="ts">
import { ref } from 'vue'

defineProps<{ tarefa: {id:number,name:string,done:boolean,hour:string} }>()
const ischecked = ref(false)
</script>

<template>
   <div class="listagem">
         <input class="input-listagem" 
         type="checkbox"
         v-model="ischecked" 
         />
         <label  v-bind:class="`${ischecked ? 'tarefa-description-completed' : 'tarefa-description-no-completed'}`">{{tarefa.name}}</label>
         <label v-bind:class="`${ischecked ? 'tarefa-hour-completed' : 'tarefa-hour-no-completed'}`">{{ tarefa.hour }}</label>
         <button class="tarefa-icon-trash" type="button" ><BsTrash size="16"/></button>
      </div>
</template>

<style scoped>
.listagem {
    background-color: #FFF;
    box-shadow: 0px 0px 5px #CCC;
    border-radius: 10px;
    padding:20px;
    margin: 10px 2% 5px 2%;
    width:95%;
    display: flex;
    justify-content: space-between;
}
.input-listagem{
    margin-right: 8px;
    min-width: 15px;
    min-height: 15px;
}
.tarefa-description-completed{
    text-decoration:line-through;
    opacity: 0.6;
    width: 40%;
}
.tarefa-description-no-completed{
    width: 40%;
}
@media screen and (max-width: 590px) {
    .tarefa-description-completed{
    max-width:35ch;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    }
    .tarefa-description-no-completed{
    max-width:35ch;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    }
}

.tarefa-hour-completed{
    text-decoration:line-through;
    opacity: 0.6;
    width: 10%;
}
.tarefa-hour-no-completed{
    width: 10%;
}
.tarefa-icon-trash{
    text-decoration: none;
    background: none;
    border:none;
    color:red;
    cursor: pointer;
}
</style>
