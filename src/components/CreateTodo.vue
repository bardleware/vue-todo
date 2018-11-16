<template>
  <div class="create-todo">
    <input type="text" v-model="newTodo" placeholder="new todo" v-on:keyup.enter="emitCreateTodo">
    <button v-on:click="emitCreateTodo">Create</button>
  </div>
</template>

<script>
export default {
  name: 'CreateTodo',
  data: function() {
    return {
      'newTodo':'',
    }
  },
  methods: {
    emitCreateTodo: function () {
      if (this.newTodo.length > 0){
        this.$emit('create-todo', {
          label: this.newTodo,
          complete: false,
        })

        this.newTodo = '';
      }
    }
  }
}
</script>

<style scoped>
div {
  display:flex;
  max-width: 600px;
  align-items: baseline;
  margin-bottom: 12px;
  margin: 0 auto;
  margin-bottom: 12px;
}

button {
  flex: 1 0 auto;
  border-radius: 4pt;
  background-color: #2c3e50;
  color: #ddd;
  font-size: 24pt;
  cursor: pointer;
  min-width: 36px;
  border-radius: 4pt;
  margin-right: 12px;
}

input {
  flex: 2 0 auto;
  font-size: 24pt;
  border:none;
  background-color: #ddd;
  margin-right: 12px;
}
</style>
