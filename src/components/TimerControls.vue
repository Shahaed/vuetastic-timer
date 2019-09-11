<template>
<div class="controls">

    <button size="1.5" id="start"
      class="button is-text is-large"
      v-if="!timer"
      v-on:click="$emit('start-timer')">
          <play-icon size="1.5x" class="custom-class"></play-icon>
    </button>
    <!--     Pause Timer -->
    <button
      id="stop"
      class="button is-text is-large"
      v-if="timer"
      @click="$emit('stop-timer')">
        <pause-icon size="1.5x" class="custom-class"></pause-icon>
    </button>
<!--     Restart Timer -->
    <button
      id="reset"
      class="button is-text is-large"
      v-if="resetButton"
      @click="$emit('reset-timer')">
        <rotate-ccw-icon size="1.5x" class="custom-class"></rotate-ccw-icon>
    </button>
<!-- EDIT TIMER -->
    <button size="1.5" id="edit"
      class="button is-text is-large"
      v-if="!timer"
      v-on:click="$emit('edit')">
        <edit-2-icon size="1.5x" class="custom-class"></edit-2-icon>
    </button>

</div>
</template>

<script>
import { PlayIcon, PauseIcon, RotateCcwIcon, Edit2Icon } from 'vue-feather-icons'

export default {
    name: "TimerControl",
    components: { PlayIcon, PauseIcon, RotateCcwIcon, Edit2Icon },
    props: {
      timer: Number,
      resetButton: Boolean
    }
}
</script>

<style scoped>
  .controls {
    align-items: center;
    bottom: 0;
    display: flex;
    justify-content: center;
    left: 0;
    right: 0;
    top:0;
  }
  .custom-class {
    display: flex;
    color: orange;
    transition: 0.1s ease;
  }
  .custom-class:hover {
    cursor: pointer;
    transform: scale(1.2);
    background:transparent;
  }

</style>