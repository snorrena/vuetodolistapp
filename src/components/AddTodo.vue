<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add Todo...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
//import uuid from 'uuid';
export default {
    name: "AddTodo",
    data(){
        return {
            title: ''
        }
    },
    methods: {
        //prevents the default behaviour
        addTodo(e){
            e.preventDefault();
            const newTodo = {
                //generated a id from uuid
            //id: uuid.v4(),
            title: this.title,
            completed: false
        }
        //send up to the parent. the new todo is then available to the home component where addtodo is embedded
        this.$emit('add-todo', newTodo);
        //clears the title field on submit of the new todo
        this.title = '';
        }
        
    }
}
</script>

<style scoped>
form {
    display: flex;
}
input[type="text"]{
    flex: 10;
    padding: 5px;
}
input[type="submit"]{
    flex: 2;
}
</style>


