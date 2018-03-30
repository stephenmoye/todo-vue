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
        <h2>to-do list</h2>
            <div class="col-xs-12">
                    <form v-on:submit.prevent>
                        <div class="list-group add-todo">
                            <button tabindex="0" type="button" v-on:click="add()" class="btn btn-default col-xs-1">
                              +
                            </button>
                            <input type="text" v-on:keyup.enter="add()" v-model="input" class="form-control col-xs-8" id="isCompleted" placeholder="Add Todo Item Here" />

                        </div>
                    </form>
            </div>
            <div class="col-xs-12">
                <ul class="list-group">
                    <li class="list-group-item" v-bind:class="{ strikeT: todos[index].isCompleted }" v-for="(todo, index) in todos" :key="index">
                       
                        <button class="btn btn-complete" v-on:click="toggleComplete(todo, index)">
                            <span v-show="todo.isCompleted">
                              <i class="far fa-check-circle"></i>
                            </span>
                            <span v-show="!todo.isCompleted">
                              <i class="far fa-circle"></i>
                            </span>
                        </button>
                        {{ index + 1 }}.
                         <span class="todo-edit" v-show="!todo.edit" v-on:click="todo.edit = true">  {{ todo.input }} </span>
                        <input v-show="todo.edit" v-model="todo.input" v-on:blur="todo.edit = false" @keyup.enter="todo.edit = false">
                        <button type="button" v-on:click="deleteItem(todo)" class="btn btn-delete">
                          x
                        </button>
                       
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
      input: "",
      editedTodo: null
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
          isCompleted: false,
          edit: false
        });
        this.input = "";

        localStorage.setItem(STORAGE_KEY, JSON.stringify(this.todos));
      }
    },
    // editList: function(todo) {
    //   this.todos.push({
    //     input: this.input
    //   });
    //     this.input = "";
    // },
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