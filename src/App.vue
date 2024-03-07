<template>
  <div>
    <Navbar />
    <Main />
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue';
import Main from './components/Task.vue';

export default {
  name: 'App',
  components: {
    Navbar,
    Main,
  }
}
</script>


