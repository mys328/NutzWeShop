<template>
  <div id="top">
    <div :style="display:showLogo">
      <img :src="logo">
    </div>
  </div>
</template>
<script>
  export default {
    data(){
      return {
        showLogo:'none',
        logo:''
      }
    },
    ready:function(){
      this.getLogo()
    },
    methods:{
      getLogo:function(){
        this.$http.get("/api/public/wx/cms/logo").then((res) => {
          const d=JSON.parse(res.data);
          this.$set('showLogo', 'block');
          this.$set('logo','/api'+d.data);
        })
      .catch(function(response) {
          console.log(response)
        })
      }
    }
  }
</script>
<style>
  #top{
    position: relative;
    height: 6rem;
    color: #fff;
    font-size: .293333rem;
  }
  #top img{
    margin: 0;
    padding: 0;
    border: 0;
    position:absolute;
    width: 100%;
    height: 180px;
  }
</style>
