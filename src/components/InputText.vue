<template>
  <input type="text" class="class" v-model="scopedValue" @input="updateValue"/>
</template>

<script>
export default {
  /**
   */
  name: 'InputText',
  /**
   */
  props: ['value'],
  /**
   */
  data () {
    return {
      scopedValue: this.value
    }
  },
  /**
   */
  methods: {
    /**
     */
    updateValue () {
      this.$emit('input', this.scopedValue)
    }
  },
  /**
   */
  watch: {
    /**
     */
    value (newValue) {
      this.scopedValue = this.value
    }
  }
}
</script>

<style scoped>
  input {
    height: 21px;
  }
  input.error {
    background: red;
    border-color: red;
  }
</style>
