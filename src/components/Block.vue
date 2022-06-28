<template>
  <div @click="stopTimer" class="block" v-if="showBlock">Click Me!</div>
</template>

<script>
export default {
  props: ['delay'],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    //starting the timmer
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay); // when the component is mounted we will wait the delay time and will wait till the green block till appear
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10; // in millisecond
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      console.log(this.reactionTime);
      this.$emit('end', this.reactionTime); // the name of our costume event and the data
    },
  },
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
