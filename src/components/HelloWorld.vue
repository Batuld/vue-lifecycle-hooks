<template>
  <div ref="greeting">Hello vue Developers !</div>
  <!-- <span>comment/uncomment me to see beforeUpdate/updated hook's reactivity</span> -->
    <div>
      <p>{{ val }} Random Number = {{ count }} times</p>
      <!-- Inline handlers -->
      <button @click="val = Math.random(0, 100)">Click to Change</button>
<<<<<<< HEAD
      
      <!-- Method Handlers -->
      <!-- <button @click="calculate()">Click Me</button> -->

      <button @click="greet()">Greet</button>
=======
      <!-- <form @submit.prevent="submitForm()">
        <input type="text"/>
        <button>
          Submit Form
        </button>
      </form> -->
>>>>>>> feb0847a020a5a0cdbf2a4f6f29775d02baee4e0
    </div>

</template>

<script lang="ts">
import { onBeforeMount, onMounted, ref, onBeforeUpdate, onUpdated, onBeforeUnmount, onUnmounted } from 'vue'
export default {
  // setup() {
  //   console.log("I'm setup hook");
  // },
  setup() {
    const val = ref('Hello!')
    // const val = 'hello'
    const type = ref('hello developers')
    const root = ref(null)
    const count = ref(0)

    console.log(`Value of val is: ${val.value}`)

<<<<<<< HEAD
    const someMethod = () => {
      // do smth
    }

    //  Method Handlers 
    const greet = () => {
       alert(`Gretting!`)
  }

    // const calculate = () => {
    //   return Math.random(); 
    // }

=======
>>>>>>> feb0847a020a5a0cdbf2a4f6f29775d02baee4e0
    onBeforeMount(() => {
      console.log(type.value)
    })
    onMounted(() => {
       // console.log('mount')
      console.log(root.value)
    })
    onBeforeUpdate(() => {
      count.value++
      console.log('beforeUpdate')
    })
    onUpdated(() => {
      console.log(`updated() val: ${count.value}`)
    })
    onBeforeUnmount(() => {
      console.log('unmount')
    })
    onUnmounted(() => {
      console.log('unmounted')
    })
    // const submitForm = () => {
    //   alert("submitted");
    // }
    return {
      val, root, count, greet
    }
  },
}
</script>
