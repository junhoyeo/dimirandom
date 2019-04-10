<script>
export default {
  name: 'app',
  created () {
    this.initWeights()
  },
  data () {
    return {
      random: 1,
      weights: [],
      variationWeight: 0.2,
      studentNumber: 35,
    }
  },
  methods: {
    initWeights () {
      this.weights = Array(this.studentNumber).fill(1)
    },
    updateRandom () {
      let selected = this.weightedRandom(this.weights)
      this.weights[selected] += this.variationWeight
      this.weights[selected] = Number(this.weights[selected].toFixed(1))
      this.random = selected + 1
    }
  }
}
</script>

<template>
  <div id="app">
    <div
      class="random"
      @click="updateRandom"
    >
      <span>{{ random }}</span>
    </div>
    <pre>
      {{ weights }}
    </pre>
  </div>
</template>

<style lang="scss" scoped>
.random {
  font-size: 3em;
  user-select: none;
  cursor: pointer;
  width: 1.5em;
  background-color: rgb(240, 240, 240);
  color: black;
  text-align: center;

  span {
    display: inline-block;
    vertical-align: middle;
  }
}
</style>
