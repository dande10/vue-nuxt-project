<template>
  <div class="container">  
    <grid-layout
            :layout.sync="layout"
            :col-num="12"
            :row-height="30"
            :is-draggable="true"
            :is-resizable="true"
            :is-mirrored="false"
            :vertical-compact="true"
            :margin="[10, 10]"
            :use-css-transforms="true"
    >

        <grid-item class="vue-grid-item-container" 
             v-for="item in layout"
                   :x="item.x"
                   :y="item.y"
                   :w="item.w"
                   :h="item.h"
                   :i="item.i"
                   :key="item.i">
                  <span contenteditable="true"></span>
           
        </grid-item>
    </grid-layout>
    
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'
  import VueGridLayout from 'vue-grid-layout';
@Component({
  components: {  
   GridLayout: VueGridLayout.GridLayout,
   GridItem: VueGridLayout.GridItem
   },
  name: 'dragable-component'
})
export default class DragableComponent extends Vue {
  public layout: object[] = [
    {"x":0,"y":0,"w":2,"h":2,"i":"0"},
	    {"x":2,"y":0,"w":2,"h":4,"i":"1"},
	    {"x":4,"y":0,"w":2,"h":5,"i":"2"}
  ]
  public drag(event: any) {
   event.dataTransfer.setData('text/plain', event.target.id);
  }
  public drop(event: any) {
    const id = event.dataTransfer.getData('text');

    const draggableElement = document.getElementById(id);
    const dropzone = event.target;
    dropzone.appendChild(draggableElement);

    event.dataTransfer.clearData();
  }
}
</script>
<style scoped>
.resizable {
  border: 2px solid;
  padding: 20px;
  width: 300px;
  resize: both;
  overflow: auto;
  grid-column-gap: 20px;
}

.vue-grid-item-container{
  background: #fff;
}

.container {
  width: 100%;
  margin: auto;
  display: block;
  padding: 25px;
  height: 100%;
  height: calc(100% - 50px);
  min-height: auto;
}
</style>
