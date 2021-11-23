<template>
  <form @submit.prevent="onSubmit">
    <div>
      <label for="username"> Username </label>
      <input type="text" placeholder="Enter username" required />
    </div>
    <div>
      <label for="password"> Password </label>
      <input type="text" placeholder="Enter password" required />
    </div>
    <span class="error">{{ userStore.state.error }}</span>
    <button type="submit">Login</button>
  </form>
</template>
<script lang="ts">
import { defineComponent, reactive } from 'vue';
import userStore from '@/store/user';

export default defineComponent({
  setup() {
    const form = reactive({ username: '', password: '' });

    const onSubmit = () => {
      userStore.login(form.username, form.password);
      form.username = '';
      form.password = '';
    };

    return { form, onSubmit, userStore };
  },
});
</script>
<style scoped>
.error {
  color: red;
}
</style>
