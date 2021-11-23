<template>
  <div v-if="!userStore.getters.isLoggedIn">
    <FormLogin />
    <counter />
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted } from 'vue';
import FormLogin from './components/FormLogin.vue';
import Counter from './components/Counter.vue';
import userStore from '@/store/user';

export default defineComponent({
  name: 'App',
  components: {
    FormLogin,
    Counter,
  },
  setup() {
    onMounted(() => userStore.getUser);
    return { userStore };
  },
});
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
