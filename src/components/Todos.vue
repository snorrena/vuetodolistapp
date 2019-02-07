<template>
<div>
    <!--outputs the current list of todos and binds the id as key-->
    <div v-bind:key="todo.id" v-for="todo in todos">
        <!--injection of the Todoitem into the template of todos
            each todo is the list is v-bind and will emit the todo id on execution of the del-todo method
        -->
        <Todoitem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)"/>
    </div>
</div>
</template>

<script>
//the todoitem component is imported from the current folder
import Todoitem from './Todoitem.vue';
//the Todos component is exported including the embedded todoitem component and property todos
export default {
    name: "Todos",
    components: {
        Todoitem
    },
    //makes to todos list available in the template as a property
    props: ["todos"]
}
</script>

<!-- no styles are applied to the template in this file-->
<style scoped>

</style>

