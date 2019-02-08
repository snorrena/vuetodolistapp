<template>
    <header class="header">
        <h1>TodoList</h1>
        <div id="nav">
            <!--router-links are vue router routes defined in the router.js file
            the path / defaults to load the Home component
            -->

      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    </header>
</template>

<script>
export default {
    name: "Header"
}
</script>

<style scoped>
    /*scoped style sheet only applies to the template defined in this file*/
    .header{
        background: #333;
        color: #fff;
        text-align: center;
        padding: 10px;
    }
    .header a{
        color: #fff;
        padding-right: 5px;
        text-decoration: none;
    }
</style>
