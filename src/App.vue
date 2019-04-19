<template>
  <div id="app" class="text-center">
    <br>
    <h1>Word Translator</h1>
    <h5 class="text-success">Power By Vue.js</h5>
    <hr>
    <translate-form v-on:formSubmit="translateText"></translate-form>
    <translate-output v-text="translatedText"></translate-output>
  </div>
</template>

<script>
import translateForm from './components/translateForm.vue';
import translateOutput from './components/translateOutput.vue';

export default {
  name: 'App',
  components: {
    'translate-form': translateForm,
    'translate-output': translateOutput
  },
  data() {
    return {
      translatedText: ''
    };
  },
  methods: {
    translateText(text, language) {
      const axios = require('axios');
      axios
        .get(
          'https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190415T054339Z.339c96c79bed0370.be0750a49b6090ab33135e27ed05778d0252647b&lang=' +
            language +
            '&text=' +
            text
        )
        .then(response => {
          // handle success
          this.translatedText = response.data.text[0];
        });
    }
  }
};
</script>

<style>
@import url('bootstrap.min.css');

body {
  background: #fcfcfc;
}
</style>
