<template>
  <el-col class="username-container">
    <el-row class="username-input-container">
      <span class="username-label">
        {{ introduction1 }}<br/>
        {{ introduction2 }}<br/>
        {{ introduction3 }}<br/>
        {{ introduction4 }}
      </span>
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
      username: '',
      introduction1: 'Hello little one.',
      introduction2: 'we are going to ask you some questions to choose your schools house.',
      introduction3: 'Please answer the questions choosing the letter of your answer choice.',
      introduction4: 'So... whats your name little wizzard?'
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

.username-label {
  border: solid 1px;
  padding: 10px;
  border-radius: 30px 30px 0 30px;
  background-color: #034387;
  color: white
}
</style>