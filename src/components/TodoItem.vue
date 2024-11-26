<script setup>
defineProps({
  todo: {
    type: String,
    required: true,
  },
})
</script>

<template>
  <div>

    <BFormCheckbox
      id="checkbox-1"
      v-model="status"
      name="checkbox-1"
      value="accepted"
      unchecked-value="not_accepted"
    >
      {{todo}}
    </BFormCheckbox>
    
  </div>
</template>

<style scoped>
</style>
