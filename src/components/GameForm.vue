<template>
  <div class='gameform'>
    <div class='question'>
      <h1 class='question_title' style='text-align: center'>{{questions[currentQuestion].question}}</h1>
      <div class='question_answers'>
        <button
            v-for='(answer,idx) in questions[currentQuestion].answers'
            v-bind:key="idx"
            v-on:click="checkAnswer(questions[currentQuestion].answers[idx])">
          {{answer}}
        </button>
      </div>
      <div class='question_counter'>{{currentQuestion+1}}/{{questions.length}}</div>
    </div>
    <div class='restart' v-show="ended">
      <div class='restart_content'>
        <p class='restart_text'>Правильных ответов: {{correctAnswers}}</p>
        <button class='restart_button' @click="restartGame">Попробовать снова</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'GameForm',
  data() {
    return {
      idx: 0,
      ended: false,
      currentQuestion: 0,
      correctAnswers: 0,
      questions: [
        {
          question: 'Что такое JavaScript?',
          answers: ['Язык программирования, который используют для веб-приложений', 'Язык программирования, который используют для игры в codebox', 'Кроссплатформенная игра для браузеров'],
          correct: 'Язык программирования, который используют для веб-приложений',
        },
        {
          question: 'Сколько гласных в слове "собака"?',
          answers: ['2', '3', 'Бесконечно много'],
          correct: '3',
        },
        {
          question: 'Кто такой Папич?',
          answers: ['Писатель', 'Стример', 'Музыкант'],
          correct: 'Стример',
        },
      ]
    }
  },
  methods: {
    checkAnswer(answer){
      if (answer===this.questions[this.currentQuestion].correct) {
        this.correctAnswers +=1;
      }
      if (this.currentQuestion !== this.questions.length-1) {
        this.currentQuestion +=1;
      } else {
        this.ended = true;
      }
    },
    restartGame(){
      this.currentQuestion = 0;
      this.correctAnswers = 0;
      this.ended = false;
    },
  },
}
</script>


<style scoped>

.restart{
  font-family: "Trebuchet MS", "Lucida Sans",serif;
  font-size: 20px;
  height: 100%;
  position: absolute;
  width: 100%;
  max-height: 100%;
  margin: auto;
  overflow: auto;
  top: 0; left: 0; bottom: 0; right: 0;
  background-color: rgba(255,255,255,0.9);
  border-radius: 30px;
  text-align: center;
}

.restart_content{
  padding-top: 20%;
  display: inline-block;
}

.restart_button{
  font-family: "Trebuchet MS", "Lucida Sans",serif;
  font-weight: bold;
  font-size: 15px;
  background-color: white;
  color: black;
  border: 2px solid #4CAF50;
  padding: 20px;
}

.restart_button:hover{
  cursor: pointer;
  background-color: white;
}

.question_counter{
  font-family: "Trebuchet MS", "Lucida Sans",serif;
  text-align: right;
  margin-right: 2em;
}
.question_title {
  font-family: 'Nunito', sans-serif;
}
.question_answers {
  display: flex;
  flex-direction: column;
}
.question_answers button {
  font-family: "Trebuchet MS", "Lucida Sans",serif;
  padding: 7px 20px;
  margin-bottom: 10px;
  border-radius: 10px;
  border-left: 10px solid #f05d22;
  border-color: #f05d22;
  box-shadow: 1px 1px 1px 1px rgba(0,0,0,.1);
  font-size: 20px;
  letter-spacing: 2px;
  transition: 0.3s all ease;
}
.question_answers button:nth-child(2){border-color: #8bc63e;}
.question_answers button:nth-child(3){border-color: #fcba30;}
.question_answers button:nth-child(4){border-color: #1ccfc9;}
.question_answers button:nth-child(5){border-color: #493224;}
.question_answers button:hover {
  cursor: pointer;
  background-color: white;
}
</style>
