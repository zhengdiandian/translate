<template>
  <div id="translateForm" class="row">
      <div class="col-md-6 col-md-offset-3">
        <form id="transForm" class="well form-inline" v-on:submit="formSubmit">
          <input class="form-control" type="text" name="" id="" placeholder="输入需要翻译的内容" v-model="textToTranslate">
          <select class="form-control" name="" id="" v-model="language"  aria-valuetext="">
              <option  value="en">English</option>
              <option value="ru" >俄语</option>
              <option value="ja">日语</option>
              <option value="ko">韩语</option>
          </select>
          <input class="btn btn-primary" type="submit" value="翻译"></input>
        </form>
        </div>
  </div>
</template>

<script>
// import Hello from './components/Hello'

export default {
  name: 'translateForm',
  data:function(){
      return {
        textToTranslate:"",
        language:""
      }
  },
  methods: {
      formSubmit:function(e){
        //   alert(this.textToTranslate)
        this.$emit("formSubmit",this.textToTranslate,this.language)
          e.preventDefault();
          
      },
      created:function(){
          this.language = "en";
      }
  }
}
</script>

<style>
    #transForm{
        border: 1px solid #CCC;
        border-radius: 10px;
    }
</style>
