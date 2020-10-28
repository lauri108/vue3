<template>
  <div class="axios-test">
    <h1>Github Events</h1>
    <div class="container w-75">
      <button type="submit" class="btn btn-success" @click.prevent="loadGithubEvents">Load latest 10 push events</button>
    </div>
    <div class="container w-75" v-if="listOfPushEvents.length > 0">
        <div class="list-group">
            <a v-for="event in listOfPushEvents" v-bind:key="event.id" :href="event.repo.url" target="_blank" class="list-group-item list-group-item-action" style="width: 18rem;"><img style="height: 100px" :src="event.actor.avatar_url" /> {{event.actor.login}}</a>
        </div>
    </div>
  </div>
</template>

<script>
import axios from "axios"
import {ref} from "vue"

export default {
  name: 'AxiosTest',
  methods:{

  },
  setup() {
    const listOfPushEvents = ref([]);
    function loadGithubEvents() { 
      axios.get(`https://api.github.com/events`).then(response => {
        this.listOfPushEvents = response.data.filter(item => {
            return item.type === "PushEvent"
        })
      })
    }
    
    return { listOfPushEvents, loadGithubEvents };
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/** */
</style>
