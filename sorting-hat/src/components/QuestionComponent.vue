<template>
  <el-col class="question-container">
    <el-row class="question"><span class="text-border title">{{ question.title }}</span></el-row>
    <el-row v-for="answers in question.answers" :key="answers.title">
      <el-row v-if="question.answers.length > 2" class="answer"><span class="text-border answer">{{ answers.title }}</span></el-row>
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
</style>