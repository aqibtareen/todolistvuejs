<template>
  <title>Vuejs Todolist</title>
  <div class="todo">
    <h1>My To-Do List</h1>
    <form @submit.prevent="addItem">
      <input type="text" v-model="newItem" placeholder="Add a new item" required>
      <button>Add</button>
    </form>
    <ul>
      <li v-for="(item, index) in items" :key="index">
        <input type="checkbox" v-model="item.completed">
        <span :class="{completed: item.completed}">{{ item.text }}</span>
        <button @click="removeItem(index)">Remove</button>
      </li>
    </ul>
  </div>
  <br><br>
  <footer>
      <p>&copy; Vue.js Todolist By Aqib Tareen</p>
    </footer>
</template>


<script>
export default {
  data() {
    return {
      items: [
        { text: 'Learn Vue.js', completed: false },
        { text: 'Build a to-do list app', completed: true },
        { text: 'Master front-end development', completed: false },
      ],
      newItem: ''
    };
  },
  methods: {
    addItem() {
      if (this.newItem) {
        this.items.push({
          text: this.newItem,
          completed: false
        });
        this.newItem = '';
      }
    },
    removeItem(index) {
      if (confirm('Are you sure you want to remove this item?')) {
        this.items.splice(index, 1);
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.todo {
  margin: 0 auto;
  width: 50%;
  padding: 10px;
  background-color: #f1f1f1;
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.2);
  font-family: sans-serif;
  color: #333;
}

h1 {
  text-align: center;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  margin-bottom: 10px;
  display: flex;
  align-items: center;
}

li input[type=checkbox] {
  margin-right: 10px;
}

li button {
  margin-left: auto;
  background-color: #ddd;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

li button:hover {
  background-color: #999;
  color: #fff;
}

.completed {
  text-decoration: line-through;
  color: #888;
}
footer {
  padding: 20px;
  background-color: #fff;
  box-shadow: 0 -2px 4px 0 rgba(0, 0, 0, 0.2);
  text-align: center;
}
</style>