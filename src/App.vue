
<template>
   
   <div class="ctr">
    
    <transition name="fade" mode="out-in">
    
    
    <question 
    v-if="questionsAnswered < questions.length" 
    :questions="questions"
    :questionsAnswered="questionsAnswered"
    @question-answered="questionAnswered"
    ></question>
    <result v-else :totalCorrect="totalCorrect" :results="results"></result>
  </transition>
  
  <button
      type="button"
      class="reset-btn"
      @click.prevent="back"
     v-show="questionsAnswered >= 1"
    >
      Back 
    </button>
   <button
      type="button"
      class="reset-btn"
      @click.prevent="reset"
     v-show="questionsAnswered === questions.length"
     
    >
      Reset 
    </button>
   </div>
  
  
</template>



<script>
 import Question from './components/Question.vue'; 
 import Result from './components/Result.vue';

 export default{
  name: 'App',

  components:{
    Question,
    Result
  },

  methods:{
    questionAnswered(is_correct){
      if(is_correct){
        this.totalCorrect++
      }
      this.questionsAnswered++
    },
    reset(){
      this.questionsAnswered = 0
      this.totalCorrect = 0
    }, back(){
      this.questionsAnswered--
    }
  },
 
  data() {
    return {
      questionsAnswered: 0,
      totalCorrect: 0,
      questions: [
        {
          q: "Which of the following results in the fall of acid rain?",
          answers: [
            {
              text: "gaseous hydrocarbon",
              is_correct: false,
            },
            {
              text: "particulate matter",
              is_correct: false,
            },
            {
              text: "oxides of sulphur",
              is_correct: true,
            },
            {
              text: "oxide of lead",
              is_correct: false,
            },
          ],
        },
        {
          q: 'The oxidation state of carbon in HCOOH is ?',
          answers: [
            {
              text: "-1",
              is_correct: false,
            },
            {
              text: "0",
              is_correct: false,
            },
            {
              text: "2",
              is_correct: true,
            },
            {
              text: "3",
              is_correct: false,
            },
          ],
        },
        {
          q: "Which of the following is a base ?",
          answers: [
            {
              text: "CO2",
              is_correct: false,
            },
            {
              text: "CH3COOH",
              is_correct: false,
            },
            {
              text: "CaO",
              is_correct: true,
            },
            {
              text: "H3PO4",
              is_correct: false,
            },
          ],
        },
      ],
      results: [
        {
          min: 0,
          max: 2,
          title: "Try again!",
          desc: "Do a little more studying and you may succeed!",
        },
        {
          min: 3,
          max: 3,
          title: "Wow, you're a genius!",
          desc: "Studying has definitely paid off for you!",
        },
      ],
    };
  },
 }
</script>


 