<template>
  <li @click="selectCard">
    <a class="card" :class="{card_selected: cardSelected}">
      <img :src="data.fields.gameImage.fields.file.url" class="card__image" alt="" />
      <div class="card__overlay">
        <div class="card__header">
          <svg class="card__arc" xmlns="http://www.w3.org/2000/svg"><path /></svg>                     
          <img class="card__thumb" src="https://i.imgur.com/7D7I6dI.png" alt="" />
          <div class="card__header-text">
            <h3 class="card__title">{{ data.fields.gameName }}</h3>            
            <span class="card__status">1 hour ago</span>
          </div>
        </div>
        <p class="card__description">{{ data.fields.gameDescription.content[0].content[0].value.slice(0,70) }}...</p>
      
      </div>
    </a>      
  </li>
</template>

<script>
export default {
  name: 'GameCard',
  props: {
    data: Object
  },
  data() {
    return {
      cardSelected: false,
    }
  },
  methods: {
    selectCard(){
      this.cardSelected = !this.cardSelected
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
