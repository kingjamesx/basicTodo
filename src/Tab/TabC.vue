<script setup>

const props=defineProps({
  action:{
    action:'Function',
  },
  remove:{
    remove:'Function',
  },
  removeAll:{
    removeAll:'Function',
  },
  data:{
    id:"String",
    details:"String",
  completed:"Boolean",
  Active:"Boolean",
  remove:"Boolean"
  }
})
</script>
<template>
<div v-for="todo in data" class="list" :key="todo.id">
    <section  v-if="todo.completed && !todo.remove" class="cont"><div class="d-flex2"><input type="checkbox" @change="action" :id="todo.id" :checked="todo.completed" ><p :class="todo.completed?'linethrough':''">{{todo.details}}</p> </div><span><button class="del t" @click="remove" :id="todo.id">Delete</button></span></section> 
  </div>
    <div class="all"> <button class="del" @click="removeAll">remove All</button></div>
</template>
<style scoped>
 .cont{
    display: flex;
    justify-content: space-between;
    align-items: center;
 }
  .del{
    background-color: #EB5757;
    color: #fff;
  }
  .all{
    margin-top: 2rem;
  }
  @media (max-width:611px) {
    .del{
        padding: 0.5rem;
    }
    .t{
        margin-left: 1rem;
    }
  }
</style>