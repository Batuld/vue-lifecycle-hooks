<template>
  <div ref="greeting">Hello vue Developers !</div>
  <span>comment/uncomment me to see beforeUpdate/updated hook's reactivity</span>
    <div>
      <p>{{ val }} Random Number = {{ count }} times</p>
      <!-- Inline handlers -->
      <button @click="val = Math.random(0, 100)">Click to Change</button>
      
      <!-- Method Handlers -->
      <!-- <button @click="calculate()">Click Me</button> -->

      <button @click="greet()">Greet</button>
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
    
    const type = ref('hello developers')
    const root = ref(null)
    const count = ref(0)
    const vals = ref(0)

    console.log(`Value of val is: ${val.value}`)

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

    onBeforeMount(() => {
      console.log(type.value)
    })
    onMounted(() => {
      console.log(root.value)
      // console.log('mount')
      window.addEventListener('resize', someMethod)
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
      window.removeEventListener('resize', someMethod)
    })
    onUnmounted(() => {
      console.log('unmounted')
    })

    return {
      val, root, count, greet
    }
  },
}
 
</script>
<style scoped>
.read-the-docs {
  color: #888;
}
</style>
