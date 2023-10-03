<template>
  <el-col class="test-result-container">
    <div><span>{{ name }}</span> <span>WELCOME TO</span></div>
    <img v-if="house === 'gryffindor'" class="image" src="../assets/images/gryffindor.jpg" />
    <img v-if="house === 'hufflepuff'" class="image" src="../assets/images/hufflepuff.jpg" />
    <img v-if="house === 'ravenclaw'" class="image" src="../assets/images/ravenclaw.jpg" />
    <img v-if="house === 'slytherin'" class="image" src="../assets/images/slytherin.jpg" />
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