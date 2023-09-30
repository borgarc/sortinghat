<template>
  <div class="hello">
    <div v-for="question in questions" :key="question.title">
      <span>{{ question.title }}</span>
    </div>
  </div>
</template>

<script>
import seeds from '../assets/sorting_hat.json'

export default {
  name: 'SelectionChat',
  data () {
    return {
      questions: seeds
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>