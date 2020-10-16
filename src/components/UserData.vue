<template>
  <div>
    <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3>
  </div>
</template>

<script>
import { computed, inject } from 'vue'

export default {
  props: ['firstName','lastName'],
  // computed: {
  //   userName() {
  //     return `${this.firstName} ${this.lastName}`
  //   }
  // }

  // props are reactive in setup
  setup(props, context) {
    const uName = computed(function() {
      // we can't use 'this' (setup() is called too early in lifecycle)
      // but we can use 'props' instead
      return `${props.firstName} ${props.lastName}`
    })

    // we can use provide and inject in Composition API - BEST PRACTICE: do not change injected values 
    // (change them in module/component where it is provided)
    const age = inject('userAge')

    // we see attrs, emit, slots
    console.log(context)

    // you can use context.emit instead of this.$emit
    context.emit('save-data')

    // expose injected age to template
    return { userName: uName, age: age }

  }
}
</script>