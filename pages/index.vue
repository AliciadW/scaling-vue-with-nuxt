<template>
  <div>
    <h1>Events</h1>

    <EventCard
      v-for="(event, index) in events"
      :key="index"
      :event="event"
      :data-index="index"
    />
  </div>
</template>

<script>
  import EventCard from "~/components/EventCard";

  export default {
    name: "index",
    components: {
      EventCard
    },
    head() {
      return {
        title: 'Event Listings'
      }
    },
    async asyncData({ $axios, error }) {
      try {
        const { data } = await $axios.get('http://localhost:3001/events');
        return {
          events: data
        }
      } catch(e) {
        error({
          statusCode: 503,
          message: 'Unable to fetch events at this time. Please try again later.'
        })
      }
    }
  }
</script>

<style scoped></style>
