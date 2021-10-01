<template>
    <v-container class="my-6 container" max-width="60vw">
        <hr/>
        <ul class="my-5">
            <transition-group name="slide" type="transition">
                <v-card class="my-5 pa-5 d-flex flex-row justify-space-between" v-for="(todo, index) in todos" :key="index">
                    <li>{{todo}}  {{index}}</li>
                    <v-btn class="deep-purple darken-4" dark small @click="deleteTodo(index)">Remove</v-btn>
                </v-card>
            </transition-group>
        </ul>
    </v-container>
</template>

<script>
export default {
    props: ['todos', 'deleteTodo'],
}
</script>

<style scoped>
    ul {
        list-style: none;
    }

    @media (min-width: 1193px) {
        .container {
            max-width: 40vw !important;
        }
    }

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
  .slide-move {
    transition: transition 1s;
  }
  @keyframes slide-in {
    from {
        transform: translateY(20px);
    }
    to {
        transform: translateY(0);
    }
  }
  @keyframes slide-out {
    from {
        transform: translateY(0);
    }
    to {
        transform: translateY(20px);
    }
  }
</style>