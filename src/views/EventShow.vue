<template>
    <div>
        <h1>Showing event {{ id }}</h1>
        <EventCard :event="event"/>
    </div>

</template>

<script>
  import EventService from '@/services/EventService.js'
  import EventCard from '@/components/EventCard'
export default {
  props: ['id'],
  components: {
    EventCard
  },
  data() {
    return {
      event: {}
    }
  },
  created() {
    EventService.getEvent(this.id)
      .then((response) => {
        this.event = response.data
      }).catch((error) => {
        console.log('There  was an error: ' + error)
      })
  }
};
</script>
