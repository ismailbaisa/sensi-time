<template>
  <div>
    <button type="button" class="button" :disabled="disabled" :class="classes">
      <slot></slot>
    </button>
  </div>
</template>
<script>
  export default {
    props: ['stylings', "playing"],
    computed: {
      classes() {
        return this.stylings;
      },
      disabled() {
        return this.playing;
      }
    }
  }

</script>
