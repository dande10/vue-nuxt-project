<template>
  <div class="container">
    <dragable-component />
  </div>
</template>
<script lang="ts">
import Vue from 'vue'
import DragableComponent from '../components/DragableComponent.vue';
export default Vue.extend({
  components: {
    DragableComponent
  }
})
</script>       
<style>
html, body {
  margin: 0;
  padding: 0;
}
* {
  box-sizing: border-box;
}
.container {
  position: relative;
  display: block;
  background: rgba(0,0,0,0.3);
  height: 100%;
  min-height: 100vh;
  max-height: 100%;
  width: 100%;
  overflow-y: auto;
}
</style>
