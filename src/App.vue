<template>
  <v-app>
    <h2 class="text-center mt-10">Todo<span class="font-weight-thin">List</span></h2>
    <v-main>
      <transition-group name="slide" type="animation" appear>
        <Input key='input' :todo="todos"/>
        <List key='list' :todos="todos" :deleteTodo="deleteTodo"/>
      </transition-group>
    </v-main>
  </v-app>
</template>

<script>
import Input from './components/Input.vue';
import List from './components/List.vue';

export default {
  name: 'App',

  components: {
    Input,
    List
  },

  data: () => ({
    todos: [],
  }),

  methods: {
    deleteTodo(index) {
      this.todos.splice(index, 1)
    }
  }
};
</script>

<style scoped>
  .slide-enter {
    opacity: 0;
  }
  .slide-enter-active {
    animation: slide-in 1s ease-out forwards;
    transition: opacity .5s;
  }
  .slide-leave-active {
    transition: opacity .5s;
    opacity: 0;
  }

  @keyframes slide-in {
    from {
      transform: translateY(20px);
    }
    to {
      transform: translateY(0);
    }
  }
</style>
