<template>
  <section class="container">
    <h2>{{ user.name }}</h2>
    <h3>{{ user.age }}</h3>
  </section>
</template>

<script>
import { ref } from 'vue'

export default {
  // NEW WAY: (Composition API)
  setup() {
    // const uName = ref('Maximilian') // create a reference (a reactive value we can use in our template)
    // const uAge = ref(31)

    const user = ref({
      name: 'Maximilian',
      age: 31
    })

    setTimeout(function() {
      // uName.value = 'Max'
      // uAge.value = 32
      user.value.name = 'Max'
      user.value.age = 32
    }, 2000)

    // passing 'raw' object (user) lets template use this in a reactive way
    return { userName: user.value.name, age: user.value.age, user: user } // return whatever you want to expose to template
  },
  // OLD WAY: (Options API)
  // data() {
  //   return {
  //     userName: 'Maximilian',
  //   }
  // },
}
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>