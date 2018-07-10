<template>
  <div id="app">
   <h1>在线翻译</h1>
   <h5 class="text-muted">简单 / 易用 / 便捷</h5>
    <translateForm v-on:formSubmit="translateText">
   </translateForm>
   <translateOutput v-text="translatedText"></translateOutput>
   

    
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'
export default {
  name: 'App',
  data:function(){
       return{translatedText:""}
  },

  components: {
      TranslateForm,TranslateOutput
  },
  methods:{
    translateText:function(text,language){
      //alert(text);
      this.$http.get(
  'https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180611T041751Z.761a657e2b451443.1c8c07e511b6d3bf8a5744cf21be71903bb64489&lang='+language+'&text='+text)
  .then((response) => {
   // console.log(response.body.text[0]);
   this.translatedText = response.body.text[0];
  })
    }
  }
}
</script>

<style>
#app{
  text-align: center;
}
</style>
