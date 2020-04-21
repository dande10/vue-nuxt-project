<template>
  <div class="container">
    <!-- <div class="input-wrapper" ondragover="return false">
      <label for="columnNumbers">Columns: </label><input name="column-number" id="columnNumbers" v-model="columns" type="number" min="1" />
    </div> -->
    
    <draggable class="grid-wrapper" v-model="columns" group="people" @start="drag=true" @end="drag=false">
        <div class="grid dropable-element resizable" v-for="(column, index) in columns"
        :key="index"
        >
        <textarea placeholder="enter text here..."></textarea>
        </div>
   </draggable>
    
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'
import draggable from 'vuedraggable'
@Component({
  components: { draggable },
  name: 'dragable-component'
})
export default class DragableComponent extends Vue {
  public columns: object[] = [
    {
      id: 1,
      text: ''
    },
    {
      id: 2,
      text: ''
    },
    {
      id: 3,
      text: ''
    }
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
