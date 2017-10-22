<template>
  <div class="row" id="TranslateForm">
      <div class="col-md-6 col-md-offset-3">
        <form class="well form-inline" v-on:submit="formSubmit">
          <input class="form-control" v-model="textTotranslate" type="text" placeholder="请输入要翻译的内容">
          <select class="form-control" v-model="language">
              <option value="en" selected  >English</option>
              <option value="ko">Korean</option>
          </select>
          <input class="btn btn-primary" type="submit" value="翻译">
      </form>
      </div>
     
  </div>
</template>

<script>
export default {
  name: "TranslateForm",
  data: function() {
    return {
      textTotranslate: "",
      language: ""
    };
  },
  methods: {
    formSubmit: function(e) {
      //   alert(this.textTotranslate)
      this.$emit("formSubmit", this.textTotranslate, this.language);
      e.preventDefault();
    }
  }
};
</script>

<style>

</style>
