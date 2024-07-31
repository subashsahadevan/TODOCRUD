
<template>
  <div>
   <Navbar/>
   <Todos/>
  </div>

</template>
<script>
import Navbar from './components/Navbar.vue';
import Todos from './components/Todos.vue';
export default{
  components:{
    Navbar,
    Todos
  }
}

</script>



<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
