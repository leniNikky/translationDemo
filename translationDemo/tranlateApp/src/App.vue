<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单/易用/便捷</h5>
    <TranslateForm v-on:formsubmit="translateform"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'App',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data:function(){
    return{
      translatedText:""
    }
  },
  methods:{
    translateform:function(text,language){
      this.$http.get("https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20181009T010721Z.ec1896c2344291e4.e85b052fd20793b803dcdb0fecaf78421e4881b1&lang="+language+"&text="+text)
          .then((response)=>{
            //alert(response.body.text[0])
            this.translatedText = response.body.text[0]
          })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
