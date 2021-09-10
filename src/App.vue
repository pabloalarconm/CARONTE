<template>
<div>
  <img alt="Vue logo" src="./assets/logo.png">
  <Form msg="Bioportal API Controller"/>
</div>
</template>

<script>
import Form from './components/Form.vue';

export default {
  name: 'App',
  components: {
    Form
  },
}
</script>

<style>
  @import './assets/css/style.css';
</style>
