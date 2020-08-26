<template>

    <div>
        
        <button @click="oneDelToDo" style="margin-top: 2px"> Выполено </button>
        <span>
            {{oneToDo}}
        </span>

    </div>

</template>

<script>

export default {
    name: 'TodoItem',

    // data() {
    // },
    props: {
        oneToDo: {
            type: String,
            required: true
        }
    },

    methods: {
      oneDelToDo() {
        this.$emit("delToDoItem", this.oneToDo);
      }
    }
}

</script>