<template>
  <div id="app">
    <div class="cards">
      <list-card
        v-for="(item, index) in dataList"
        v-on:cardClick="onCardClick"
        v-bind:class="recentlyClicked.selectedKey === index ? 'selected' : null"
        :key="index"
        :selectedKey="index"
        :name="item.name"
        :phone="item.phone"
        :adress="item.adress"
        :email="item.email"
      />
      <create-card v-on:createCard="createNewCard" />
  </div>
    <div class="clicked">
      <last-clicked :name="recentlyClicked.name" :phone="recentlyClicked.phone" :adress="recentlyClicked.adress" :email="recentlyClicked.email" />
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
                adress: "Mountymanroad 15, 40564 Stockholm",
                phone: "5703374525",
                email: "calle.munken@gmail.com"
              },
              {
                name: "Erik Olsson",
                adress: "Lövhammarsvägen 24, 44445 Stenungsund",
                phone: "0703374525",
                email: "erik.r.olsson@telia.com"
              },
              {
                name: "Pelle Pellesson",
                adress: "Pellesgatan 3, 66633 Pellesund",
                phone: "+462031393",
                email: "pe.le@sson.com"
              },
              {
                name: "Fredrik Olsson",
                adress: "Kanelgatan 18, 60564 Svenljunga",
                phone: "5704050625",
                email: "Fidde123@gmail.com"
              },
              {
                name: "Andreas Holmstedt",
                adress: "Döbelnsgatan 88, 50638 Borås",
                phone: "0739893424",
                email: "holmstedt.andreas@hotmail.com"
              },
              {
                name: "Carl Frederiksen",
                adress: "Fjärilsgatan 15, 44434 Stenungsund",
                phone: "072510149",
                email: "gillar_handboll@hotmale.se"
              },
              {
                name: "Hans Zimmer",
                adress: "Symphonystreet 82, 12378 New York",
                phone: "+31786543568",
                email: "Imakesweetmusic@gmail.com"
              },
              {
                name: "Gustav Karlström",
                adress: "Anonymous Road 2, 13337 Skövde",
                phone: "07013371337",
                email: "alskar_fotboll@live.com"
              },
              {
                name: "Frej Larsson",
                adress: "Beatroad 14, 40589 Ronneby",
                phone: "0736669857",
                email: "rapperBoy@gmail.com"
              },
              {
                name: "Markus Mattsson",
                adress: "Halmgatan 15, 78564 Halmstad",
                phone: "0783546898",
                email: "slackerMan@gmail.com"
              }
          ],
          recentlyClicked: {
              selectedKey: 0,
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
            selectedKey: card.selectedKey,
            name: card.name,
            adress: card.adress,
            phone: card.phone,
            email: card.email
          }
      },
      createNewCard: function(card) {

          this.dataList.push(card);
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

  .cards {
      display: flex;
      flex-direction: row;
      flex-wrap: wrap;
  }

  .selected {
    outline: 3px solid #7CB6C9;
  }

  #app h1 {
    color: #2c3e50;
    font-weight: 300;
    margin: 0;
  }
</style>
