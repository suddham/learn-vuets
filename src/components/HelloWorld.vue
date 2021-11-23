<template>
  <div class="hello">
    <h1>{{ msg }}</h1>

    <div>
      {{ userObj.name }}
      {{ userObj.username }}
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

type UserObjectInterface = {
  name: string;
  username: string;
};

export default defineComponent({
  name: 'HelloWorld',
  props: {
    msg: String,
    userObj: {
      required: true,
      type: Object as () => UserObjectInterface,
    },
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
