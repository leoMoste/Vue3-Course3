<script setup>
import SectionCard from '@/components/SectionCard.vue'
import RoundButton from '@/components/RoundedButton.vue'
import { Loader, Check } from 'lucide-vue-next'
import { computed } from 'vue'

const props = defineProps({
  title: String,
  status: String,
})

const pending = computed(() => props.status === 'pending')
const icon = computed(() => (pending.value ? Loader : Check))
defineEmits(['cancelled'])
</script>

<template>
  <SectionCard>
    <div class="flex justify-between">
      <div class="flex space-x-2">
        <div>{{ title }}</div>
        <div>
          <component
            :is="icon"
            :class="{ 'animate-spin': pending }"
          ></component>
        </div>
      </div>
      <RoundButton variant="danger" @click="$emit('cancelled')">
        Cancel
      </RoundButton>
    </div>
  </SectionCard>
</template>
