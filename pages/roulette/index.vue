<template>
  <div class="blog-page" :class="{ 'redbg': timeLeft === 0, 'greenbg': timeLeft > 0 }">
    <div>I'm a blog page</div>
    <input v-model.number="number1" type="number" />
    <input v-model.number="number2" type="number" />
    <input :value="result" type="number" readonly />
    <button @click="performcalc('plus')">Calc</button>
    <button @click="clearall()"> Clear </button>
    <button @click="performcalc('pom')">Pomnozeno</button>
    <button @click="performcalc('min')">Minus</button>
    <div>Timer: {{ timeLeft }}</div>
    <button @click="startTimer()">Start timer</button>
    <button @click="startTimer()" :disabled="timeLeft === 0">Place bet</button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      number1: 0,
      number2: 0,
      result: 0,
      timeLeft: 10,
      timeLeft2: 10
    }
  },
  methods: {
    performcalc (operator) {
      if (operator === 'plus') {
        const result = this.number1 + this.number2
        this.result = result
      } else if (operator === 'pom') {
        const result = this.number1 * this.number2
        this.result = result
      } else if (operator === 'min') {
        const result = this.number1 - this.number2
        this.result = result
      }
    },
    clearall () {
      this.result = 0
      this.number1 = 0
      this.number2 = 0
    },
    startTimer () {
      this.timeLeft = 10
      let intervalval = null
      const fn = () => {
        if (this.timeLeft === 0) {
          this.startTimer2()
          clearInterval(intervalval)
          return
        }
        this.timeLeft = this.timeLeft - 1
      }
      intervalval = setInterval(fn, 1000)
    },
    startTimer2 () {
      let interval2 = null
      this.timeLeft2 = 10
      interval2 = setInterval(() => {
        if (this.timeLeft2 === 0) {
          this.startTimer()
          clearInterval(interval2)
          return
        }
        this.timeLeft2 = this.timeLeft2 - 1
      }, 1000)
    }
  }
}
</script>
<style>
.redbg {
  background-color: red;
}
.greenbg {
  background-color: green;
}
</style>
