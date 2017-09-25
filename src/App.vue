<template>
  <div id="app">
    <h1>快捷翻译</h1>
    <h5 class="text-muted">简单 / 易用 / 便捷</h5>
    <translateForm v-on:formSubmit="translateText"></translateForm>
    <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'
export default {
  name: 'app',
  data () {
    return {
      translatedText:""
    }
  },
  components: {
    TranslateForm,
    TranslateOutput
  },
  methods:{
    translateText:function(text,language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170925T070133Z.00ab94384ab1aea2.fed61328412c26a30cdee0253a38d07feef574d9&lang='+language+'&text='+text)
      .then((Response)=>{
        console.log(Response.body.text[0]);
        this.translatedText=Response.body.text[0]
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
