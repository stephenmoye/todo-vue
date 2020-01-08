/* Features to add */
/*
  - Editable text on click
  - Multiple todo lists
  - export/import todo list as text file
  - repositioning of todos >> across multiple lists
*/

<template>
    <div>
        <div class="row">
            <div class="col-xs-12">
                    <form v-on:submit.prevent>
                        <div class="form-group">
                            <input type="text" v-on:keyup.enter="add()" v-model="input" class="form-control col-xs-8" id="isCompleted" placeholder="Add Todo Item Here" />
                            <button tabindex="0" type="button" v-on:click="add()" class="btn btn-default col-xs-1">+</button>
                        </div>
                    </form>
            </div>
        </div>
        <div class="row">
            <div class="col-xs-12">
                <h2 v-on:click="editList()">to-do list</h2>
                <ul class="list-group">
                    <li class="list-group-item" v-bind:class="{ strikeT: todos[index].isCompleted }" v-for="(todo, index) in todos" :key="index">
                       
                        <button class="btn btn-complete" v-on:click="toggleComplete(todo, index)">
                            <span v-if="todo.isCompleted">☑</span>
                            <span v-else>☐</span>
                        </button>
                        
                          {{ index + 1 }}. {{ todo.input }} 
                        
                        <button type="button" v-on:click="deleteItem(todo)" class="btn btn-delete">x</button>
                       
                    </li>
                </ul>
            </div>
            
        </div>
    </div>
</template>  
 
<script>
const STORAGE_KEY = "todo-storage";
export default {
  name: "Todo",
  data() {
    return {
      todos: [],
      input: ""
    };
  },
  created() {
    this.todos = JSON.parse(localStorage.getItem(STORAGE_KEY) || "[]");
  },
  methods: {
    add: function() {
      if (this.input === "") {
        //alert("Please enter a to-do item");
      } else {
        this.todos.push({
          input: this.input,
          isCompleted: false
        });
        this.input = "";

        localStorage.setItem(STORAGE_KEY, JSON.stringify(this.todos));
      }
    },
    deleteItem(todo) {
      var position = this.todos.indexOf(todo);
      this.todos.splice(position, 1);
      localStorage.setItem(STORAGE_KEY, JSON.stringify(this.todos));
    },
    toggleComplete(todo, index) {
      var position = this.todos.indexOf(todo);
      var todoItem = this.todos[position].isCompleted;

      if (todoItem === false) {
        //$set is needed to access and modify properties within the array object todos
        this.$set(this.todos[position], "isCompleted", true);

      } else {
        this.$set(this.todos[position], "isCompleted", false);
      }
      localStorage.setItem(STORAGE_KEY, JSON.stringify(this.todos));
    }
  }
};
</script>  