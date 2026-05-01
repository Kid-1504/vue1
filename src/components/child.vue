<template>
  <div class="child">
    <p>{{ message }}</p>
    <p v-if="!message" class="empty">Нет сообщения</p>
  </div>
</template>

<script setup>
defineProps({
  message: {
    type: String,
    default: 'Сообщение по умолчанию'
  }
})
</script>

<style scoped>
.child {
  padding: 12px;
  margin: 8px 0;
  background-color: #f0f0f0;
  border-radius: 8px;
  border-left: 4px solid #42b883;
}
p {
  margin: 0;
  font-size: 16px;
}
.empty {
  color: #999;
  font-style: italic;
}
</style>