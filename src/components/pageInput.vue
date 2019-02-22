<template>
  <div id="pageInput">
    <form @submit.prevent="submitForm">
      <input type="text" placeholder="请输入要翻译的文案" v-model="message">
      <select v-model="language">
        <option value="en">英语</option>
        <option value="ru">俄罗斯</option>
        <option value="ko">韩语</option>
        <option value="ja">日语</option>
      </select>
      <input type="submit" value="翻译">
    </form>
  </div>
</template>

<script>
  export default {
    name: 'App',
    components: {},
    data: function() {
      return {
        message: "",
        language: "en"
      }
    },
    methods: {
      submitForm() {
        this.$emit("inputMessage", this.message, this.language);
      }
    }
  }
</script>

<style>

</style>
