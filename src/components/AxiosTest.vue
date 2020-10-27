<template>
  <div class="axios-test">
    <h1>Axios test</h1>
    <div>{{content}}</div>
    <button @click="loadContent">Load some content</button>
  </div>
</template>

<script>
import axios from "axios"
import {ref} from "vue"

export default {
  name: 'AxiosTest',
  setup() {
    const content = ref("This is the initial content");

    function loadContent() { 
      axios.get('https://api.github.com/users/phantomjs').then(res => {
        this.content = res
      })
    }
    return { content, loadContent };
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/** */
</style>
