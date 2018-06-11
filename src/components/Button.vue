<template>
  <button @click="click">{{ label }}</button>
</template>

<script>
export default {
  /**
   */
  name: 'Button',
  /**
   */
  props: ['label'],
  /**
   */
  data () {
    return {}
  },
  /**
   */
  methods: {
    /**
     */
    click (event) {
      this.$emit('click', this.label)
    }
  }
}
</script>

<style scoped>
  button {
    padding: 5px 10px;
    border: 1px solid slategrey;
    background: slategrey;
    color: white;
    cursor: pointer;
  }
</style>
