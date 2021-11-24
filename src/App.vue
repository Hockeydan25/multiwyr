<template>
  <div id="app">
    <h1>Would you rather??</h1> <!-- header  -->
    <!-- reference to h2 component from would-you-rather template. lower case tag names with dashes identifies its a vue component.  -->
    <multi-would-you-rather v-for="question in questions"
    v-bind:question="question.mwyrQuestion" v-bind:key="question" 
    v-bind:answer1="question.mwyrAnswer1"
    v-bind:answer2="question.mwyrAnswer2"
    v-on:answer-changed="answerChanged"></multi-would-you-rather> 
     <!--data from wouldyourather gets bond to app. Prop data in child=answer1, Parent data wyrAnswer1   -->
    <!-- message to be dispalayed on page is the selection from the binding. -->  
    <div class="selection"><!--Start div choice--><!--bind key on choice parent child-->
        <h2>Your selections:</h2>
        <ul  v-for="choice in userSelectionMessage" v-bind:key="choice">
          <li>{{ choice }}</li>
        </ul>
    </div><!-- end div choice-->
               
  </div><!-- end app div -->
  

</template>
<!-- end html template above and starting js script below-->
<script>
//
import MultiWouldYouRather from './components/MultiWouldYouRather.vue'

export default {
  name: 'App',
  components: {
    MultiWouldYouRather
  },
  data(){  // function return array of data of 3 questions.
    return{
      questions: [ 
        {
        id:0,
          mwyrQuestion: 'Would you rather never eat cheese again or never drink anything sweet again?',
          mwyrAnswer1: 'eat cheese',
          mwyrAnswer2: 'Drink anything Sweet',
          //userSelectionMessage: '' 
        },
        {
        id:1,
          mwyrQuestion: 'Would you rather be a great hockey player or great football player?',
          mwyrAnswer1: 'Hockey Player',
          mwyrAnswer2: 'Football Player',
          //userSelectionMessage: '' 
        },            
        {
        id:2,
          mwyrQuestion: 'Would you rather be a Rock Star or a Movie Star?',
          mwyrAnswer1: 'Rock Star',
          mwyrAnswer2: 'Movie Star',
          //userSelectionMessage: '' 
        }
      ],
      userSelectionMessage: []//empty array container for the users selections as answers change.
    }
  },
  methods: { //method used to fill array with userselection
    answerChanged(choice) {      //argument choice is chnged and reviewed belwo for selections.
      if (choice == this.questions[0].mwyrAnswer1 || choice == this.questions[0].mwyrAnswer2){
          this.userSelectionMessage[0] = `${choice}`
      }
      if (choice == this.questions[1].mwyrAnswer1 || choice == this.questions[1].mwyrAnswer2){
          this.userSelectionMessage[1] = `${choice}`
      }
      if (choice == this.questions[2].mwyrAnswer1 || choice == this.questions[2].mwyrAnswer2){
          this.userSelectionMessage[2] = `${choice}`
      }
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
.selection{
  list-style-type:circle;
  display: inline-block;  
}
body{
  background-color: darkgrey;
}
/* ending css Style app.vue */
</style>
