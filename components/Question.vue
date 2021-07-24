<template>
  <div class="flex flex-fd-c flex-ai-c" v-if="showThis">
    <div class="flex flex-fd-c flex-ai-c">
      <h1>What color is this?</h1>
      <div v-html="quiz"></div>
      <h2>{{result}}</h2>
    </div>
    <div class="flex flex-jc-sb ma-10">
      <button class="button button__default ma-10" @click="myAnswer(0)">White</button>
      <button class="button button__gray ma-10" @click="myAnswer(1)">Gray</button>
      <button class="button button__success ma-10" @click="myAnswer(2)">Green</button>
      <button class="button button__warning ma-10" @click="myAnswer(3)">Yellow</button>
      <button class="button button__danger ma-10" @click="myAnswer(4)">Red</button>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['delay'],
    data() {
      return {
        showThis: false,
        timer: null,
        reactionTime: 0,
        colorAnswer: 0,
        result: '',
      }
    },
    mounted() {
      setTimeout(() => {
        this.showThis = true
        this.startTimer()
        this.randomColor(4)
      }, this.delay)
    },
    methods: {
      startTimer() {
        this.timer = setInterval(() => {
          this.reactionTime += 10
        }, 10);
      },
      myAnswer(answer) {
        clearInterval(this.timer)
        this.$emit('end', this.reactionTime)
        if (this.colorAnswer == answer) {
          this.result = 'Congrats you are not colorblind'
        } else {
          this.result = 'You should see a doctor..'
        }
      },
      randomColor(max) {
        this.colorAnswer = Math.floor(Math.random() * max);
      }
    },
    computed: {
      quiz() {
        switch (this.colorAnswer) {
          case 0:
            return '<h2 style="color:blue;">blue</h2>'
          case 1:
            return '<h2 style="color:gray;">gray</h2>'
          case 2:
            return '<h2 style="color:green;">green</h2>'
          case 3:
            return '<h2 style="color:yellow;">yellow</h2>'
          case 4:
            return '<h2 style="color:red;">red</h2>'
        }
      }
    }
  }

</script>
