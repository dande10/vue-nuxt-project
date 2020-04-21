<template>
  <div class="container">
    <!-- <div class="input-wrapper" ondragover="return false">
      <label for="columnNumbers">Columns: </label><input name="column-number" id="columnNumbers" v-model="columns" type="number" min="1" />
    </div> -->
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

        <grid-item class="vue-grid-item-container" v-for="item in layout"
                   :x="item.x"
                   :y="item.y"
                   :w="item.w"
                   :h="item.h"
                   :i="item.i"
                   :key="item.i">
                   {{item.i}}
            <!-- <input placeholder="enter text here"/> -->
        </grid-item>
    </grid-layout>
    
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'
import draggable from 'vuedraggable'
  import VueGridLayout from 'vue-grid-layout';
@Component({
  components: { draggable, 
   GridLayout: VueGridLayout.GridLayout,
           GridItem: VueGridLayout.GridItem},
  name: 'dragable-component'
})
export default class DragableComponent extends Vue {
  public layout: object[] = [
    {"x":0,"y":0,"w":2,"h":2,"i":"0"},
	    {"x":2,"y":0,"w":2,"h":4,"i":"1"},
	    {"x":4,"y":0,"w":2,"h":5,"i":"2"}
  ]
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
.dropable-element{
   width: 200px;
   height: 200px;
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
.input-wrapper {
  width: 100%;
  display: block;
  display: flex;
  align-self: center;
  justify-content: center;
}
label {
  color: #333;
  font-size: 16px;
  padding: 15px;

}
input {
  min-height: 36px;
  background: #fff;
  line-height: 1;
  font-size: 16px;
  border: 1px solid #e3e3e3;
  border-radius: 4px;
  margin-bottom: 15px;
  text-align: center;
}
.grid-wrapper {
  display: flex;
  margin: auto;
  background: #ccc;
  grid-gap: 10px 15px;
  margin-top: 30px;
  clear: both;
}

.grid {
  width: auto;
  background: #fff;
  padding: 20px;
  text-align: center;
  display: block;
  margin: 20px;
}
</style>
