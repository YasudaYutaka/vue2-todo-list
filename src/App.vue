<template>
  <v-app>
    <h2 class="text-center mt-10">Todo<span class="font-weight-thin">List</span></h2>
    <v-main>
      <Input />
    </v-main>
  </v-app>
</template>

<script>
import Input from './components/Input.vue';

export default {
  name: 'App',

  components: {
    Input
  },

  data: () => ({
    //
  }),
};
</script>
