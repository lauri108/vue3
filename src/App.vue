<template>
  <div>
    <h1>My Event</h1>
    <p>Capacity: {{ capacity }}</p>
    <button @click="increaseCapacity()">Increase Capacity</button>
    <axios-test />
  </div>
</template>

<script>
import { ref } from "vue";
import AxiosTest from "./components/AxiosTest" 

export default {
  components: {
    AxiosTest
  },

  // Below setup() function is an example of Composition API
  setup() {
    const capacity = ref(3);

    function increaseCapacity() { 
      capacity.value++;
    }
    return { capacity, increaseCapacity };
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
