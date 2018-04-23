<template>
  <div id="TranslateForm">
    <form v-on:submit="formSubmit">
      <input type="text" placeholder="请输入翻译的内容" v-model="text">
      <select v-model="lang">
        <option value="en">English</option>
        <option value="ja">Chinese</option>  
        <option value="ko">Korean</option>
        <option value="ru">Russian</option>
        <option value="ja">Japanese</option>
      </select>
      <button type="submit" value="翻译">翻译</button>
    </form>
  </div>
</template>

<script>

export default{
  data(){
    return {
      text:'',
      lang:'en'
    }
  },
  methods:{
    formSubmit(e){
      this.$emit('formData',this.text,this.lang);
      e.preventDefault();
      
      // console.log(this.text);
      // console.log(this.lang);
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
