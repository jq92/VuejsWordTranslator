<template>
  <h1 class="text-success">{{translatedText}}</h1>
</template>

<script>
export default {
  name: 'translateOutput',
  props: ['translatedText']
};
</script>

<style>
h1 {
  font-size: 4rem;
}
</style>
