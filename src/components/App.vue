<template>
  <div id="app">
    <div class="cards"  >
      <list-card v-for="(item, index) in dataList" v-on:cardClick="onCardClick" :key="index" :name="item.name" :phone="item.phone" :adress="item.adress" :email="item.email" />
      <create-card />
  </div>
    <div class="selected">
      <last-clicked />
  </div>
  </div>
</template>

<script>
  import listCard from './listCard.vue';
  import lastClicked from './lastClicked.vue';
  import createCard from './createCard.vue';

  export default {
    name: 'app',
    data: function() {
        return {
            dataList: [
              { name: "Robert Karlson",
                adress: "Beefroad 22, 35352 Queenscounty",
                phone: "0703374525",
                email: "robert@karl.son"
              },
              { name: "Robert Persson",
                adress: "Wallawalla 2, 506 36 Svenljunga",
                phone: "0703346735",
                email: "robert@persson.se"
              },
              { name: "Alfred Svensson",
                adress: "Porkloin Avenue 25, 13337 Höga Stora",
                phone: "0706922033",
                email: "robert@karl.son"
              },
              { name: "Calle Munkhammar",
                adress: "Mountymanroad 15, 40564, Stockholm",
                phone: "5703374525",
                email: "calle.munken@gmail.com"
          }],
          recentlyClicked: {
              name: "",
              adress: "",
              phone: "",
              email: ""
          }
        }
    },
    methods: {
      onCardClick: function (card) {
          this.recentlyClicked = {
            name: card.name,
            adress: card.adress,
            phone: card.phone,
            email: card.email,
          }
      }
    },
    components: {
      'list-card': listCard,
      'last-clicked': lastClicked,
      'create-card': createCard,
    },
  }

</script>

<style src="normalize.css/normalize.css"></style>

<style>

</style>

<style scoped>
  #app {
    text-align: center;
  }

  #app h1 {
    color: #2c3e50;
    font-weight: 300;
    margin: 0;
  }
</style>
