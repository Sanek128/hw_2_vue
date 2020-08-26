<template>

    <div>
        <!-- <h1>AddTodo</h1> -->
        <div>
            <button @click="newToDo" :class="none" style="margin-right: 3px"> Добавить задачу </button>
            <h2 v-if="x" style = "background-color: red; text-align: center"> !!!  Слишком много задач, выполни что-то  !!! </h2>
            <input v-model = "addToDo" type = "text" style="width: 350px" placeholder = "Новая задача">
        </div>    
    </div>

</template>

<script>

export default {
    name: 'AddTodo',

    data() {

        return {
        addToDo: '',
        // x: false,
        }
    },

    props: {
        toDo: {
            type: Array,
            required: true
        },
        x: {
            type: Boolean,
            required: true
        }

    },

    methods: {

        newToDo() {
            if (this.addToDo.length > 0)
                {
                    // this.toDo.push (this.addToDo)
                    // this.addToDo = '';
                    this.$emit("newToDoS", this.addToDo)
                    this.addToDo = '';
                }
            // if (this.toDo.length >= 10) 
            //     {this.x = true;} else {this.x = false}
        }
    },

    computed: {

        none() {
            if (this.toDo.length >= 10)
            {
                return 'none'; 
            }
            else 
            { return ''}
        }
    }
}

</script>