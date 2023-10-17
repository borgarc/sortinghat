<template>
  <el-col :xs="24" id="app">
    <SelectionChat />
  </el-col>
</template>

<script>
import SelectionChat from '@/views/SelectionChat.vue'

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
  background-image: url('@/assets/images/greathall.webp');
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

@media (max-width: 1220px) {
  body {
    display: block;
    width: 100%;
    height: 100%;
    background: url('@/assets/images/greathall.webp');
    background-position: center;
    background-size: cover;
  }

  #app {
    width: 100%;
    height: 100%;
  }
}
</style>
