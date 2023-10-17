<template>
  <el-col class="answer-container">
    <el-row class="answer">
      <Transition name="bounce">
        <span v-show="show" class="text-border">{{ answer }}</span>
      </Transition>
    </el-row>
  </el-col>
</template>

<script>

export default {
  name: 'AnswerComponent',
  props: {
    answer: {
      type: String,
      required: true,
    },
    willShow: {
      type: Boolean,
      required: true,
    },
  },
  data () {
    return {
      show: false,
    }
  },
  mounted () {
    setTimeout(()=> { this.show = this.willShow }, 500)
  }
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
  justify-content: flex-start;
  margin: 10px;
}

.text-border {
  border: solid 1px;
  padding: 10px;
  border-radius: 30px 30px 30px 0;
  background-color: #5e5e5e;
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