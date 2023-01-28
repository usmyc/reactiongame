<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
   click me
  </div>
</template>

<script>
export default {
  props: ["delay"],
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.showReaction = true;
      this.$emit("end", this.reactionTime);
    },
  },
  data() {
    return {
      showBlock: false,
      showReaction: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  updated() {
    if (!this.showBlock) {
      this.stopTimer();
    }
  },
};
</script>

<style scoped>
.block {
  width: 400px;
  border-radius: 20px;
  background-color: rgb(126, 238, 160);
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
