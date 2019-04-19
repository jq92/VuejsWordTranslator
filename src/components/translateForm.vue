<template>
  <div class="col-md-6 offset-3" id="translateForm">
    <div>
      <form class v-on:submit="formSubmit">
        <input
          class="form-control"
          type="text"
          v-model="textToTranslate"
          placeholder="Enter a Word..."
        >
        <select class="form-control" v-model="language">
          <option value="ru">Russian</option>
          <option value="ko">Korean</option>
          <option value="fr">French</option>
          <option value="ja">Japanese</option>
          <option value="de">German</option>
          <option value="ja">Japanese</option>
        </select>
        <br>
        <input class="form-control btn btn-primary" type="submit" value="Translate">
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data() {
    return {
      textToTranslate: '',
      language: ''
    };
  },
  created() {
    this.language = 'ru';
  },
  methods: {
    formSubmit(arg) {
      if (this.textToTranslate == '') {
        alert('Please enter a word');
      } else this.$emit('formSubmit', this.textToTranslate, this.language);
      // Preventing from actually submit to a webpage
      arg.preventDefault();
    }
  }
};
</script>

<style>
#translateForm {
  /* margin-left: 700px; */
  margin-top: 20px;
  margin-bottom: 20px;
}
</style>
