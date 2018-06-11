<template>
  <div>
      <span>#{{ this.id }}</span>
      <InputText ref="inputText" :class="{error: hasSpace()}" v-model="scopedValue" @input="updateValue" />
      <Button label="-" @click="removePart()"/>
  </div>
</template>

<script>
import Button from './Button'
import InputText from './InputText'

export default {
  /**
   */
  name: 'PathBuilderPart',
  /**
   */
  components: {
    Button,
    InputText
  },
  /**
   */
  props: ['id', 'value'],
  /**
   */
  data () {
    return {
      scopedValue: this.value
    }
  },
  /**
   */
  computed: {},
  /**
   */
  methods: {
    /**
     */
    hasSpace () {
      return this.scopedValue.indexOf(' ') !== -1
    },
    /**
     */
    updateValue () {
      this.$emit('input', {
        id: this.id,
        value: this.scopedValue}
      )
    },
    /**
     */
    removePart () {
      this.$emit('delete', this.id)
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
  div {
    margin: 5px;
  }
  span {
    display: inline-block;
    padding: 0px 5px;
    border: 1px solid slategrey;
    background: slategrey;
    height: 25px;
    color: white;
    min-width: 30px;
    line-height: 24px;
  }
</style>
