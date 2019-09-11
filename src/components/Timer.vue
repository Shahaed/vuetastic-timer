<template>
    <div id="timer">
      <div class="level"> 
        <div class="block">
          <p class="text">minutes</p>
          <p id="minutes">{{ minutes }}</p>
          
        </div>
        <div class="block" style="color: #9834eb;">
          <p class="text" >seconds</p>
          <span id="seconds">{{ seconds }}</span>
          
        </div>
      </div>
      
      <TimerControls
        v-on:start-timer="startTimer"
        v-on:stop-timer="stopTimer"
        v-on:reset-timer="resetTimer"
        v-on:edit="editTimer"
        v-bind:timer="timer"
        v-bind:resetButton="resetButton"/>

      <EditForm v-bind:edit="edit" v-on:set-time="setTime"/>
    </div>
</template>

<script>
import TimerControls from "./TimerControls.vue";
import EditForm from "./EditForm";

export default {
  components: {
    TimerControls,
    EditForm
  },
    data() {
        return {
        timer: null,
        initalTime: (25 * 60),
        totalTime: (25 * 60),
        resetButton: false,
        edit: false
        }
    },
  methods: {
    startTimer() {
      this.timer = setInterval(() => this.countdown(), 1000);
      this.resetButton = true;
    },
    stopTimer() {
      clearInterval(this.timer);
      this.timer = null;
      this.resetButton = true;
    },
    resetTimer() {
      this.totalTime = this.initalTime;
      clearInterval(this.timer);
      this.timer = null;
      this.resetButton = false;
    },
    padTime(time) {
      return (time < 10 ? '0' : '') + time;
    },
    countdown() {
      if(this.totalTime >= 1){
        this.totalTime--;
      } else{
        this.totalTime = 0;
        this.resetTimer()
      }
    },
    editTimer() {
      this.edit = !this.edit
    },
    setTime(newTime) {
      this.initalTime = newTime * 60;
      this.totalTime = newTime * 60;
      clearInterval(this.timer);
      this.timer = null;
      this.resetButton = false;
    }
  },
  computed: {
    minutes() {
      const minutes = Math.floor(this.totalTime / 60);
      return this.padTime(minutes);
    },
    seconds() {
      const seconds = this.totalTime - (this.minutes * 60);
      return this.padTime(seconds);
    }
  }
}
</script>

<style scoped>
@import url(https://fonts.googleapis.com/css?family=Roboto+Condensed:400|Roboto:100);

#timer {
  color: #1abc9c;
  font-size: 200px;
  font-family: 'Roboto', serif;
  line-height: 1;
  position: auto;
  padding-top: 15%;
  padding-bottom: 15%;
  max-height: 100%;
}

.block {
    display: flex;
    flex-direction: column-reverse;
    margin: 20px;}

.text {
    color: #ffffff;
    font-size: 40px;
    font-family: 'Roboto Condensed', serif;
    font-weight: 400;
    margin-top:10px;
    margin-bottom: 10px;
    text-align: center;
}

</style>