<template>
  <el-col class="question-container">
    <el-row class="question">
      <Transition name="bounce">
        <span v-show="show" class="text-border title">{{ question.title }}</span>
      </Transition>
    </el-row>
    <el-row v-for="answers in question.answers" :key="answers.title">
      <el-row class="answer">
        <Transition name="bounce">
          <span v-if="show" class="text-border answer">{{ answers.letter }}{{ answers.title }}</span>
        </Transition>
      </el-row>
    </el-row>
  </el-col>
</template>

<script>

export default {
  name: 'QuestionComponent',
  props: {
    question: {
      type: Object,
      required: true,
    },
    willShow: {
      type: Boolean,
      required: true,
    },
  },
  data () {
    return {
      show: false
    }
  },
  mounted () {
    setTimeout(()=> { this.show = this.willShow }, 500)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.question-container {
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
}

.answer, .question {
  display: flex;
  justify-content: flex-end;
  margin: 10px
}

.text-border {
  border: solid 1px;
  padding: 10px;
  border-radius: 30px 30px 0 30px;
}

.text-border.title {
  background-color: #034387;
  color: white
}

.text-border.answer {
  background-color: #535dfc;
  color: white
}

.bounce-enter-active {
  animation: bounce-in 0.5s;
}
.bounce-leave-active {
  animation: bounce-in 0.5s reverse;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.25);
  }
  100% {
    transform: scale(1);
  }
}
</style>