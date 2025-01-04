<script setup>
import RoundedButton from '@/components/RoundedButton.vue'
import SectionCard from '@/components/SectionCard.vue'
defineProps({
  title: String,
  when: String,
  description: String,
})

//to comunicate with the parent
defineEmits(['register'])
</script>

<template>
  <SectionCard>
    <template #header>
      {{ title }}
    </template>
    {{ when }}
    <template #footer>
      <div class="space-y-4">
        <p>{{ description }}</p>
        <div class="flex justify-end">
          <RoundedButton @click="$emit('register')"> Register </RoundedButton>
        </div>
      </div>
    </template>
  </SectionCard>
</template>
