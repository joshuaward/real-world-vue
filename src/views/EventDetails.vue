<template lang="pug">
.event-details(v-if="event")
	img(:src="event.image")
	h1.event-title {{ event.title }}
	p {{ event.time }} on {{ event.date }} @ {{ event.location }}
	p {{ event.description}}
</template>
<script>
import EventService from '@/services/EventService'

export default {
  name: 'EventDetails',
	props: ['id'],
  data() {
		return {
			event: null
		}
	},
	created() {
		EventService.getEvent(this.id)
			.then(response => {
				this.event = response.data;
				console.log(this.event)
			})
			.catch(error => {
				console.error(error)
			})
	}
}
</script>

<style scoped lang="scss">
.event-details {}
</style>
