<template>
  <h4>{{ state.count }} x 2 = {{ getters.times2 }}</h4>
  <button @click="inc(1)">increment</button>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import counterStore from '@/store/counter';

export default defineComponent({
  setup() {
    const { state, getters, inc } = counterStore;
    return { state, getters, inc };
  },
});
</script>
