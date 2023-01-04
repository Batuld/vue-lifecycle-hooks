<template>
  <div ref="greeting">Hello vue Developers !</div>
  <!-- <span>comment/uncomment me to see beforeUpdate/updated hook's reactivity</span> -->
    <div>
      <p>{{ val }} Random Number = {{ count }} times</p>
      <!-- Inline handlers -->
      <button v-on:click="val = Math.random(0, 100)">Click to Change</button>
      
      <!-- Method Handlers -->
      <!-- <button @click="calculate()">Click Me</button> -->

      <button @click="greet($event)">Greet</button>

      <!-- prevent example -->
      <form @submit.prevent="submitForm()">
        <input type="text" />
        <button>
          Submit Form
        </button>
      </form>

      <!-- once example -->
      <button v-on:click.once="clicked">click me</button>
      
      <!-- stop example -->
      <div id="stop-example">
        <h3>without stop propagation</h3>
        <div @click="greet($event)">
          <button @click="greet($event)">Click Me for without stop </button>
        </div>
        <h3>with stop propagation</h3>
        <div @click="greet($event)">
          <button @click.stop="greet($event)">Click Me for with stop</button>
        </div>
      </div>
    </div>

    <!-- self example -->
    <div>
      <div v-on:click="roots">root
        <div v-on:click.self="parent">Parent
          <div v-on:click="child">Child
          </div>
        </div>
      </div>
    </div>

    <!-- Capture example -->
    <div>
      <div @click.capture="clicked($event)">
        <button @click="btnClick">capture</button>
      </div>
    </div>

</template>

<script lang="ts">
import { onBeforeMount, onMounted, ref, onBeforeUpdate, onUpdated, onBeforeUnmount, onUnmounted } from 'vue'
export default {
  setup() {
    const val = ref('Hello!')
    // const val = 'hello'
    const type = ref('hello developers')
    const root = ref(null)
    const count = ref(0)

    console.log("I'm setup hook");
    console.log(`Value of val is: ${val.value}`)

    const someMethod = () => {
      // do smth
    }

    //  Method Handlers 
    const greet = (event:any) => {
      alert(`Gretting!`)
      if (event) {
        console.log(event)
       }
  }

    // const calculate = () => {
    //   return Math.random();
    // }

    const clicked = (e) => {
      alert(`okay!`)
    }

    const btnClick = (e) => {
      alert(`button is clicked!`)
    }

    const roots = ()=> {
      console.log('you have clicked roots');
    }
    const parent = () => {
      console.log('you have clicked parent');
    }
    const child = () => {
      console.log('you have clicked child');
    }
    onBeforeMount(() => {
      console.log(type.value)
    })
    onMounted(() => {
       console.log('mount')
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
    const submitForm = (event) => {
      // event.preventDefault()
      alert("submitted");
    }
    return {
      val, root, count, greet, submitForm, clicked, btnClick, roots, parent, child
    }
  },
}
</script>
