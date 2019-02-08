<template>
 <div id="app">
   <!--Components injected into template-->

   <!--when a new todo object is emitted under add-todo then pass the obj to the method addTodo here-->
   <!--the addtodo component is a text input fied and a submit button-->
   <AddTodo v-on:add-todo="addTodo"/>
   <!--injects the Todos component here. calls the deleteTodo method on emit of an id from the del-todo-->
   <!--the todos component is a list of all todos-->
   <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
   </div> 
</template>

<script>
//import of components to be used in home
import Todos from '../components/Todos';
import AddTodo from '../components/AddTodo';
import axios from 'axios';

//export of home included embedded dependency components, data object todos[] and methods
export default {
  name: 'Home',
  components:  {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id){
      //user backtick and url and forward slash ${} to pass in a variable
      /*axios calls the deleted method passing in a url and id param. The response
      is a promise that mocks deletion of a todo identified by id from a remote server.
      The response is filtered to remove the todo identified from the local todo list*/
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(res => this.todos = this.todos.filter(todo => todo.id !== id))
      .catch(err => console.log(err));
      
      //this.todos = this.todos.filter(todo => todo.id != id);
    },
    addTodo(newTodo){
      const {title, completed } = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      }).then(res => this.todos = [...this.todos, res.data])
      .catch(err => console.log(err));
    }
  },
  //special method that runs on app launch
  created(){
    //mock data returned in json format from jsonplaceholder. This string includes a param to limit to 5 todos.
      axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err));
    }
}


</script>

<style>
   * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }
  .btn{
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }
  .btn:hover{
    background: #666;
  }
</style>
