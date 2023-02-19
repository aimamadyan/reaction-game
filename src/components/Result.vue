<template>
  <p>Reaction time: {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  name: "Result",
  props: ['score'],
  data() {
    return {
      rank: null
    }
  },
  mounted() {
    if (this.score < 250) {
      this.rank = 'Blazing Flash'
    } else if (this.score < 400) {
      this.rank = 'Rapid Reflex'
    } else {
      this.rank = 'Snail finger'
    }
  }
}
</script>

<style scoped>
  .rank {
    font-size: 1.4em;
    color: #0faf87;
    font-weight: bold;
  }
</style>