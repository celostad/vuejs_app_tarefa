<template>
  <div id="app">
    <header> Minhas tarefas </header>
    <CTask/>

  </div>
</template>

<script>
import CTask from './components/CTask';
export default {
  name: 'App',
  components:{
    CTask
  }
}
</script>

<style scoped>
  header{
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 80px;
    font-size: 40px;
    color: #FFF;
  }
</style>
