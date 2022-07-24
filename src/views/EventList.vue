<template lang="pug">
.events
	h1 Events for Good
	EventCard(v-for="(event, index) in events" :key="event.id" :event="event")
</template>

<script>
// @ is an alias to /src
import EventService from '@/services/EventService.js';
import EventCard from '@/components/EventCard.vue';

export default {
	name: 'EventList',
	components: {
		EventCard
	},
	data() {
		return {
			endpoint: 'https://my-json-server.typicode.com/joshuaward/real-world-vue/events',
			events: null
		}
	},
	created() {
		EventService.getEvents()
			.then(response => {
				this.events = response.data;
				console.log(this.events)
			})
			.catch(error => {
				console.error(error)
			})
	}
}
</script>

<style scoped lang="scss">
.events {
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
}
</style>
