<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">

  <div class="hello">
    <h1 ref="h1Test" @click="clickTitle">Home Page</h1>

    <ul class="cards">
      <GameCard v-for="item in responseContentful.items" :key="item.id" :data='item ? item : null' />  
    </ul>

  </div>

  </div>
</template>

<script>
// @ is an alias to /src
import GameCard from '@/components/GameCard.vue'
import { client } from '@/client'
import { ref } from 'vue'

export default {
  name: 'Home',
  components: {
    GameCard
  },
  setup() {

    // ref data/state
    const responseContentful = ref(1)

    // ref get DOM ellement
    const h1Test = ref(null)

    const clickTitle = () => {
      console.log(h1Test, h1Test.value)
      // change class
      h1Test.value.classList.add('title-style-a')
      h1Test.textContent = 'No more'
    }

    return {  
      responseContentful,
      h1Test,
      clickTitle  
      }
  },
  created() {
  client.getEntries() // Simple GET request using fetch
    .then(data => {
      console.log(data)
      this.responseContentful = data
      }
    )
    .catch(console.error)
  },
}
</script>

<style scoped>
  .title-style-a {
    color: red;
  }
</style>
