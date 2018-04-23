<template>
  <div id="app">
    <h1 class="title">在线翻译</h1>
    <p class="text-muted">这是一个基于vue的子父组件传值练习</p>
    <TranslateForm v-on:formData="getForm"></TranslateForm>
    <TranslateOutput v-bind:translated="translatedText"></TranslateOutput>
  </div>
</template>

<script>

import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'App',
  data(){
    return{
      translatedText:''
    } 
  },
  methods:{
    getForm(text,lang){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180423T060012Z.2cd1b8a9e33a7023.48acf584d7e388e05ac2bd21258f946c64e5d822&lang='+lang+'&text='+text).then((response)=>{
        // console.log(response.body.text[0]);
        this.translatedText=response.body.text[0];
      });
    }
  },
  components: {
    TranslateForm,
    TranslateOutput
  }
}
</script>

<style>
#app {
  width: 100%;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
