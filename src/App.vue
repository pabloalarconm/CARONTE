<template>
<div>
  <img alt="Vue logo" src="./assets/logo.png">
  <Form msg="CARONTE: Catcher of Ontological Terms"/>
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
