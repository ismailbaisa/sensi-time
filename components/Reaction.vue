<template>
  <div>
   Your reaction time is {{yourReaction}}
  </div>
</template>
<script>
  export default {
    props: ['score'],
    computed: {
      yourReaction() {
        return this.score;
      }
    }
  }

</script>
