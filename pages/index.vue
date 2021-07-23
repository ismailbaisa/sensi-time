<template>
  <div class="flex flex-fd-c vh-95">
     <div class="flex flex-jc-c mb-20 mt-20" @click="start">
        <ButtonDefault stylings="button__danger button__round pxh-200 pxw-200" :playing="isPlaying">Click Me!</ButtonDefault>
    </div>
    <div class="flex flex-jc-c flex-fd-c flex-ai-c hh-100">
        <Question v-if="isPlaying" :delay="isDelaying"></Question>
        <!-- <div v-if="showScore"> {{isScore}} </div> -->
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isPlaying: false,
      isDelaying: null,
      isScore: null,
      showScore: false,
    }
  },
  methods: {
    start() {
      this.isDelaying = 2000 + Math.random() * 5000;
      this.isPlaying = true
      // this.showScore = false
    },
    // endGame(){
    //    this.isPlaying = false
    //    this.showScore = true
    // }
  }

}
</script>

<style>

</style>