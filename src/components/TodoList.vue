<template>
  <div class="container">
    <h3>Todo List (TPM-3)</h3>
    <div>
      <p><strong>Todo list:</strong></p>
      <ol>
        <li v-for="(item, index) in todoList" :key="index">{{ item.name }}</li>
      </ol>
    </div>

    <form v-on:submit.prevent="addItem">
      <p>
        <input
          type="text"
          required
          placeholder="item name.."
          v-model="itemName"
        />
        <button type="submit">Add item</button>
      </p>
    </form>
    <p v-if="todoList.length >= 4">Hebat!</p>
  </div>
</template>

<script>
export default {
  name: 'TodoList',
  data() {
    return{
      itemName: null,
      todoList: [],
    }
  },
  methods: {
    addItem() {
      let item = {
        name: this.itemName,
      };
      this.todoList.push(item);
      this.itemName = null;
    },
  },
  computed: {
    isHebat() {
      if (this.todoList.length >= 4) {
        return "Hebat!";
      } else {
        return "";
      }
    },
  },
}
</script>

<style scoped>
  .container{
    width: 60%;
    border: 1px solid black;
    margin: auto;
    text-align: left;
    padding-left: 20px;
  }
</style>