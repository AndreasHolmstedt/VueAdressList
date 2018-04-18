<template>
  <div v-bind:class="cardStyle" v-on:click="cardClick">
    <div v-bind:class="headerStyle">
      <h2 v-if="!edit">{{ cardName }}</h2>
      <input v-if="edit" v-model="placeholderName"></input>

      <button v-if="!edit" v-on:click="toggleEditMode">✎</button>
      <button v-if="edit" v-on:click="discardChanges">X</button>
      <button v-if="edit" v-on:click="saveChanges">✔</button>
    </div>
    <div v-bind:class="bottomStyle">
      <h3 v-if="!edit">{{ cardAdress }}</h3>
      <p v-if="!edit">{{ cardPhone }}</p>
      <p v-if="!edit">{{ cardEmail }}</p>

      <input v-if="edit" v-model="placeholderAdress"></input>
      <input v-if="edit" v-model="placeholderPhone"></input>
      <input v-if="edit" v-model="placeholderEmail"></input>
    </div>
  </div>
</template>

<script>
export default {
  props: ['name', 'phone','email', 'adress', 'selectedKey'],
  data: function(){
     return {
       cardStyle: "cardStyle1",
       headerStyle: "headerStyle1",
       bottomStyle: "bottomStyle1",
       edit: false,
       cardName: this.name,
       placeholderName: this.name,
       cardPhone: this.phone,
       placeholderPhone: this.phone,
       cardEmail: this.email,
       placeholderEmail: this.email,
       cardAdress: this.adress,
       placeholderAdress: this.adress
     };
  },
  methods: {
    cardClick: function () {
      this.$emit('cardClick', { selectedKey: this.selectedKey, name: this.name, adress: this.adress, phone: this.phone, email: this.email });
    },
    toggleEditMode: function() {
      this.edit = !this.edit;
    },
    discardChanges: function () {
      this.toggleEditMode();
    },
    saveChanges: function () {
      this.cardName = this.placeholderName;
      this.cardAdress = this.placeholderAdress;
      this.cardEmail = this.placeholderEmail;
      this.cardPhone = this.placeholderPhone;
      this.toggleEditMode();
  },
  },
  computed: {
    nameComputed: function() {
        return this.name;
    }
  }

}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Lato:300,400,700|Roboto+Slab');

.cardStyle1 {
  font-family: 'Roboto Slab', serif;
  font-weight: 300;
  width: 320px;
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
  justify-content: space-between;
  align-items: center;
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

.headerStyle1 > input {
  margin-left: 1.2em;

}

.headerStyle1 > button {
  font-size: 1.5em;
  font-weight: 700;
  margin: 0px;
  padding: 0px;
  color: #f3Bdac;
  border: none;
  background-color: transparent;
  margin-right: .5em;
}

.selected {
  outline: 3px solid #36859f;
}

.selected .headerStyle1 {
  background-color: #36859f;
}

.headerStyle1 > button:first-of-type:focus {
  outline: 0;
}

.bottomStyle1 {
    color: #137477;
    position: relative;
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

</style>
