<template>
  <div>
    <h2>Vue3 Draggable Example</h2>

    <draggable
      v-model="items"
      @start="onDragStart"
      @update="onDragUpdate"
      @end="onDragEnd"
    >
      <template v-slot:item="{ element }">
        <div class="draggable-item">
          {{ element.text }}
        </div>
      </template>
    </draggable>

  </div>
</template>
<script setup>
import { ref,watchEffect  } from 'vue';
import draggable from 'vuedraggable';

const items = ref([
  { id: 1, text: 'Item 1' },
  { id: 2, text: 'Item 2' },
  { id: 3, text: 'Item 3' },
  { id: 4, text: 'Item 4' },
  { id: 5, text: 'Item 5' },
]);

const onDragStart = (event) => {
  // เริ่มลากร
  console.log('Drag start:', event);
};

const onDragUpdate = (event) => {
  // อัปเดตตำแหน่งในระหว่างการลากร
  console.log('Drag update:', event);
};

const onDragEnd = (event) => {
  // ลากรสิ้นสุด
  console.log(items.value);
};

watchEffect(() => {
  console.log('Items have changed:', items.value);
});
</script>



<style>
.draggable-item {
  border: 1px solid #ccc;
  padding: 10px;
  margin: 5px;
  background-color: #f0f0f0;
  cursor: grab;
  user-select: none;
}
</style>
