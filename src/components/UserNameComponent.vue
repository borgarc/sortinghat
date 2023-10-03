<template>
  <el-col class="username-container">
    <el-row class="username-input-container">
      <span class="username-label">Nombre </span>
      <el-input
        class="username-input"
        placeholder=""
        suffix-icon="el-icon-position"
        v-model="username"
        @change="updateParent">
      </el-input>
    </el-row>
  </el-col>
</template>

<script>

export default {
  name: 'UserNameComponent',
  data () {
    return {
      username: ''
    }
  },
  methods: {
    updateParent() {
      let data = {
        username: this.username,
        hasUserName: true
      }
      if (data.username.trim() !== '') {
        this.$emit('setUserName', data)
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.username-input-container {
  display: flex;
  flex-direction: column
}

.username-input {
  width:80%;
  margin: 10px
}
</style>