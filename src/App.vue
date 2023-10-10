<template>
  <el-col :xs="24" id="app">
    <SelectionChat />
  </el-col>
</template>

<script>
import SelectionChat from './views/SelectionChat.vue'

export default {
  name: 'App',
  components: {
    SelectionChat
  },
}
</script>

<style>
html, body {
  width: 100%;
  height: 100%;
}

body {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0;
}

#app {
  width: 50%;
  height: 50%;
}

@media (max-width: 600px) {
  body {
    display: block
  }

  #app {
    width: 100%;
    height: 100%;
  }
}
</style>
