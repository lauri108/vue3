<template>
  <div class="axios-test">
    <h1>Axios test</h1>
    <div class="container w-75">
    <form>
      <div class="form-group">
        <label for="exampleFormControlInput1">Email address</label>
        <input type="text" v-model="usernameToSearch" class="form-control" id="exampleFormControlInput1" placeholder="Search for Github users...">
      </div>
      <button type="submit" class="btn btn-success" @click.prevent="searchGithubUsers">Search for users</button>
    </form>
    </div>
    <div class="container w-75" v-if="listOfUsers.length > 0">
      <div v-for="user in listOfUsers" v-bind:key="user.id" class="card" style="width: 18rem;">
        <img :src="user.avatar_url" class="card-img-top" alt="...">
        <div class="card-body">
          <h5 class="card-title">USER: {{user.login}}</h5>
          <p class="card-text">ID: {{user.id}}</p>
          <a :href="user.html_url" target="_blank" class="btn btn-primary">Go to {{user.login}}'s profile</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios"
import {ref} from "vue"

export default {
  name: 'AxiosTest',
  setup() {
    const listOfUsers = ref([]);
    const usernameToSearch = ref("");
    function searchGithubUsers() { 
      axios.get(`https://api.github.com/search/users?q=${this.usernameToSearch}`).then(response => {
        this.listOfUsers = response.data.items
      })
    }
    
    return { listOfUsers, searchGithubUsers, usernameToSearch };
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/** */
</style>
