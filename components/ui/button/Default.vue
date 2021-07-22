<template>
  <div>
    <button type="button" class="button" :class="classes">
      <slot></slot>
    </button>
  </div>
</template>
<script>
  export default {
    name: 'subtitle',
    props: ['stylings'],
    computed: {
      classes() {
        return this.stylings;
      }
    }
  }

</script>
