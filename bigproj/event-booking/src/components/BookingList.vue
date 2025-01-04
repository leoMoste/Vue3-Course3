<script setup>
import { onMounted } from 'vue'
import BookingItem from '@/components/BookingItem.vue'
import LoadingBookingItem from '@/components/LoadingBookingsItem.vue'
import ErrorCard from '@/components/ErrorCard.vue'
import useBookings from '@/composables/useBookings'

const { bookings, loading, fetchBookings, cancelBooking, error } = useBookings()

onMounted(() => {
  fetchBookings()
})
</script>

<template>
  <template v-if="error">
    <ErrorCard :retry="fetchBookings"> Failed to fetch bookings. </ErrorCard>
  </template>
  <template v-else>
    <section class="grid grid-cols-1 gap-4">
      <template v-if="!loading">
        <BookingItem
          v-for="booking in bookings"
          :key="booking.id"
          :title="booking.eventTitle"
          :status="booking.status"
          @cancelled="cancelBooking(booking.id)"
        />
      </template>
      <template v-else>
        <LoadingBookingItem v-for="i in 4" :key="i" />
      </template>
    </section>
  </template>
</template>
