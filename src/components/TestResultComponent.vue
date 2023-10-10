<template>
  <el-col class="test-result-container">
    <div><span>{{ name }}</span> <span>WELCOME TO</span></div>
    <img class="image" :src="`../assets/images/${house}.jpg`" />
    <span>{{ house }}</span>
  </el-col>
</template>

<script>

export default {
  name: 'TestResultComponent',
  props: {
    name: {
      type: String,
      required: true
    },
    house: {
      type: String,
      required: true
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.image {
  width: 50%;
  height: 50%;
}

.test-result-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center
}

</style>