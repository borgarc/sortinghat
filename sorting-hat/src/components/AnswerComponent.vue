<template>
  <el-col class="answer-container">
    <el-row class="answer"><span class="text-border">{{ answer }}</span></el-row>
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

.answer {
  display: flex;
  justify-content: flex-start
}

.text-border {
  border: solid 1px;
  padding: 10px;
  border-radius: 30px 30px 30px 0
}
</style>