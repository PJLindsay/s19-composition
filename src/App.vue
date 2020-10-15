<template>
  <section class="container">
    <h2>{{ user.name }}</h2>
    <h3>{{ user.age }}</h3>
  </section>
</template>

<script>
import { reactive } from 'vue'

export default {
  // NEW WAY: (Composition API)
  setup() {
    // ref() approach
    // const uName = ref('Maximilian') // create a reference (a reactive value we can use in our template)
    // const uAge = ref(31)

    // reactive() approach
    const user = reactive({
      name: 'Maximilian',
      age: 31
    })

    setTimeout(function() {
      // ref() approach
      // uName.value = 'Max'
      // uAge.value = 32

      // reactive() approach
      user.name = 'Max'
      user.age = 32
    }, 2000)

    // refs() approach
    // return { userName: user.value.name, age: user.value.age, user: user } // return whatever you want to expose to template

    // reactive() approach
    // passing 'raw' object (user) lets template use this in a reactive way
    return { user: user }
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