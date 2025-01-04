<script setup>
import SectionCard from '@/components/SectionCard.vue'
import RoundedButton from '@/components/RoundedButton.vue'

defineProps({
  retry: {
    type: Function,
    required: false,
  },
})
</script>

<template>
  <SectionCard>
    <div class="space-y-4 items-center flex flex-col">
      <div class="text-red-500">
        <slot></slot>
      </div>
      <div>
        <RoundedButton v-if="retry" @click="retry">Retry now</RoundedButton>
      </div>
    </div>
  </SectionCard>
</template>
