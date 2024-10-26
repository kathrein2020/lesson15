<script>
  export default {
    name: 'MyButton',
    emits: ['click-event'],
    methods: {
      toggleText() {
        this.$emit('click-event')
      }
    }
  }
</script>
<template>
  <button @click="toggleText">   
    <slot></slot>
  </button>
</template>