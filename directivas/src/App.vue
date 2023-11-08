<script setup>
import{ref} from 'vue';

let newTaks = ref ('')
let taskList = ref([
  {
    name : 'Estudiar',
    done : true},
    {
    name :'Comer',
    done : false},{
    
    name :'Mimir',
    done : false}])

function setDone(index){
  
  taskList.value[index].done = !taskList.value[index].done 

}

function addTask(){

  if(newTaks.value.trim()== '')return
  taskList.value.push({
  name: newTaks.value,
  done : false
})
newTaks.value =''
}
</script>

<template>
  
  <div class="container">
    <h1>Lista de tareas</h1>
    <p class="subtitle">{{ newTaks }}</p>


  <div>
    <div class="task" :class="{done: task.done}" v-for="(task,index) in taskList" :key="index">{{ task.name }}<samp @click="setDone(index)" class="button">x</samp></div>
   
  </div>
  <input v-model="newTaks" @keypress.enter="addTask" type="text" placeholder="Esbriba su tarea">
  <p v-show="newTaks != '' " class="help">presina "entre para agregar la tarea"</p>

  </div>

</template>

<style scoped>
.done{
  text-decoration: line-through;
}
.help{
  font-size: 8px;
  opacity: 0.6;
  margin: 0;

}
.container{
  text-decoration-color: white;
  font-family: 'Montserrat', sans-serif;
  background-color: #025E73;
  border-radius: 6px;
  max-width: 420px;
  margin: 0 auto;
  padding: 6px 12px;
}
.button{
  background-color: #F2A71B;
  display: inline-block;
  padding: 0 6px;
  border-radius: 3px; 
}
.button:hover{
  cursor: pointer;
}

.task{
  display: flex;
  justify-content: space-between;
  background-color: #A5A692;
  border-radius: 3px;
  margin-bottom: 1px;
  padding: 2px 2px 1px 6px;
}

input{
  border: none;
  border-radius: 3px;
  padding: 2px 6px;
   /*width:calc(100% - 12px) ; */
   width: 100%;
   box-sizing: border-box;
   margin-top: 12px;
}
.input::placeholder{
  opacity: 0.4;
}

.task:hover{
  background-color: rgba(242,178,99,0.8);
}

h1{
  text-transform: uppercase;
  font-size: 18px;
  text-align: center;
  margin: 0;
  margin-top: 12px;
}
.subtitle{
  font-size: 10px;
  margin: 0;
  margin-bottom: 16px;
  text-align: center;
  opacity: 0.6;
}

</style>
