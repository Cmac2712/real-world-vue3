<template>
  <h1>Events For Good</h1>
  <div class="events">
    <event-card v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
import EventCard from "@/components/EventCard.vue";
import EventService from "@/services/EventService.js";

export default {
  name: "EventList",
  components: {
    EventCard
  },
  created() {
    EventService.getEvents()
      .then(response => {
        this.events = response.data;
      })
      .catch(error => {
        console.error(error);
      });
  },
  data() {
    return {
      events: null
    };
  }
};
</script>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
