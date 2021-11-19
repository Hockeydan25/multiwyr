<template>
  <div id="app">
    <h1>Would you rather??</h1>
    <!-- reference to h2 component from would-you-rather template. lower case tag names with dashes identifies its a vue component.  -->
    <multi-would-you-rather 
    v-bind:question="mwyrQuestion"
    v-bind:answer1="mwyrAnswer1"
    v-bind:answer2="mwyrAnswer2"
    v-on:answer-changed="answerChanged"></multi-would-you-rather> 
     <!--data from wouldyourather gets bond to app. Prop data in child=answer1, Parent data wyrAnswer1   -->
    <!-- message to be dispalayed on page is the selection from the binding. -->
    <p> {{ userSelectionMessage }}</p>
    <!-- <p>You have practiced:
      Meditation: {{ typeHours[0]}} hour(s);
      Exercise: {{ typeHours[1]}} hour(s);
      Homework: {{ typeHours[2]}} hour(s), 
      and your Activies total is: {{totalHours}} hours. Great Job!</p> -->
      
  </div>

</template>

<script>

import MultiWouldYouRather from './components/MultiWouldYouRather.vue'

export default {
  name: 'App',
  components: {
    MultiWouldYouRather
  },
  data(){  // function.
    return{
      quetions: [ 
        {
          id:0,
        mwyrQuestion: 'Would you rather never eat cheese again or never drink anything sweet again?',
        mwyrAnswer1: 'eat cheese',
        mwyrAnswer2: 'Drink anything Sweet',
        userSelectionMessage: '' 
        },
        {
          id:1,
        mwyrQuestion: 'Would you rather be a great hockey player or great football player?',
        mwyrAnswer1: 'Hockey Player',
        mwyrAnswer2: 'Football Player',
        userSelectionMessage: '' 
        },            
        {
          id:2,
        mwyrQuestion: 'Would you rather be a Rock Star or a Movie Star?',
        mwyrAnswer1: 'Rock Star',
        mwyrAnswer2: 'Movie Star',
        userSelectionMessage: '' 
        }
      ]
    }
  },
  methods: {
    answerChanged(choice) {
      this.userSelectionMessage = `Thanks! you chose ${choice}`
    }
  } 
}
/* ending Script */
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body{
  background-color: darkgrey;
}
/* ending css Style app.vue */
</style>
