<template>
  <div id="app">
    <OptionSelector />
    <router-view/>
  </div>
</template>

<script>
import OptionSelector from './components/OptionSelector.vue';

export default {
  name: 'App',
  components: {
    OptionSelector
  }
};
</script>

<style>
/* 你可以在这里添加样式 */
</style>
