<template>
  <q-page padding>
    <button
      style="position: absolute; right: 10px"
      @click="counter++">
      {{counter}}
    </button>
    <!-- vuejs directives (v-model, @keyup, @click, @mouseenter, etc.): allows js codes into html -->
    <!-- <input v-model="message" @keyup="handleKeyup"/> -->
    <input 
      v-model="message" 
      @keyup.esc="clearMessage" 
      @keyup.enter="alertMessage"/>
    <button 
      @click="clearMessage">Clear</button>

    <!-- the h5 message shows only if the message have a lenght greater then zero -->
    <!-- <h5 
      class="border-grey" 
      v-show="message.length">{{ message }}
    </h5>     -->

    <!-- implementation of v-if/else directives -->
    <h5 
      class="border-grey" 
      v-if="message.length">{{ message }}
    </h5>
    <h6 
      v-else>{{ message2 }}
    </h6>

    <hr>
    <p>Uppercase message:</p>
    <p v-if="message.length"> {{ messagetoUpperCase }}</p>
    <!-- even though computed properties are technicaly METHODS, they are treated
    as static data properties, like 'message' or 'counter', so the parenthesis 
    are not needed in the directive-->
    <p v-else>{{message3}}<br>{{message4}}</p>
    <!-- <p>Lowercase message: {{message | lowCase}}</p> -->
    <!-- BUT FILTERS ARE DEPRECATED IN VUE 3, so i'm commenting it... -->
  </q-page>
</template>


<style>
/* create SCSS classes here */
.border-grey {
  border: 1px solid grey;
}
</style>

<script>
// where all data and methods should go
// lesson 2: creating a data function which returns an object
import { defineComponent } from 'vue';

export default defineComponent({
  data() {
    return {
      // here is where all properties will go:
      // id: 1,
      // properties are separated with commas
      message: 'Introducing titles in my app', //lesson 2 more adaptability if a further method changes the content of this property.
      message2: 'No message entered D=',
      message3: 'No message to Uppercase',
      message4: 'Just by clearing the message using backspace you will se that the computed directive fires 27 times, showing that this is highly ineficient',
      counter: 0,
      // changed: false
    }
  },
  // computed property:
  computed: {
    messagetoUpperCase() {
      console.log('messagetoUppercase was triggered');
      return this.message.toUpperCase() + this.counter
      // computed properties have access to data and methods properties, thus been more powerful than
      // the deprecated filter property
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
        console.log(this.message);
        // this.changedMessage();
        console.log(this.changed);
      }
    },
    alertMessage() {
      alert(this.message)
      // this.changedMessage(this.message)
    },
    
    // alertId() {
    //   alert(this.id)
    // },
    // changedMessage(dataMessage) {
    //   var msg
    //   console.log('1', dataMessage);
    //   msg = dataMessage
    //   console.log('2', msg);
    //   if (this.changed == false && msg != this.message) {
    //     this.changed = true
    //     this.message = msg
    //     console.log('3', this.message);
    //   }
      // } else if (this.changed == true) {
      //   this.changed = true;
      // }
    // }
  },
  // Filters are basicaly methods, so they can accept values AND ARE DEPRECATED IN VUE 3
  // Puting it in my project comentated just for learning it
   /*/filters: {
      lowCase(v) {
      return v.toLowerCase()
     }
    }*/ 
})

</script>
