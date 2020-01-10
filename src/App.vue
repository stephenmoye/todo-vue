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
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
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

.form-group {
  max-width: 750px;
  width: 70vw;
  margin: auto;
}

.btn {
  transition: 0.5s;
  background: #eee;
  vertical-align: top;
}

.btn-default {
  /* position: absolute; */
}

.btn-delete {
  position: absolute;
  right: 0;
  bottom: 0;
  margin: 0;
  height: 100%;
  width: 50px;
  font-size: 1.5rem;
  line-height: 2rem;
  border-radius: 0; 
}

.btn-delete:hover {
  background: #ff8d8d;
  /* box-shadow: #ff8180 0 -3px 1px inset; */
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
  /* box-shadow: #ff8180 0 -3px 1px inset; */
  transition: 0.5s;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
