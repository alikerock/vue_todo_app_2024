<script setup>
import { reactive, ref } from 'vue';
import Todo from './components/TodoItem.vue';
const todoText = ref('');

const addtodo = (e)=>{
  todoText.value = e.target.value;
  const todoTextLength = todoText.value.trim().length;   //빈칸 없애기. 대상.trim()
  if(todoTextLength > 0){
    todos.push({id:todoTextLength+1,title:todoText.value,checked:false})
  }
  todoText.value = '';
}
const todos = reactive([
  {id:1,title:'웹 배우기',checked:false},
  {id:2,title:'취직하기',checked:false}  
])

const toggleCheckbox = ({id, checked})=>{
  const idx = todos.findIndex(todo=>todo.id === id);
  todos[idx].checked = checked;
}

const todoDelete = ({id})=>{
  if(window.confirm('정말 삭제할까요')){
    const idx = todos.findIndex(todo=>todo.id === id);
    todos.splice(idx,1);
  }
}

</script>

<template>
 <div id="app" class="container">
  <h1>Vue Todo App</h1>
  <!-- 
  입력 내용이 실시간 반영
  <BFormInput placeholder="할일을 입력하세요"  v-model="todoText"/>
  <Todo :todo="todoText"/> 
  -->
  <!-- 입력후 엔터시 내용이 추가 -->
  <BFormInput placeholder="할일을 입력하세요"  @keyup.enter="addtodo" v-model="todoText"/>
  <Todo 
    v-for="todo in todos" 
    :key="todo.id" 
    :todo="todo"
    @toggle-checkbox="toggleCheckbox"
    @todo-delete="todoDelete"
  />

 </div>
</template>

<style scoped>
</style>
