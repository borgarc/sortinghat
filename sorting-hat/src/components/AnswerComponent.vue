<template>
  <el-col class="answer-container">
    <el-row class="answer">{{ answer }}</el-row>
  </el-col>
</template>

<script>

export default {
  name: 'AnswerComponent',
  props: {
    answer: {
      type: String,
      required: true,
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.answer-container {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}

.answer, .answer {
  display: flex;
  justify-content: flex-start
}
</style>