<script setup>
const variants = {
  default: 'border border-gray-200 hover:bg-gray-100 text-gray-900',
  danger: 'bg-red-200 hover:bg-red-100 text-red-900',
}
defineProps({
  variant: {
    type: String,
    default: 'default', // Ensure default style applies when no variant is provided
  },
})
defineEmits(['click'])
</script>

<template>
  <button
    :class="[
      'text-sm font-medium rounded-full px-3 py-1',
      variants[variant] ?? variants.default, // Fall back to default if invalid variant
    ]"
    @click="$emit('click')"
  >
    <slot></slot>
  </button>
</template>
