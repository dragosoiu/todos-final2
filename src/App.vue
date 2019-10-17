<template>
  <div>
    <section class="todoapp">
      <todos-input :title="title" @createTodo="createTodoHandler" />
      <!-- This section should be hidden by default and shown when there are todos -->

     <todos-list :todos="filteredTodos" @deleteTodo="deleteTodoHandler"  />

      <!-- This footer should hidden by default and shown when there are todos -->
      <todos-actions @fitlerChanged="filterChangedHandler" :itemsAvailable="filteredTodos.length"  
      :activeFilter="filter" />
     
    </section>
    <footer class="info">
      <p>Double-click to edit a todo</p>
      <!-- Remove the below line ↓ -->
      <p>
        Template by
        <a href="http://sindresorhus.com">Sindre Sorhus</a>
      </p>
      <!-- Change this out with your name and url ↓ -->
      <p>
        Created by
        <a href="http://todomvc.com">you</a>
      </p>
      <p>
        Part of
        <a href="http://todomvc.com">TodoMVC</a>
      </p>
    </footer>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import TodosInput from "./components/TodosInput";
import TodosList from "./components/TodosList";
import TodosActions from "./components/TodosActions";

export default {
  name: "App",
  components: {
    HelloWorld,
    TodosInput,
    TodosList,
    TodosActions
  },
  computed:{
    filteredTodos:function(){
      return {
        'all':this.todos,
        'completed':this.todos.filter(x=>x.isCompleted == true),
        'active':this.todos.filter(x=>x.isCompleted == false)
      }[this.filter.toLowerCase()];
    }
  },
  data() {
    return { 
      title: "my todos",
      todos:[
        {id:1, title:"Taste JavaScript", isCompleted: true},
        {id:2, title:"Buy a unicorn", isCompleted: false},
        ],
        filter:'all'
       };
  },
  methods:{
    createTodoHandler(todoTitle){
      console.log('create new todo: '+ todoTitle);
      if (todoTitle){
        this.todos.push({
          id: this.todos.length +1,
          title: todoTitle,
          isCompleted: false
        })
      }
    },
    deleteTodoHandler(todo){
       this.todos.splice(this.todos.indexOf(todo),1);
    },
    filterChangedHandler(filter){
      this.filter = filter;
    }
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
</style>
