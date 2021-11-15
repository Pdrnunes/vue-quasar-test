<template>
  <q-page padding>
    <!-- vuejs directives (v-model, @keyup, @click, @mouseenter, etc.): allows js codes into html -->
    <!-- <input v-model="message" @keyup="handleKeyup"/> -->
    <input v-model="message" @keyup.esc="clearMessage" @keyup.enter="alertMessage"/>
    <button @click="clearMessage">Clear</button>
    <h5>{{message}}</h5>    
  </q-page>
</template>

<style>
</style>

<script>
// where all data and methods should go
// lesson 2: creating a data function which returns an object
import { defineComponent } from 'vue';

export default defineComponent({
  data() {
    return {
      // here is where all properties will go:
      id: 1,
      // properties are separated with commas
      message: 'Introducing titles in my app', //lesson 2 more adaptability if a further method changes the content of this property.
      changed: false
    }
  },
  methods: { //this is where all methods of component defineComponent should go
    clearMessage() { //the method for clearing the message editor
      this.message = ''
    }, //methods are also separated with commas
    handleKeyup(keyInput) {
      // console.log(keyInput.keyCode);
      if (keyInput.keyCode == 27) {
        // this.message = '' redundant
        this.clearMessage(); // code reuse
      } else if (keyInput.keyCode == 13) {
        this.alertMessage();
        this.changedMessage();
        console.log(this.changed);
      }
    },
    alertMessage() {
      alert(this.message)
      this.changedMessage()
      console.log(this.changed);

    },
    alertId() {
      alert(this.id)
    },
    changedMessage() {
      if (this.changed == false) {
        this.changed = true
      } else if (this.changed == true) {
        this.changed = false;
      }
    }
  }
})
</script>
