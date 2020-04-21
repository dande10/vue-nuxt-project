<template>
  <div class="container">
    <div class="input-wrapper" ondragover="return false">
      <label for="columnNumbers">Columns: </label><input name="column-number" id="columnNumbers" v-model.number="totalColumns" type="number" min="1" />
    </div>

    <!-- <div class="grid-wrapper" :style="gridWrapperStyles">
      <div class="grid dropable-element" :draggable="!dragged||dragged&&dragged==n" v-for="n in totalColumns" :data-num="n" :id="'element-'+n" :key="n" @drop="dragEnd($event, n)">{{n}}</div>
    </div> -->
    <div class="grid-wrapper">
      <div class="grid dropable-element resizable" v-for="n in totalColumns"
      :data-num="n" 
      :id="'element-'+n" 
      :key="n"
       type=text
      ></div>
    </div>
    
    <!-- <div class="text-wrapper" v-for="index in count" :key="index">
      <button class="button-delete" @click="deleteComponent">X</button>
      <textarea    draggable="true"  class="resizable" placeholder="Enter text here..."></textarea>
    </div> -->
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'dragable-component',
  components: {},
  data() {
    return  {
      totalColumns : 1,
      wrapperWidth: 900,
      dragged: '',
      currentDragging:''
      
    }
  },
  computed: {
    // gridWrapperStyles() {
    //   const value = this.wrapperWidth / this.totalColumns;

    //   let cssString = '';

    //   for( let i = 0; i < this.totalColumns; i++ ) {
    //     cssString += value+'px ';
    //   }
      
    //   return {
    //     // gridTemplateColumns: `repeat(${this.totalColumns}, 1fr)`
    //     gridTemplateColumns: cssString
    //   };
    // }
  },
  methods: {
    addComponent(): void {
      this.totalColumns += 1;
    },
    deleteComponent(): void {
      this.totalColumns -= 1;
    },
    dragEnd(event: DragEvent, n: number) {
      console.log(event, n);
      this.dragged = '';
    },
    drag(event: DragEvent, n:number){
    
     event.dataTransfer.dropEffect = 'move'
      event.dataTransfer.effectAllowed = 'move'
     event.dataTransfer.setData('text/plain', JSON.stringify(n))
    },
    isDragging(n: number) {
      this.currentDragging = n;
    },
    drop(event: DragEvent, target) {
       if(event == null){
         this.dragEnd();
         return;
       }
       const data = event.dataTransfer.getData('text/plain');
       const original = JSON.stringify(data);
       console.log(original, 'originalValue')
       if(target.key === original || target.key == null){
         this.dragEnd();
         return ;
       }
       target = {...target};
       const originalPosition = target.position;
       target.position = originalPosition;
    }
  }
  // mounted() {
  //   const vm = this;

  //   document.addEventListener("dragstart", function( event ) {
      
  //     // store a ref. on the dragged elem
  //     // make it half transparent
  //     const target = event.target as HTMLElement;
  //     vm.dragged = target.getAttribute('data-num');
  //     console.log('dragstart: ', vm.dragged)
  //     target.style.opacity = "0.5";
  //   }, false);

  //   document.addEventListener("dragend", function( event ) {
  //     // reset the transparency
  //     vm.dragged = '';
  //   }, false);


  //   document.addEventListener("drop", function( event ) {
  //     // prevent default action (open as link for some elements)
  //     event.preventDefault();
  //     console.log("drop", event)
  //     const target = event.target as HTMLElement;
  //     // move this. elem to the selected drop target
  //     if ( target.className === "dropable-element" ) {
  //       const num = target.getAttribute('data-num');
  //       console.log(num);
  //         // target.style.background = "";
  //         // dragged.parentNode.removeChild( dragged );
  //         // target.appendChild( dragged );
  //     }
    
  // }, false);
  // }
});
</script>
<style scoped>
[draggable=true] {
  cursor: move;
}
.resizable {
  border: 2px solid;
  padding: 20px;
  width: 300px;
  resize: both;
  overflow: auto;
  grid-column-gap: 20px;
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
