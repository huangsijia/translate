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
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170721T082515Z.54cf3dc583f679db.f4a96182281281d8b5dfe24b4e88298e2133f219&lang='+language+'&text='+text).then((Response)=>{
          this.outputMessage = Response.body.text[0];
        })
      }
    }
  }
</script>

<style>

</style>
