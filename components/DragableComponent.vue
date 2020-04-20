<template>
 <div>
   <div class="button-wrapper">
     <button class="button-class" @click ="addComponent">Add</button>
   </div>
  
  <div class="text-wrapper" v-for="index in count" :key="index">
    <button class="button-delete" @click="deleteComponent">X</button>
    <textarea    draggable="true"  class="resizable" placeholder="Enter text here..."></textarea>
  </div>
 </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'dragable-component',
  components: {
  },
  data() {
    return  {
       count : 1  
    }
  },
  methods: {
    addComponent(): void {
      this.count += 1;
    },
    deleteComponent(): void {
      this.count -= 1;
    }
  }
  
});
</script>
<style>
[draggable=true] {
  cursor: move;
}

.resizable {
  resize: both;
  border: 1px solid black;
}
.button-delete{
  position: absolute;
  margin: 10px;
}
</style>
