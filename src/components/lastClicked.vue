<template>
  <div v-bind:class="cardStyle">
    <p>Last Selected Contact</p>
    <div v-bind:class="headerStyle">
      <h2>{{ name }}</h2>
    </div>
    <div v-bind:class="bottomStyle">
      <h3>{{ adress }}</h3>
      <p>{{ phone }}</p>
      <p>{{ email }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["name", "phone", "adress", "email"],
  data: function(){
     return {
       cardStyle: "cardStyle1",
       headerStyle: "headerStyle1",
       bottomStyle: "bottomStyle1",
     }
  },

}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Lato:300,400,700|Roboto+Slab');

.cardStyle1 {
  font-family: 'Roboto Slab', serif;
  font-weight: 300;
  max-width: 320px;
  height: 380px;
  margin: 20px;
  background-color: #F4F4F4;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}

p {
  color: #137477;
}

.headerStyle1 {
  margin: 0px;
  padding: 0px;
  height: 70px;
  background-color: #137477;
}

.headerStyle1 > h2 {
  font-family: 'Lato', sans-serif;
  font-weight: 700;
  color: #f3Bdac;
  margin: 0px;
  padding-top: 1em;
  padding-bottom: 1em;
  text-align: left;
  padding-left: 1em;
}

.headerStyle1 > button:first-of-type {
  position: relative;
  left: 140px;
  top: -60px;
  font-size: 2em;
  font-weight: 700;
  transform: rotate(90deg);
  margin: 0px;
  padding: 0px;
  color: #f3Bdac;
  border: none;
  background-color: transparent;
}

.headerStyle1 > button:first-of-type:focus {
  outline: 0;
}

.bottomStyle1 {
    color: #137477;
    position: relative;
    border: 3px solid #137477;
    border-top: none;
    margin: 0px;
    padding: 0px;
    flex:1 1 400px;
}
</style>
