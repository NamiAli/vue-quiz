<template>
  <div id="app">
    <Header 
     :num_correct='num_correct'
     :num_total='num_total'
    />
    <b-container class="bv-example-row">
  <b-row>
    <b-col sm='6' offset='3'>
    <QuestionBox
    v-if="questions.length"
     :currentQuestion="questions[index]"
     :next='next'
     :increament='increament'
    />
    </b-col>
  </b-row>
</b-container>

  </div>
</template>

<script>

import Header from './components/Header.vue';
import QuestionBox from './components/QuestionBox';

export default {
  name: 'app',
  components: {
    Header,
    QuestionBox
  },
  data(){
    return {
      questions: [],
      index: 0,
      num_correct: 0,
      num_total: 0
    }
  },
  methods: {
    next(){
      this.index++;
    },
    increament(isCorrect){
      if(isCorrect){
        this.num_correct++;
      }

      this.num_total++;


    }
  },
  mounted: function(){
    fetch('https://opentdb.com/api.php?amount=10&category=27&difficulty=medium&type=multiple', {
     method: 'get'
    })
    .then((response) => {
       return response.json();
    }).then((jsonData)=>{
       this.questions = jsonData.results;
    });
  }
  
  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
