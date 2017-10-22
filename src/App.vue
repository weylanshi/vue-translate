<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单 /  易用 / 便捷</h5>
    <TranslateForm v-on:formSubmit="translateText"/>
    <TanslateOutput v-text="translatedText"/>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TanslateOutput from './components/TranslateOutput'

export default {
  name: 'app',
  data:function(){
    return{
      translatedText:""
    }
  },
  components: {
    TranslateForm,TanslateOutput
  },
  methods:{
    translateText:function(text,language){
      // alert(text)
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170721T082515Z.54cf3dc583f679db.f4a96182281281d8b5dfe24b4e88298e2133f219&lang='+language+'&text='+text)
      .then((response)=>{
        this.translatedText= response.body.text[0]
       // console.log(response.body.text)
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
