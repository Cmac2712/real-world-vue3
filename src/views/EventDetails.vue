<template>
  <div v-if="event">
    <h4>{{ event.title }}</h4>
    <span>@ {{ event.time }} on {{ event.date }}</span>
    <p>{{ event.description }}</p>
  </div>
</template>

<script>
import EventService from "@/services/EventService.js";
export default {
  props: ["id"],
  data() {
    return {
      event: null
    };
  },
  created() {
    EventService.getEvent(this.id)
      .then(response => {
        this.event = response.data;
      })
      .catch(error => {
        console.error(error);
      });
  }
};
</script>
