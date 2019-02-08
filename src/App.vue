<template>
  <div id="app">
    <!--the header component is injected into the template here-->
    <Header />
    
    <!--the vue router is injected into the template here-->
    <!--this components defines paths/routes used by the app and are defined in the router.js file-->
    <router-view/>
  </div>
</template>

<script>
  //import of the header for injection into the app
import Header from './components/layout/Header';
//export of the app with embedded component header
export default {
  name:"app",
  components:{
    Header
  }
}
</script>


<style>
  /* styles here may be applied globally to the application*/
   * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }
  .btn{
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }
  .btn:hover{
    background: #666;
  }
</style>
