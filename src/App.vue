<script setup>
import {ref,onMounted,shallowRef} from 'vue'
import { nanoid } from 'nanoid'
import TabA from './Tab/TabA.vue'
import TabB from './Tab/TabB.vue'
import TabC from './Tab/TabC.vue'


let value=ref('')
let tab= shallowRef(TabA)
let data=ref([{
  id:nanoid(),
  details:'Do coding challenges',
  completed:false,
  Active:true,
}])

console.log(data)

 const add=()=>{
  data.value.push({
    id:nanoid(),
    details:value.value,
  completed:false,
  Active:true,
  })
 value.value=''
 }
 const check=(e)=>{
  const obj=data.value.find((item)=>item.id==e.target.id)
  obj.completed=!obj.completed;
  obj.Active=!obj.Active;
 }
 const remove=(e)=>{
   const obj=data.value.filter((item)=>item.id!==e.target.id)
   data.value=obj
     
 }
 const removeAll=(e)=>{
   const obj=data.value.filter((item)=>!item.completed)
    data.value=obj
     
 }
</script>

<template>
  <h1>#todo</h1>
  <section class="sect">
 <div class="d-flex">
    <span @click="tab=TabA" :class="tab==TabA?'bb':''"><p>All</p></span>
    <span @click="tab=TabB" :class="tab==TabB?'bb':''"><p>Active</p></span>
    <span @click="tab=TabC" :class="tab==TabC?'bb':''"><p>Completed</p></span>
  </div>
  <div class="hr"><hr></div>
  </section>
 
  <div class="search" v-if="tab!==TabC"><input type="text" class="input-box" v-model="value" placeholder="add details">  <button @click="add" class="btn">Add</button></div>
  <component :is="tab" :action="check" :data="data" :remove="remove" :removeAll="removeAll"/>
</template>

<style >
h1{
  text-align: center;
}
.d-flex{
  display: flex;
  gap: 10rem;
  justify-content: center;
}
.d-flex2{
  display: flex;
  align-items: center;
  gap: 0.2rem;
}
.d-flex p{
  cursor: pointer;
}
.btn{
  background-color: #2F80ED;
  border-radius: 12px;
  padding: 1rem 2rem;
  color: #333;
  font-weight: 700;
}
.input-box{
  height: 56px;
  width: 476px;
  border: none;
  border: 1px solid #BDBDBD;
  border-radius: 12px;
  font-size: 14px;
  padding-inline: 1rem;
}
.linethrough{
  text-decoration: line-through;
}
.bb{
 border-bottom: 4px solid #2F80ED;
 border-radius: 4px 4px 0px 0px;
 width: 80px;
}
.hr{
  margin-top: -0.6rem;
  padding: 0;
}
.search{
  margin-top: 1.5rem;
}
@media (max-width:614px) {
  .input-box{
    max-width: 100%;
  }
  .search{
    max-width: 220px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  gap: 1rem;
  }
  .d-flex{
    gap: 2rem;
  }
  .sect{
    max-width: 400px;

  }
}
</style>
