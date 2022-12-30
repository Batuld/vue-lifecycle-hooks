<template>
  <div ref="greeting">Hello vue Developers !</div>
  <!-- <span>comment/uncomment me to see beforeUpdate/updated hook's reactivity</span> -->
    <div>
      <p>{{ val }} Random Number = {{ count }} times</p>
      <button @click="val = Math.random(0, 100)">Click to Change</button>
      <!-- <form @submit.prevent="submitForm()">
        <input type="text"/>
        <button>
          Submit Form
        </button>
      </form> -->
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
      val, root, count
    }
  },
}
</script>
