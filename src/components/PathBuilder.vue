<template>
  <section>
    <div>
      <h1>s3 path builder</h1>
    </div>
    <div>
      <Button :label="'Add a part'" @click="addPart"/>
    </div>
    <section v-for="(value, id) in parts" :key="id">
      <PathBuilderPart :id="id" :value="value" @input="updatePart" @delete="removePart"/>
    </section>
  </section>
</template>

<script>
import PathBuilderPart from './PathBuilderPart'
import Button from './Button'
import { cloneDeep } from 'lodash'

export default {
  /**
   */
  name: 'PathBuilder',
  /**
   */
  components: {
    PathBuilderPart,
    Button
  },
  props: ['value'],
  /**
   */
  data () {
    return {
      parts: this.splitPath(this.value)
    }
  },
  /**
   */
  computed: {
    /**
     */
    fullPath () {
      return `s3://${this.parts.join('/')}`
    }
  },
  methods: {
    /**
     */
    nextState (object, fn) {
      return fn(cloneDeep(object))
    },
    /**
     */
    splitPath (fullPath) {
      return fullPath.replace('s3://', '').split('/')
    },
    /**
     */
    addPart () {
      this.parts.push('')
    },
    /**
     */
    updatePart (partObject) {
      this.parts = this.nextState(this.parts, (nextState) => {
        nextState[partObject.id] = partObject.value
        return nextState
      })
    },
    /**
     */
    removePart (id) {
      this.parts = this.nextState(this.parts, (nextState) => {
        nextState.splice(id, 1)
        return nextState
      })
    }
  },
  watch: {
    /**
     */
    parts (newValue) {
      this.$emit('input', this.fullPath)
    },
    /**
     */
    value (newValue) {
      this.parts = this.splitPath(this.value)
    }
  }
}
</script>

<style scoped>
</style>
