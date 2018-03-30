<template>
  <div id="app">
    <Todo/>
  </div>
</template>

<script>
import Todo from "./components/index";

export default {
  name: "App",
  components: {
    Todo
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Nunito");

* {
  transition: 0.25s;
  outline: none;
}

svg {
  color: black;
}

#app {
  /*font-family: "Avenir", Helvetica, Arial, sans-serif;*/
  font-family: "Nunito", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: antialiased;
  text-align: center;
  margin-top: 60px;
}

@media screen and (max-width: 767px) {
  #app {
    margin-top: 15px;
  }
}

input {
  width: calc(100% - 50px);
  padding: 0;
  margin: -1px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.row {
  margin-left: 0;
  margin-right: 0;
}

.col-xs-12 {
  padding-left: 0;
  padding-right: 0;
}

.list-group {
  width: 40vw;
  margin: auto;
}
.list-group > input {
  width: calc(100% - 50px);
  height: 50px;
  font-size: 2rem;
  margin-bottom: 10px;
  margin-top: 0;
}

.list-group-item {
  padding: 10px 60px;
  text-align: left;
  font-size: 2rem;
}

.strikeT {
  text-decoration: line-through;
}

@media screen and (max-width: 767px) {
  .list-group {
    width: 95vw;
  }
}

.form-control {
  width: 85%;
  max-width: 750px;
  border: 1px solid #ccc;
}

.form-control:focus {
  border: 1px solid #aaa;
  -webkit-box-shadow: none;
  box-shadow: none;
}

.form-group.btn {
  position: absolute;
  top: 3px;
  right: 3px;
  font-size: 5rem;
  margin: 0;
  padding: 0px 10px 7px;
  line-height: 0.5;
}

/* .todo-edit input {
  outline: 1px solid #eee;
} */

.btn {
  transition: 0.5s;
  background: #eee;
  vertical-align: top;
}

.btn-default {
  width: 50px;
  height: 50px;
  font-size: 3rem;
  font-weight: bold;
  line-height: 0;
}

.btn-delete {
  position: absolute;
  right: 0;
  bottom: 0;
  margin: 0;
  height: 100%;
  width: 50px;
  font-size: 2.5rem;
  font-weight: bold;
  line-height: 2rem;
  border-radius: 0;
}

.btn-delete:hover {
  background: #ff8d8d;
  -webkit-box-shadow: inset -3px 3px 5px rgba(0, 0, 0, 0.1);
  box-shadow: inset -3px 3px 5px rgba(0, 0, 0, 0.1);
  transition: 0.5s;
}

.btn-complete {
  position: absolute;
  left: 0;
  bottom: 0;
  margin: 0;
  height: 100%;
  width: 50px;
  border-radius: 0;
  font-size: 2rem;
  line-height: 0;
}
.btn-complete:hover {
  background: #7ef1b7;
  -webkit-box-shadow: inset 3px 3px 5px rgba(0, 0, 0, 0.1);
  box-shadow: inset 3px 3px 5px rgba(0, 0, 0, 0.1);
  transition: 0.5s;
}
.btn-complete:focus {
  background:#eee;
}

.btn.active.focus,
.btn.active:focus,
.btn.focus,
.btn:active.focus,
.btn:active:focus,
.btn:focus {
  outline: none!important;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>

