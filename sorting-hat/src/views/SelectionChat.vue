<template>
  <el-col class="selection-chat-container">
    <el-row class="chat-container" ref="chatContainer" v-for="(question, index) in questions" :key="question.title">
      <QuestionComponent :question="question"/>
      <AnswerComponent v-if="selectedAnswer[index] !== undefined" :answer="selectedAnswer[index]" />
    </el-row>
    <el-row class="answer-input-container">
      <el-input
        class="answer-input"
        placeholder=""
        suffix-icon="el-icon-position"
        v-model="answer"
        @change="onEnter">
      </el-input>
    </el-row>
  </el-col>
</template>

<script>
import seeds from '../assets/sorting_hat.json'
import QuestionComponent from '../components/QuestionComponent.vue'
import AnswerComponent from '../components/AnswerComponent.vue'

export default {
  name: 'SelectionChat',
  components: {
    QuestionComponent,
    AnswerComponent
  },
  mounted() {
    this.questions.push(seeds[0])
  },
  data () {
    return {
      questionsList: seeds,
      questionIndex: 0,
      questions: [],
      answer: '',
      selectedAnswer: [],
      scores: undefined,
      houses: {
        g: 0,
        h: 0,
        r: 0,
        s: 0
      }
    }
  },
  methods: {
    onEnter() {
      const actualQuestion = this.questionsList[this.questionIndex]
      actualQuestion.answers.forEach(answer => {
        let testAnswer = answer.title.toLowerCase()
        let userAnswer = this.answer.toLowerCase()
        if (testAnswer === userAnswer) {
          this.scores = answer.scores
          this.selectedAnswer.push(this.answer)
          this.answer = ''
          this.houses.g += this.scores.g
          this.houses.h += this.scores.h
          this.houses.r += this.scores.r
          this.houses.s += this.scores.s
          this.questionIndex++
          this.questions.push(this.questionsList[this.questionIndex])
        } else {
          return ''
        }
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.answer-input-container {
  display: flex;
  justify-content: flex-start;
}

.answer-input {
  width: 40%;
  margin: 5px
}
</style>