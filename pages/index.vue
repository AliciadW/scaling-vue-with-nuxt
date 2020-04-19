<template>
  <div>
    <h1>Events</h1>
  </div>
</template>

<script>

  export default {
    name: "index",
    head() {
      return {
        title: 'Event Listings'
      }
    },
    asyncData({ $axios }) {
      return $axios.get('http://localhost:3001/events').then(response => {
        return {
          events: response.data
        }
      })
    }
  }
</script>

<style scoped></style>
