<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col">
          Central stuff: {{count}}<br />
          messageFromVuex: {{messageFromVuex}}
        </div>
        <div class="col">
          <composition-buttons />
          <github-events />
        </div>
        <div class="col"><axios-test /></div>
      </div>
    </div>
    
  </div>
</template>

<script>
import AxiosTest from "./components/AxiosTest" 
import CompositionButtons from "./components/CompositionButtons" 
import GithubEvents from "./components/GithubEvents"
import { computed } from 'vue'
import { useStore } from 'vuex'

export default {
  setup () {
    const store = useStore()
    return {
      messageFromVuex: computed(()=> store.state.messageFromVuex),
      count: computed(()=> store.state.count)
    }
  },
  components: {
    AxiosTest,
    CompositionButtons,
    GithubEvents
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
