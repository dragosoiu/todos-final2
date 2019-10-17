<template>
  <footer class="footer">
        <!-- This should be `0 items left` by default -->
        <span class="todo-count">
          <strong>{{itemsAvailable}}</strong> item(s) left
        </span>
        <!-- Remove this if you don't implement routing -->
        <ul class="filters">
          <li>
            <a @click.stop="changeFilter('all')" :class="{selected: isClassSelected('all')}" href="#/all">All</a>
          </li>
          <li>
            <a  @click.stop="changeFilter('active')"  :class="{selected: isClassSelected('active')}" href="#/active" >Active</a>
          </li>
          <li>
            <a @click.stop="changeFilter('completed')"  :class="{selected: isClassSelected('completed')}" href="#/completed">Completed</a>
          </li>
        </ul>
        <!-- Hidden if no completed items are left ↓ -->
        <button class="clear-completed">Clear completed</button>
      </footer>
</template>

<script>
export default{
  name:"TodosActions",
  props:['itemsAvailable','activeFilter'],
  methods:{
    changeFilter(filter){
      if (filter)
        this.$emit('fitlerChanged', filter)
    },
    isClassSelected(cls){ 
      return this.activeFilter == cls ;}
  }
}

</script>
