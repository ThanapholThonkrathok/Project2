<script setup>
import { ref } from 'vue'

const date = ref(new Date())
</script>

<template>
  <VCard>
    <VCardText class="d-flex justify-space-between h-100">
      <VDatePicker
        v-model="date"
        mode="dateTime"
      />
    </VCardText>
  </VCard>
</template>
