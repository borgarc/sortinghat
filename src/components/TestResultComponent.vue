<template>
  <el-col class="test-result-container">
    <img class="image" :src="require(`@/assets/images/${house}.png`)" />
  </el-col>
</template>

<script>

export default {
  name: 'TestResultComponent',
  props: {
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
  width: 100%;
  height: 100%;
}

.test-result-container {
  width: 50%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

@media (max-width: 600px) {
  .test-result-container {
    width: 100%;
  }

  .container {
    display: none;
  }
}

</style>