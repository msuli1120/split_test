<template>
  <div class="row container">
    <div class="col-md-6">
      <h1>App Component</h1>
      <ul>
        <li v-for="(todo, index) in todos" @click="remove(index, todo)">{{ todo }}</li>
      </ul>
    </div>

    <div class="col-md-6">
      <p v-for="(thing, index) in output" @click="reverseRemove(index, thing)">{{ thing.todo }}: {{ thing.price }}</p>
      <div v-if="result != 0">
        <p v-model="result">Total: {{ result }}</p>
      </div>
    </div>

    <driver></driver>
  </div>
</template>

<script>
import Driver from './components/Driver.vue'

export default {
  components: {
    'driver': Driver,
  },
  data () {
    return {
      todos: [
        { todo: 'Do the dishes', price: 1},
        { todo: 'Take out the trash', price: 5},
        { todo: 'Movie', price: 3},
        { todo: 'Sleep', price: 4},
        { todo: 'Shopping', price: 9},
      ],
      output: [],
      result: 0,
    }
  },
  methods: {
    remove: function(i, obj){
      this.output.push(obj);
      this.todos.splice(i, 1);
      this.result += obj.price;
    },
    reverseRemove: function(i, obj){
      this.todos.push(obj);
      this.output.splice(i, 1);
      this.result -= obj.price;
    }
  }
}
</script>

<style>

</style>
