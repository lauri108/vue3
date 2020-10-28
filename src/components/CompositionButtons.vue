<template>
    <div>
        <h1>Composition API events</h1>
        <p>Capacity: {{ capacity }}</p>        
        <button class="btn btn-success mr-3" @click="changeCapacity('-')">-</button>
        <button class="btn btn-success" @click="changeCapacity('+')">+</button>
        <h1>Composition API with Vuex</h1>
        <p>messageFromVuex: {{ messageFromVuex }}</p>        
        <p>centralcount: {{ centralcount }}</p>        
    </div>
</template>
<script>
import { ref, computed } from "vue";
import { useStore } from 'vuex'

export default {
    // Below setup() function is an example of Composition API
    setup() {
        
      const capacity = ref(3);
      const store = useStore()

      const messageFromVuex = computed(()=> store.state.messageFromVuex)
      const centralcount = computed(()=> store.state.count)
  
      function changeCapacity(plusOrMinus) {
        capacity.value = eval(`${capacity.value} ${plusOrMinus} 1`);
      }

      return { 
            capacity, 
            changeCapacity,
            messageFromVuex,
            centralcount
        };
    }
}
</script>