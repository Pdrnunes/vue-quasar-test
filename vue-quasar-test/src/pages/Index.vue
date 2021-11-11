<template>
  <q-page padding>
    <!-- lesson 3 - editing a property in realtime with v-model directive: -->
    <input v-model="message"/>
    <!-- lesson 4 - attaching event to a button: -->
    <!-- lesson 4 obs.: @click supports javascript coding event -->
    <!-- <button @click="message = ''">Clear</button> -->
    <!-- lesson 4 - clearing message implementing a method: -->
    <button @click="clearMessage"></button>
    <!-- all quasar pages root element -->
    <!-- <h5>introducing titles in my app</h5> lesson 2: manual hardcoded message -->
    <h5>{{message}}</h5>
    <!-- lesson 2: exporting the property message to page -->
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
      message: 'Introducing titles in my app' //lesson 2 more adaptability if a further method changes the content of this property.
    }
  },
  methods: {
    clearMessage() { //the method for clearing the message editor
      this.message = ''
    }
  }
})
</script>
