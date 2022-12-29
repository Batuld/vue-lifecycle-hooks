<!-- <template>
  
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/johnsoncodehk/volar" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p> 
</template> -->

<template>
  <div ref="greeting">Hello vue Developers !</div>
  <span>comment/uncomment me to see beforeUpdate/updated hook's reactivity</span>
    <div>
      <p>{{ val }} Random Number = {{ count }} times</p>
      <button @click="val = Math.random(0, 100)">Click to Change</button>
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
      val, root, count
    }
  },
}
 
</script>
<style scoped>
.read-the-docs {
  color: #888;
}
</style>
