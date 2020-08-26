<template>

    <div>
        <h2>TodoList</h2>
        <div
            v-for="(myToDo, index) in toDo" 
            :key="index"
        >
            <TodoItem
            :oneToDo="myToDo"
            @delToDoItem="delToDoItem"
            />
        </div>
        <!-- <span 
            v-for="(myToDo, index) in toDo" 
            :key="index">
            <button @click="delToDo(index)" style="margin-top: 2px"> Выполено </button>
            {{ myToDo }}
            <br>
        </span> -->
    </div>

</template>

<script>

import TodoItem from "@/components/ToDo/TodoItem";

export default {
    name: 'TodoList',
    
    // data() {
    // },

    props: {
        toDo: {
            type: Array,
            required: true
        }
    },

    components: {
        TodoItem,
    },

    methods: {
        // delToDo (index) {
        //     this.toDo.splice (index, 1)
        //     if (this.toDo.length < 10) 
        //     this.x = false;
        // }

        delToDoItem(ev) {
            this.$emit("delToDoList", ev)
            console.log('ev - TodoList.vue --> '+ ev);
         }
    },
}

</script>