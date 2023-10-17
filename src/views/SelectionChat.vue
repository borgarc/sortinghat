<template>
  <el-col class="selection-chat-container">
    <el-row v-if="!testOver" class="selection-chat-container">
      <el-row v-if="!hasUserName && !testOver" class="username-container">
        <UserNameComponent @setUserName="setUserName"/>
      </el-row>
      <el-row v-else class="chat-container" ref="chatContainer" v-for="(question, index) in questions" :key="question.title">
        <QuestionComponent :question="question" :willShow="true"/>
        <AnswerComponent v-if="selectedAnswer[index] !== undefined" :answer="selectedAnswer[index]" :willShow="true" />
      </el-row>
      <el-row v-if="hasUserName && !testOver" class="answer-input-container" id="input-container">
        <el-input
          class="answer-input"
          placeholder=""
          suffix-icon="el-icon-position"
          v-model="answer"
          @change="onEnter">
        </el-input>
        <div id="scrollToMe"></div>
      </el-row>
    </el-row>
    <el-row v-else class="result-container">
      <TestResultComponent :house="finalHouse" />
    </el-row>
  </el-col>
</template>

<script>
import seeds from '@/assets/sorting_hat.json'
import QuestionComponent from '@/components/QuestionComponent.vue'
import AnswerComponent from '@/components/AnswerComponent.vue'
import UserNameComponent from '@/components/UserNameComponent.vue'
import TestResultComponent from '@/components/TestResultComponent.vue'

export default {
  name: 'SelectionChat',
  components: {
    QuestionComponent,
    AnswerComponent,
    UserNameComponent,
    TestResultComponent
  },
  mounted() {
    this.questions.push(seeds[0])
  },
  data () {
    return {
      questionsList: seeds,
      hasUserName: false,
      testOver: false,
      finalHouse: '',
      username: '',
      questionIndex: 0,
      questions: [],
      answer: '',
      selectedAnswer: [],
      scores: undefined,
      houses: {
        gryffindor: 0,
        hufflepuff: 0,
        ravenclaw: 0,
        slytherin: 0
      }
    }
  },
  methods: {
    onEnter() {
      const actualQuestion = this.questionsList[this.questionIndex]
      actualQuestion.answers.forEach(answer => {
        let testAnswer = answer.letter.toLowerCase().replace(/\s/g, '').replace(/[{)}]/g, '')
        let userAnswer = this.answer.toLowerCase().replace(/\s/g, '').replace(/[{)}]/g, '')

        if (testAnswer === userAnswer) {
          this.scores = answer.scores
          this.selectedAnswer.push(answer.title)
          this.answer = ''
          this.houses.gryffindor += this.scores.g
          this.houses.hufflepuff += this.scores.h
          this.houses.ravenclaw += this.scores.r
          this.houses.slytherin += this.scores.s

          this.questionIndex++
          if (this.questionsList.length !== this.questionIndex) {
            this.questions.push(this.questionsList[this.questionIndex])
          }  else {
            this.showResults()
          }
        } else {
          return ''
        }
      })
      setTimeout(()=> { this.scrollToElement() }, 700)

    },
    showResults() {
      let arr = Object.values(this.houses)
      let max = Math.max(...arr)

      this.finalHouse = Object.keys(this.houses).find(key => this.houses[key] === max);
      this.testOver = true
    },
    setUserName(data) {
      this.hasUserName = data.hasUserName
      this.username = data.username
    },
    scrollToElement() {
      const el = document.getElementById('scrollToMe');

      if (el) {
        el.scrollIntoView({behavior: 'smooth'});
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.selection-chat-container {
  height: 100%;
  width: 100%;
  overflow: auto
}

.answer-input-container {
  display: flex;
  justify-content: flex-start;
}

.answer-input {
  width: 40%;
  margin: 5px
}

.username-container, .result-container {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}
</style>