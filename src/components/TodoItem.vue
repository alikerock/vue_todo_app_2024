<script setup>
import { ref } from 'vue';

const props = defineProps({
  todo: {
    type: Object,
    required: true,
  },
})
const emit = defineEmits(['toggle-checkbox'])

const isChecked  = ref(props.todo.checked);

const toggleCheckbox = (e)=>{

  emit('toggle-checkbox',{
    id:props.todo.id,
    checked:e.target.checked
  })
}

</script>

<template>
  <div>

    <BFormCheckbox
      id="checkbox-1"
      v-model="isChecked"
      name="checkbox-1"
      value="accepted"
      unchecked-value="not_accepted"
      @change="toggleCheckbox"      
    >
      <span :class="{ 'muted': todo.checked }">{{todo.title}}</span>
    </BFormCheckbox>

  </div>
</template>

<style scoped>
  .muted{
    text-decoration: line-through;
  }
</style>
