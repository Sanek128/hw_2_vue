<template>

    <div id = "toDo">
    <h3 style = "text-align: center"> MY TO DO LIST </h3>
    <AddTodo 
      :toDo="toDo"
      :x="x"
      @newToDoS="newToDo"
    />
    <TodoList 
      :toDo="toDo"
      @delToDoList="delToDo"
    />
      
    </div>

</template>

<script>

import AddTodo from "@/components/ToDo/AddTodo";
import TodoList from "@/components/ToDo/TodoList";

export default {
  name: 'App',

  components: {
    AddTodo,
    TodoList
  },
  
  data() {
    return {
      // message: 'Test message',

      toDo: ['Отжаться от пола 100 раз за день','Сделать вторую домашку по vue', 
            'Посмотреть пропущенный урок английского','Пробежать 5 км вечером' ],
      // addToDo: '',
      x: false,
    }
  },

  methods: {
    newToDo(e) {
      this.toDo.push(e)

      if (this.toDo.length >= 10) 
        this.x = true;
    },

    delToDo (ev) {
      let index = this.toDo.findIndex(value => value === ev);
      this.toDo.splice (index, 1)
      console.log('ev - App.vue --> '+ ev);
      console.log('index - App.vue --> '+ index);

      if (this.toDo.length < 10) 
        this.x = false;
      
    },
  }
}

</script>

<style>

.none {display: none}

#toDo {
  width: 500px;
  box-shadow: 0 3px 20px #0f0f0f23;
  padding: 10px;
  margin: 20px 0 0 20px;
}

</style>