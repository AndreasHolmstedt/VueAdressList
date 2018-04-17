<template>
  <div v-bind:class="cardStyle">
    <div v-bind:class="headerStyle">
      <p>Create New Card</p>
    </div>
    <div v-bind:class="bottomStyle">
      <input v-model="name" placeholder="Name"></input>
      <input v-model="adress" placeholder="Adress"></input>
      <input v-model="phone" placeholder="Phone Number"></input>
      <input v-model="email" placeholder="Email"></input>
      <button v-on:click="createCard">+</button>
    </div>
  </div>
</template>

<script>
export default {
  data: function(){
     return {
         cardStyle: "cardStyle1",
         headerStyle: "headerStyle1",
         bottomStyle: "bottomStyle1",
         name: "",
         adress: "",
         phone: "",
         email: ""
     }
  },
  methods: {
    createCard: function() {
      this.$emit("createCard", { name: this.name, adress: this.adress, phone: this.phone, email: this.email });
      this.name = "";
      this.phone = "";
      this.adress = "";
      this.email = "";
    }
  }

}
</script>


<style scoped>
@import url('https://fonts.googleapis.com/css?family=Lato:300,400,700|Roboto+Slab');

.cardStyle1 {
  font-family: 'Roboto Slab', serif;
  font-weight: 300;
  max-width: 320px;
  height: 250px;
  margin: 20px;
  background-color: #F4F4F4;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  box-shadow: 0px 4px 5px 0px rgba(0,0,0,.2)
}


.headerStyle1 {
  margin: 0px;
  padding: 0px;
  height: 100px;
  background-color: #137477;
  display: flex;
  justify-content: center;
  align-items: center;
}

.headerStyle1 > p {
  font-family: 'Lato', sans-serif;
  font-weight: 700;
  color: #f3Bdac;
  margin: 0px;
  padding-top: 1em;
  padding-bottom: 1em;
  text-align: left;
  padding-left: 1em;
}

.headerStyle1 > input {
  padding-left: 1em;
}

.headerStyle1 > button {
  font-size: 2em;
  font-weight: 700;
  margin: 0px;
  padding: 0px;
  color: #f3Bdac;
  border: none;
  background-color: transparent;
  margin-right: .5em;
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
    flex:1 1 400px;
    padding: 10px;
}

.bottomStyle1 > input{
  width: 90%;
  height: 1.5em;
  margin-bottom: .5em;
}

.bottomStyle1 > button {
  width: 90%;
  background-color: #137477;
  border: none;
  color: #f3Bdac;
  font-size: 2em;
}

</style>
