<template>
  <div  id="translateForm">
    <form id="transform" v-on:submit="formSubmit">
      <input type="text" v-model="textToTranslate" placeholder="需要翻译的内容">
      <select  v-model="language">
        <option value="en">英语</option>
        <option value="ru">俄语</option>
        <option value="ko">朝鲜语</option>
        <option value="ja">日语</option>
        <option value="es">西班牙语</option>
        <option value="it">意大利语</option>
        <option value="de">德语</option>
        <option value="zh">中文</option>
      </select>
      <input class="btn btn-primary"  type="submit" value="翻译">
    </form>   
  </div>
</template>

<script>


export default {
  name: 'translateForm',
  data:function(){
    return{
      textToTranslate:"",
      language:""
    }

  },
   methods:{
     formSubmit:function(e){
   // alert(this.textToTranslate);
    this.$emit("formSubmit",this.textToTranslate,this.language);
     e.preventDefault();

  } 
   }
}
</script>

<style>
</style>
