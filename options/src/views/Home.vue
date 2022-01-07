<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">

  <div class="hello">
    <h1>Home Page</h1>

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

export default {
  name: 'Home',
  components: {
    GameCard
  },
  props: {
    msg: String
  },
  data() {
    return {
      responseContentful: 1,
    }
  },
  methods: {

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
