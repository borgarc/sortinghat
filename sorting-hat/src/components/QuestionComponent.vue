<template>
  <el-col class="question-container">
    <el-row class="question">{{ question.title }}</el-row>
    <el-row v-for="answers in question.answers" :key="answers.title">
      <el-col v-if="question.answers.length > 2" class="answer">{{ answers.title }}</el-col>
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
    }
  },
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
  justify-content: flex-end
}
</style>