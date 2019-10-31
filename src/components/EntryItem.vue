<template>
  <div class="items">
      <div class="item" v-for="(entry, index) in todos" v-bind:key="'entry-' + index" v-bind:class="{done: entry.isDone}">
          <input type="checkbox" name="isDone" v-model="entry.isDone">
          {{entry.value}}
          <a class="close" v-on:click="removeEntry(index)">X</a>
      </div>
  </div>
</template>

<script>
export default {
  props: ["todos"], 
  methods: {
      removeEntry: function(index){
          this.todos.splice(index, 1);
      }
  }
};
</script>

<style>
.items {
  text-align: left;
  margin: 1rem 0;
}

.item {
  margin: 0.5em 0;
  font-size: 1.2rem;
  display: flex;
  align-items: center;
}

.item input[type="checkbox"] {
  transform: scale(1.2);
  margin-right: 1rem;
}

.item.done {
  text-decoration: line-through;
  color: grey;
}

.item .close {
  color: red;
  font-weight: bold;
  margin-left: auto;
  cursor: pointer;
}
</style>