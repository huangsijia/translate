<template>
  <div id="app">
    <h1>欢迎来到的在线翻译</h1>
    <pageInput @inputMessage="inputMessageFun"></pageInput>
    <pageOutPut v-text="outputMessage"></pageOutPut>
  </div>
</template>

<script>
  import pageInput from "./components/pageInput";
  import pageOutPut from "./components/pageOutPut";
  export default {
    name: 'App',
    components: {
      pageInput,
      pageOutPut
    },
    data:function () {
      return{
        outputMessage:''
      }
    },
    methods: {
      inputMessageFun(text, language) {
        this.$http.get('https://translate.google.cn/#view=home&op=translate&sl=zh-CN&tl='+ language+'&text='+text).then((Response)=>{
          this.outputMessage = Response.body.text[0];
        })
      }
    }
  }
</script>

<style>

</style>
