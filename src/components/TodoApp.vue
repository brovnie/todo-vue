<template>
<div>
    <div class="">
        <input type="text" placeholder="todo" v-model="newToDo">
        <button @click="addToDo">Add ToDo</button>
    </div>
    <TodoItem 
    :item="item" 
    v-for="item in items" 
    v-bind:key="item.id"
    @removeClicked="removeToDo"/>
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
    components: {
        TodoItem
    },
  data() {
    return {
      title: "Todo-list",
      newToDo: 'default',
      items: [
        {title: "Practice vue", completed: true, id:1},
        {title: "Make a coffee", completed: false, id:2}
      ]
    }
  },
  methods: {
    addToDo() {
      this.items.push({
        title: this.newToDo, 
        completed: false, 
        id:Math.random()})
         this.newToDo = "";
    },
    removeToDo(id) {
      const index = this.items.findIndex(el => el.id === id)
      this.items[index].completed = true;
    }
   
  }
} // end export
</script>

<style>
.item{
  border: 1px solid #CDCDCD;
  margin: 2em auto;
  max-width: 50%;
}
.complated {
  text-decoration: line-through;
  opacity: 0.3;
}
</style>

