<template>
  <div class="block">
    <p>Reaction Time - {{ score }} in ms</p>
    <p class="rank">{{ rank }}</p>
  </div>
</template>

<script>
export default {
  props: ['score'],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = 'Ninja Fingers';
    } else if (this.score < 400) {
      this.rank = 'Rabbit Fingers';
    } else {
      this.rank = 'Snail Fingers';
    }
  },
};
</script>

<style>
.block {
  width: 240px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
.rank {
  font-size: 1.4rem;
  color: rgb(0, 0, 0);
  font-weight: bold;
}
</style>
