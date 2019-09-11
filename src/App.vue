<template>
  <div id="app">
    <Timer/>
  </div>
</template>

<script>
import Timer from './components/Timer.vue'


export default {
  name: 'app',
  components: {
    Timer
  },
  data () {
    return {
      now: new Date()
    }
  }
}
</script>

<style>
#app{
    align-items: center;
    bottom: 0;
    background-color: #34495e;
    display: flex;
    justify-content: center;
    left: 0;
    position: absolute;
    right: 0;
    top:0;
}
</style>
