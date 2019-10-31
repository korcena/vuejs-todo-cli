<template>
  <div id="app">
    <h1>My To Do List</h1>
    <EntryInput v-bind:todos="todos" />
    <div class="status">Unfinished entries: {{unfinishedEntries.length}}</div>
    <EntryItem v-bind:todos="todos"/>
  </div>
</template>

<script>
import EntryInput from "./components/EntryInput.vue";
import EntryItem from "./components/EntryItem.vue";

export default {
  name: "app",
  data: function() {
    return {
      todos: []
    };
  },
  components: {
    EntryInput,
    EntryItem
  }, 
  computed: {
    unfinishedEntries: function(){
      return this.todos.filter(en => !en.isDone);
    }
  }, 
  watch: {
    todos: {
      handler: function(newList){
        sessionStorage.setItem('my-todo-list', JSON.stringify(newList));
      }, 
      deep: true
    }
  },
  mounted: function(){
    const data = sessionStorage.getItem('my-todo-list');
    this.todos = data ? JSON.parse(data) : [];
  }
};
</script>

<style>
body > div {
  width: 600px;
  max-width: 90%;
  margin: 0 auto;
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
}

.status {
    text-align: left;
    margin: 1rem 0;
}
</style>
