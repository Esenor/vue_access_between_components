<template>
  <div id="app">
    <PathBuilder v-model="s3Url"/>
    <div>
      <pre>{{ s3Url }}</pre>
    </div>
    <div>
      <Button :label="'Reset path'" @click="resetDefaultUrl"/>
    </div>
  </div>
</template>

<script>
import PathBuilder from './components/PathBuilder'
import Button from './components/Button'
const S3_DEFAULT_URL = 's3://demo.io/assets/webapp/redering-engine/products/'

export default {
  /**
   */
  name: 'App',
  /**
   */
  components: {
    PathBuilder,
    Button
  },
  /**
   */
  data () {
    return {
      s3Url: S3_DEFAULT_URL
    }
  },
  /**
   */
  methods: {
    /**
     */
    resetDefaultUrl () {
      this.s3Url = S3_DEFAULT_URL
    }
  }
}
</script>

<style>
html, body{
  color: slategrey;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
}
</style>
