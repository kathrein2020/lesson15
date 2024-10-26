<script>
  export default {
    name: 'MyButton',
    emits: ['click-event'],
    methods: {
      addCounter() {
        this.$emit('click-event', 6)
      }
    }
  }
</script>
<template>
  <button @click="addCounter">Увеличить значение счетчика</button>
</template>