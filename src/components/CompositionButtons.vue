<template>
    <div>
        <h1>Composition API events</h1>
        <p>Capacity: {{ capacity }}</p>
        <button class="btn btn-success mr-3" @click="changeCapacity('-')">-</button>
        <button class="btn btn-success" @click="changeCapacity('+')">+</button>
    </div>
</template>
<script>
import { ref } from "vue";

export default {
    // Below setup() function is an example of Composition API
    setup() {
      const capacity = ref(3);
  
      function changeCapacity(plusOrMinus) {
        capacity.value = eval(`${capacity.value} ${plusOrMinus} 1`);
      }
      return { capacity, changeCapacity };
    }
}
</script>