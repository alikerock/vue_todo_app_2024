<script setup>
import { ref, watch } from 'vue';
const props = defineProps({
  todo: {
    type: Object,// `todo`는 객체형 데이터여야 함
    required: true,
  },
})
const emit = defineEmits(['toggle-checkbox'])

// 내부 상태 관리용 ref 생성
const isChecked = ref(props.todo.checked);

// prop 변경 시 내부 상태도 업데이트
watch(
  () => props.todo.checked,
  (newVal) => {
    isChecked.value = newVal;
  }
);



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
      :id="`checkbox-${todo.id}`"
      v-model="isChecked"
      @change="toggleCheckbox"      
    >
      <!-- 
      <span :class="isChecked && 'muted'">{{todo.title}}</span> 
      -->
      <!-- Vue에서 권장하는 동적 클래스 바인딩 방식으로 변경 -->
      <span :class="{ muted: isChecked }">{{ todo.title }}</span>
    </BFormCheckbox>

  </div>
</template>

<style scoped>
  .muted{
    text-decoration: line-through;
  }
</style>
