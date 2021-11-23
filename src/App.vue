<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div>
  <router-view />

  <div v-if="!userStore.getters.isLoggedIn">
    <FormLogin />
    <counter />
  </div>
  <router-view />
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
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
