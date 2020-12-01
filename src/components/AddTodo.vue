<template>
    <form @submit="addTodo">
        <input type="text" v-model="title" name="title" placholder="Add to do...">
        <button type="submit" value="Submit" class="btn">ADD TODO</button>
    </form>
</template>

<script>
export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    props: ["todos"],
    methods: {
        addTodo(e) {
            e.preventDefault();

            console.log(this.todos.length)

            const newTodo = {
                id: this.todos.length + 1,
                title: this.title,
                completed: false
            }

            // send via emit
            this.$emit('add-todo', newTodo);
            this.title = '';
        }
    },
}
</script>

<style scoped>
    form{
        display: flex;
    }
    input[type="text"] {
        flex:10;
        padding:5px;
    }
    button[type="submit"]
    {
        flex:2;
    }
</style>