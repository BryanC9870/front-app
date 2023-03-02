<template>    
  <div id="app">      
    <Invoices /> <!--INVOCACIÓN DE COMPONENTE-->
    <router-view></router-view>
  </div>  
</template>    
<script>  // IMPORTACIÓN DE COMPONENTES
  import Invoices from './components/invoices.vue'
  import Details from './components/invoiceDetails.vue'
  export default {    
    name: 'app',    
    components: {      
      Invoices,
    }  
  }  
</script>    
<style>  
  #app {    
    font-family: 'Avenir', Helvetica, Arial, sans-serif;    
    -webkit-font-smoothing: antialiased;    
    -moz-osx-font-smoothing: grayscale;    
    text-align: center;    
    color: #2c3e50;    
    margin-top: 60px;  
  }  
</style>
