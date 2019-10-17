<template>
  <section class="main">
        <input id="toggle-all" class="toggle-all" type="checkbox">
        <label for="toggle-all">Mark all as complete</label>
        <ul class="todo-list">
          <!-- These are here just to show the structure of the list items -->
          <!-- List items should get the class `editing` when editing and `completed` when marked as completed -->
          <li class="completed">         
           <li v-for="todo in todos" :key="todo.id" :class="{completed: todo.isCompleted}">
            <div class="view">
              <input class="toggle" type="checkbox" :checked= "todo.isCompleted" @click="changeTodo(todo)">
              <label>{{todo.title}}</label>
              <button class="destroy" @click="destroy(todo)"></button>
            </div>
            <input class="edit" value="Rule the web">
          </li>

        </ul>
      </section>
</template>

<script>
export default{
  name:"TodosList",
  props:{
    todos:{type:Array}
  },
  methods:{
    destroy(todo){
      if (confirm("Are you sure you want to delete: " + todo.title))
        this.$emit('deleteTodo', todo);
    },
    changeTodo(todo){
      todo.isCompleted = !todo.isCompleted;
    }
  }
}

</script>
