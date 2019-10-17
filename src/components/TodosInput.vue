<template>
      <header class="header">
        <h1>{{title}}</h1>
        <input class="new-todo" placeholder="What needs to be done?" @keyup.enter="createTodo" >
      </header>
</template>

<script>
export default{
  name:"TodosInput",
  props:{
    title:{type:String}
  },
  methods:{
    createTodo(ev){
      this.$emit('createTodo',ev.target.value);
      ev.target.value = '';
    }
  }
}

</script>
