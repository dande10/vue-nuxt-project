<template>
  <div class="container">
     <dragable-component />
  </div>
</template>
<script lang="ts">
import Vue from 'vue'
import DragableComponent from '@/components/DragableComponent.vue';
export default Vue.extend({
  components: {
    DragableComponent
  }
})
</script>       
<style>
.container {
  position: relative;
  display: grid;
  height: 100%;
  grid-gap: 1.5rem;
  grid-template-columns: repeat(12, 1fr);
  min-height: 100vh;
  max-height: 100%;
  overflow-y: auto;
  grid-auto-rows: 50px 50px 68px auto;
}
</style>
