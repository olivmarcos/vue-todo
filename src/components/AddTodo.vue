<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add Todo..." class="input">
            <input type="submit" value="Submit" class="btn"> 
        </form>
    </div>
</template>

<script>
import uuid from 'uuid';
export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();

                const newTodo = {
                    title: this.title,
                    completed: false
                }
                // send to parent

                this.$emit('add-todo', newTodo);
                this.title = '';
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
        margin-bottom: 2rem;
        justify-content: space-between;
    }

    input[type="text"] {
        flex: 10;
        padding: 5px;
    }

    .btn {
        width: 4rem;
        height: 3.5rem;
        background-color: white;
        border: 0;
        outline: 0;
        color: rgb(113, 89, 193);
        box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.2);
        cursor: pointer;
        margin-left: 0.5em;
    }

    .input {
        width: 25rem;
        height: 3.5rem;
        border: 0;
        outline: 0;
        box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.2);
        padding: 1.5rem;
        margin-bottom: 1rem;
    }

</style>