<template>
  <input
    type="text"
    name="newEntry"
    placeholder="Enter entry"
    v-model="newEntry"
    v-on:keyup.enter="addEntry"
  />
</template>

<script>
export default {
  data: function() {
    return {
      newEntry: ""
    };
  },
  props: ["todos"],
  methods: {
    addEntry: function() {
      this.todos.push({value: this.newEntry, isDone: false});
      this.newEntry = "";
    }
  }
};
</script>

<style>
input[type="text"] {
  width: 90%;
  font-size: 1.2rem;
  padding: 0.4em;
}
input:focus {
  outline: none;
}
</style>