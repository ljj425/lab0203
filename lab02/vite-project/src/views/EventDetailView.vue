<script setup lang="ts">
import { ref, onMounted } from 'vue'
import type {Event} from '@/types/Event'
import EventService from '@/services/EventService'
const event = ref<Event>()
  const id = ref<number>(5928101)
onMounted(() => {
  EventService.getEvent(id.value)
.then((response) => {
event.value = response.data
})
.catch((error) => {
 console.error('There was an error!', error)
 })
})
</script>
<template>
 <div v-if=”event”>
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
  export default {
   getEvents() {
     return apiClient.get('/events')
  },
  getEvent(id: number) {
    return apiClient.get('/events/' + id)
   }
 }
</template>