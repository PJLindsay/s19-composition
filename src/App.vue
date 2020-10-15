<template>
  <section class="container">
    <!-- reactive() approach -->
    <!-- <h2>{{ user.name }}</h2>
    <h3>{{ user.age }}</h3> -->


    <!-- ref() approach -->
    <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3>

    <button @click="setAge">Change Age</button>
    <div>
        <!-- <input type="text" placeholder="First Name" @input="setFirstName" />
        <input type="text" placeholder="Last Name" @input="setLastName" /> -->

        <!-- 2-way binding still works in template same way with Composition API (without needing .value) -->
        <input type="text" placeholder="First Name" v-model="firstName" />
        <input type="text" placeholder="Last Name" v-model="lastName" />

    </div>
  </section>
</template>

<script>
import { ref, computed, watch } from 'vue'

export default {
  // NEW WAY: (Composition API)
  setup() {

    /* DATA replacement */

    // ref() approach
    // const uName = ref('Maximilian') // create a reference (a reactive value we can use in our template)
    const uAge = ref(31)
    const firstName = ref('')
    const lastName = ref('')

    // computed property is a ref() as well, but it's READ-ONLY
    const uName = computed(function()  {
      return `${firstName.value} ${lastName.value}`
    })

    // this is how we use watch in Composition API
    // whenever uAge or uName changes, this will execute
    watch([uAge, uName], function(newValues, oldValues) {
      console.log('Old age: ' + oldValues[0])
      console.log('New age: ' + newValues[0])

      console.log('Old name: ' + oldValues[1])
      console.log('New name: ' + newValues[1])
    })


    // reactive() approach
    // const user = reactive({
    //   name: 'Maximilian',
    //   age: 31
    // })

    function setNewAge() {
      // ref() approach
      uAge.value = 32

      // reactive() approach
      // user.age = 32
    }

    // function setFirstName(event) {
    //   firstName.value = event.target.value
    // }

    // function setLastName(event) {
    //   lastName.value = event.target.value
    // }

    // setTimeout(function() {
    //   // ref() approach
    //   // uName.value = 'Max'
    //   // uAge.value = 32

    //   // reactive() approach
    //   user.name = 'Max'
    //   user.age = 32
    // }, 2000)

    // refs() approach
    return {
      userName: uName,
      age: uAge,
      setAge: setNewAge,
      firstName,
      lastName
    } // return whatever you want to expose to template

    // reactive() approach
    // passing 'raw' object (user) lets template use this in a reactive way
    // return { user: user, setAge: setNewAge } // setAge is a 'pointer' to method
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