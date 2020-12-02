<template>
      <div
    class="item"
    v-bind:class="{ complated: item.completed }">
    <h3>{{ item.title }}</h3>
    <button @click="removeToDo">Done</button>
  </div>
</template>

<script>
export default {
    props: ['item'],
     methods: {
    removeToDo() {
      this.$emit('removeClicked', this.item.id)
        }
    }
}
</script>