<template>
  <div v-if="todos.length=== 0">Vous n'avez pas de tâches</div>
  <div v-else>
    <div v-for="todo in sortedTodos" :key="todo.date" :class="{completed : todo.completed}">
      <label for="completed" >
      <input type="checkbox" name="completed" id="" v-model="todo.completed" > {{ todo.title }} </input>
    </label></div>
  </div>
  <form @submit.prevent="addTodo">
    <input type="text" v-model="newTodo" placeholder="Nouvelle tâche">
    <button type="submit" :disabled="newTodo.length === 0 ">Ajouter</button>
  </form>
</template>
<script setup> 
import { computed, ref } from 'vue';
const todos = ref([
  {
  date:1,
  completed :true,
  title:'tache de test',
},
  {
  completed:false,
  date:2,
  title:'tache à faire',
}

]);
const hideCompleted  = ref(false);
const newTodo = ref('');
const addTodo = ()=> {
  todos.value.push({
    date: Date.now(),
    title: newTodo.value,
    completed: false
  })
newTodo.value =''
}

const sortedTodos = computed(() => {
  console.log(todos.value)
    return todos.value.toSorted((a,b)=>a.completed > b.completed ? 1 : -1)
 
    
})
</script>

<style scoped>

.completed {
  opacity: 5;
  text-decoration: line-through;
  color:red
}
</style>