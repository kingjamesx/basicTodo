<script setup>
const props=defineProps({
  action:{
    action:'Function',
  },
  data:{
    id:"String",
    details:"String",
  completed:"Boolean",
  Active:"Boolean",
  remove:"remove"
  }
})
</script>
<template>
<div v-for="todo in data" class="list" :key="todo.id">
     <div class="d-flex2" v-if="!todo.remove" ><input type="checkbox" @change="action" :id="todo.id" :checked="todo.completed" ><p :class="todo.completed?'linethrough':''">{{todo.details}}</p></div>
  </div>
</template>
<style >
</style>