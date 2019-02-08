<template>
<!--if the todo item is complete a class style to underline is attached-->
<div class="todo-item" v-bind:class="{'is-complete':todo.completed}
">

<p>
<!--if the check box is changed the today complete boolean is flipped thought call to the markCompleted method-->
<input type="checkbox" v-on:change="markComplete">
<!--outputs the property of title in todo-->
{{todo.title}}
<!--emits the todo id on button click-->
<button @click="$emit('del-todo', todo.id)" class="del">X</button></p>
</div>

</template>

<script>
export default {
name: "Todoitem",
//the todoitem component includes the property todo
props: ["todo"],

methods: {
    //method to flip the todo completed boolean on change of the associated checkbox
    markComplete(){
        this.todo.completed = !this.todo.completed;
    }
}

}
</script>

<style scoped>

.todo-item{
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
}

.is-complete {
    text-decoration: line-through;
}

.del{
    background: #ff0000;
    color: #fff;
    border:none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
}

</style>



