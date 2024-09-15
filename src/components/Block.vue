<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    <h2>Click here</h2>
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
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
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style scoped>
.block {
  width: 500px;
  height: 300px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 2rem;
  background-color: #000;
  margin: 10rem auto;
  cursor: pointer;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
}
.block h2 {
  font-size: 2rem;
  color: #fff;
  margin: 0;
}
</style>
