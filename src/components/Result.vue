<template>
  <div class="results">
    <p class="score">
      Your Reaction Time: <span>{{ score }}</span> ms
    </p>
    <p class="rank">
      Your Rank: <span>{{ rank }}</span>
    </p>
  </div>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return { rank: null };
  },
  mounted() {
    if (this.score < 300) {
      this.rank = "Ninja Fingers";
    } else if (this.score < 450) {
      this.rank = "Rapid Reflexes";
    } else {
      this.rank = "Snail Pace";
    }
  },
};
</script>

<style scoped>
.results {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.score {
  font-size: 2rem;
  color: #fff;
  background-color: #000;
  padding: 1rem;
  border-radius: 10px;
}
.rank {
  font-size: 1.5rem;
  color: #fff;
  background-color: #000;
  padding: 1rem;
  border-radius: 10px;
}
.score span,
.rank span {
  color: #b22;
  font-weight: bold;
}
</style>
